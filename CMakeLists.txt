cmake_minimum_required(VERSION 3.25)
project(vtr_pon_vst3_addon VERSION 0.3.0 LANGUAGES CXX)
set(CMAKE_CXX_STANDARD 20)
set(CMAKE_CXX_STANDARD_REQUIRED ON)

if(NOT WIN32 OR NOT CMAKE_SIZEOF_VOID_P EQUAL 8)
  message(FATAL_ERROR "This add-on supports Windows x64 only.")
endif()
find_package(Qt6 6.8 REQUIRED COMPONENTS Widgets)
qt_standard_project_setup(REQUIRES 6.8)
set(VTRPON_VST3_SDK_DIR "" CACHE PATH "VST 3 SDK 3.8.0 or newer")
if(NOT EXISTS "${VTRPON_VST3_SDK_DIR}/CMakeLists.txt")
  message(FATAL_ERROR "Set VTRPON_VST3_SDK_DIR to the external VST 3 SDK.")
endif()
file(READ "${VTRPON_VST3_SDK_DIR}/CMakeLists.txt" _sdk_cmake)
string(REGEX MATCH "project\\([ \t\r\n]*vstsdk[ \t\r\n]+VERSION[ \t\r\n]+([0-9]+\\.[0-9]+\\.[0-9]+)"
  _version_match "${_sdk_cmake}")
if(NOT CMAKE_MATCH_1 OR CMAKE_MATCH_1 VERSION_LESS "3.8.0")
  message(FATAL_ERROR "VST 3 SDK 3.8.0 or newer is required.")
endif()
set(SMTG_ENABLE_VST3_PLUGIN_EXAMPLES OFF CACHE BOOL "" FORCE)
set(SMTG_ENABLE_VST3_HOSTING_EXAMPLES OFF CACHE BOOL "" FORCE)
set(SMTG_ENABLE_VSTGUI_SUPPORT OFF CACHE BOOL "" FORCE)
add_subdirectory("${VTRPON_VST3_SDK_DIR}" "${CMAKE_CURRENT_BINARY_DIR}/sdk" EXCLUDE_FROM_ALL)
qt_add_executable(vtr-pon-vst3-addon
  src/vst3_addon_main.cpp
  "${VTRPON_VST3_SDK_DIR}/public.sdk/source/vst/hosting/plugprovider.cpp"
  "${VTRPON_VST3_SDK_DIR}/public.sdk/source/vst/hosting/module_win32.cpp"
  "${VTRPON_VST3_SDK_DIR}/public.sdk/source/common/memorystream.cpp")
target_include_directories(vtr-pon-vst3-addon PRIVATE include "${VTRPON_VST3_SDK_DIR}")
target_link_libraries(vtr-pon-vst3-addon PRIVATE Qt6::Widgets sdk_hosting ole32 user32)
target_compile_definitions(vtr-pon-vst3-addon PRIVATE NOMINMAX WIN32_LEAN_AND_MEAN)
if(MSVC)
  target_compile_options(vtr-pon-vst3-addon PRIVATE /utf-8)
endif()
set_target_properties(vtr-pon-vst3-addon PROPERTIES
  RUNTIME_OUTPUT_DIRECTORY "${CMAKE_BINARY_DIR}/audio-addons")
add_custom_command(TARGET vtr-pon-vst3-addon POST_BUILD
  COMMAND "${CMAKE_COMMAND}" -E copy_if_different
    "${VTRPON_VST3_SDK_DIR}/LICENSE.txt"
    "$<TARGET_FILE_DIR:vtr-pon-vst3-addon>/VST3-SDK-LICENSE.txt"
  COMMAND "$<TARGET_FILE:Qt6::windeployqt>" --release --no-translations
    --skip-plugin-types generic,imageformats,networkinformation,tls
    --no-compiler-runtime
    "$<TARGET_FILE:vtr-pon-vst3-addon>"
  VERBATIM)
install(DIRECTORY "${CMAKE_BINARY_DIR}/audio-addons/" DESTINATION audio-addons)
