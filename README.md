# VTR-PON VST3 Audio Processing Add-on

Version **0.3.0** supports **VTR-PON 3.0.0-beta.1** on Windows 11 x64. Both VTR-PON and the add-on must use x64 binaries. This add-on is distributed separately for the initial VTR-PON3 beta release.

Runs Windows x64 VST3 audio effects that support stereo processing in a separate process.

## Installation, updates, and removal

1. Download `vtr-pon-vst3-addon-0.3.0-windows-x64.vtrponaddon` from the [official VTR-PON3 add-on page](https://pondashi.com/vtr-pon/addon/) and verify it against the published SHA-256 checksum.
2. Prepare the software listed below. You do not need the SDK to use the add-on.
3. In VTR-PON, open **Settings → Add-ons → Install from package…** and select the file. Read the README, license terms, and notices before accepting the terms. You can cancel if you do not agree.
4. Follow VTR-PON's prompts to close and restart the application, then check the add-on's status.

To update, select the new version's package in the same settings page, review its documents, and accept its terms.

To remove the add-on, open **Settings → Add-ons** and follow the prompts to restart VTR-PON. Removing an add-on does not remove external runtimes, drivers, or plug-ins. Follow each vendor's instructions to update or remove those components.

## Required software and usage

The package includes Qt 6.8.3 Release shared libraries and plug-ins, along with Microsoft Visual C++ redistributable DLLs. No separate VST runtime installation is required. Install Windows x64 VST3 effects that support stereo processing and obtain any licenses they require.

Select a plug-in in VTR-PON's VST3 settings and click **Apply** to use its audio processing and editor. Selecting a candidate alone does not switch the active plug-in. The current plug-in remains active if applying the candidate fails; select **None** and click **Apply** to remove it. VTR-PON also provides controls for bypassing processing and recovering from errors. Follow each plug-in vendor's instructions for activation, required content, and configuration.

## Compatibility and limitations

Compatibility with every VST3 plug-in is not guaranteed. Instrument plug-ins and arbitrary channel layouts are outside the supported scope. Operation depends on the plug-in's processing load, latency, user interface, and license activation.

This add-on targets VTR-PON 3.0.0-beta.1. For other VTR-PON versions, check the compatibility information in the relevant release.

## License, source code, and support

The add-on's original code is licensed under the MIT License, with copyright held by Tetsu Suzuki. The project imposes no additional restrictions on commercial or non-commercial productions. External software and third-party code remain subject to their respective terms.

- [MIT License](https://github.com/pondashicom/vtr-pon-vst3-addon/blob/v0.3.0/LICENSE/MIT.txt) · [Distribution terms and third-party notices](https://github.com/pondashicom/vtr-pon-vst3-addon/blob/v0.3.0/LICENSE/DISTRIBUTION.md)
- [Source code for this version](https://github.com/pondashicom/vtr-pon-vst3-addon/tree/v0.3.0) · [Build instructions](https://github.com/pondashicom/vtr-pon-vst3-addon/blob/v0.3.0/BUILDING.md) · [Release](https://github.com/pondashicom/vtr-pon-vst3-addon/releases/tag/v0.3.0)
- [VTR-PON source code](https://github.com/pondashicom/vtr-pon/tree/main/3) · [VTR-PON website](https://pondashi.com/vtr-pon/)
- Report bugs through [Issues](https://github.com/pondashicom/vtr-pon-vst3-addon/issues). Include the add-on and VTR-PON versions, Windows version, relevant runtimes, hardware and plug-ins, and steps to reproduce the issue. For private inquiries, contact [info@pondashi.com](mailto:info@pondashi.com).

This add-on is not an official or certified product of any hardware, SDK, or plug-in vendor. All product names and trademarks belong to their respective owners.

VST is a trademark of Steinberg Media Technologies GmbH. Qt is a trademark of The Qt Company Ltd.
