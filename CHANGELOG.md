# Change Log
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](http://keepachangelog.com/).

## [Unreleased]

## [1.3.1] - 2017-01-01

This is mainly a test of doing bugfix releases.

### Fixed
- Error message in setup when the device _other_ is selected.

## [1.3] - 2016-12-21
- **IMPORTANT**: This is a major rewrite that requires you to delete the whole old version and set up the new one from scratch. See the [Migration quick-guide](https://github.com/alexa-pi/AlexaPi/wiki/Migration) for help.
- A lot of refactoring and changes for better future development.

### Added
- [Documentation] for users and developers. Also, there are [guidelines / tips for contributors](https://github.com/alexa-pi/AlexaPi/blob/master/CONTRIBUTING.md).
- Native systemd support (added a service unit file). This brings better security and is easier and convenient.
- Can run under an unprivileged user for better security.
- Newly supported platforms (apart from Raspberry Pi):
    - Orange Pi and other A20 / H3 based boards
    - C.H.I.P.
    - _desktop_ platform, which is an interactive platform. Alexa can be triggered here with keyboard input.
    - _dummy_ platform that doesn't do anything (like touching GPIO hardware) and is daemon-friendly.
    - Magic Mirror
    - See the [Devices] section in the [Documentation] for further details.
- Now configurable (in the configuration file):
    - Custom command and duration for the _long_press_ feature (e.g. shutting down the Pi after 10s button press)
    - Platform trigger voice confirmation (you can set whether you want to hear Alexa's _yes_ after you press a button)
    - Audio output device
    - Default volume
- Different audio output devices for speech and media can be specified.
- Support for Arch Linux.

### Changed
- Improved directory structure.
- Paths improvements for better _platform-independency_ and UX. 
    - Use system temporary directory for recordings/answers, which is usually in RAM to avoid using system storage.
    - Default install path is now _/opt/AlexaPi_.
- Uses pocketsphinx only from PyPI (not the extra `git pull` anymore), which saves about 200 MB on bandwidth and 250 MB in storage space.
- More detailed documentation regarding Amazon device registration.
- All configuration in a single YAML file, which among other things enables users to update the python files without worrying.
- Better UX when running setup with existing config.
- Runs via systemd by default. Other options can be selected in setup.
- Runs under an unprivileged user _alexapi_ by default. Can be changed in init scripts / unit files.
- There is no default command for the _long_press_ feature.
- Abstracted device platform code into **_device_platforms_** which means we can now support other devices within the same codebase and users can now write their own independent device platform files.
- Abstracted playback library into **_playback_handlers_** which means we can now support multiple libraries within the same codebase and users can now write their own independent handlers and can route their sound through whatever they want to.


### Removed
- Temporarily disabled voice confirmation of the _long_press_ feature.

### Fixed
- Fixed not playing files with colons in their name. This resulted in not playing certain Alexa responses like when requesting _Flash Briefing_.
- Fixed overlapping audio playbacks / not playing some files. Partially caused by previous fix.
- Fixed incorrect handling of AVS responses that contained a _further-input-request_. This fixes skills like Jeopardy for example.

## [1.2] - 2016-08-30
@maso27 made significant changes that lead to this version.

### Added
- Voice Recognition via CMU Sphinx. When the word _"alexa"_ is detected, Alexa responds with _"Yes"_ and the subsequent audio to be processed.
- Option for the user to install shairport-sync for airplay support.
- A ten-second button press will trigger a system halt.
- Option to monitor Alexa continuously and re-start if it has died.
- Command line arguments:
 `(-s / --silent)` = start without saying "Hello"
 `(-d / --debug)` = enable display of debug messages at command prompt
- Volume control via "set volume xx" where xx is between 1 and 10

### Changed
- Tunein support is improved.

## 1.1 - 2016-05-01
@sammachin created the project in January 2016 and made significant changes that lead to this version.


[Unreleased]: https://github.com/alexa-pi/AlexaPi/compare/v1.3.1...HEAD
[1.3.1]: https://github.com/alexa-pi/AlexaPi/compare/v1.3...v1.3.1
[1.3]: https://github.com/alexa-pi/AlexaPi/compare/v1.2...v1.3
[1.2]: https://github.com/alexa-pi/AlexaPi/compare/v1.1...v1.2
[Devices]: https://github.com/alexa-pi/AlexaPi/wiki/Devices
[Documentation]: https://github.com/alexa-pi/AlexaPi/wiki/