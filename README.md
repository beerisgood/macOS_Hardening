![Work in progress label](https://img.shields.io/badge/-Work%20in%20Progress-yellowgreen) ![GitHub last commit](https://img.shields.io/github/last-commit/beerisgood/macOS_Hardening?label=last%20update%3A)

take also a look at: https://github.com/drduh/macOS-Security-and-Privacy-Guide and https://github.com/sunknudsen/privacy-guides

# Requirements
- device with Apple [M1 chip](https://en.wikipedia.org/wiki/Apple_M1) because of secure ARM architecture, but at least a device with [T2 chip](https://support.apple.com/guide/security/secf020d1074/1/web/1)

# macOS_Hardening
- [x] set your Mac to check for software updates [automatically](https://support.apple.com/guide/mac-help/get-macos-updates-mchlpx1065/mac)
- [x] use apps [included](https://support.apple.com/guide/mac-help/built-in-apps-mchl110b00b7/mac) on your Mac instead of Third-Party ones
- [x] install new applications only from [App Store](https://support.apple.com/guide/app-store/get-apps-and-safari-extensions-fir9b2ea074e/mac)
- [x] [automatically](https://support.apple.com/guide/app-store/update-apps-fir9b01adda3/mac) keep apps up to date
- [x] don't turn off internal [XProtect](https://support.apple.com/guide/security/protecting-against-malware-sec469d47bd8/web) or [Gatekeeper](https://support.apple.com/HT202491) for protection against malware
- [x] enable [Application Firewall](https://support.apple.com/en-us/HT201642)
- [x] turn on [FileVault](https://support.apple.com/en-us/HT204837)
- [x] [password protect](https://support.apple.com/guide/mac-help/require-a-password-after-waking-your-mac-mchlp2270/11.0/mac/11.0) your [screen saver](https://support.apple.com/guide/mac-help/use-a-screen-saver-mchl4b68853d/mac)
- [x] disable [remote access](https://support.apple.com/guide/remote-desktop/enable-remote-management-apd8b1c65bd/mac)
- [x] setup backup with [Time Machine](https://support.apple.com/en-us/HT201250)
- [x] [disable](https://support.apple.com/en-us/HT201476) automatic login during startup
- [x] [Set up](https://support.apple.com/guide/mac-help/set-up-other-users-on-your-mac-mtusr001/mac) users, guests, and groups on Mac

## Further Hardening / reading material
- [ ] How to protect Mac computers from cold boot attacks [Youtube](https://www.youtube.com/watch?v=d_M18sq0TIQ)
- [ ] How to spoof MAC address and hostname automatically at boot on macOS [Youtube](https://www.youtube.com/watch?v=ASXANpr_zX8)
- [ ] Why Macs equipped with T2 chip are bad for hackers [Youtube](https://www.youtube.com/watch?v=brGLX_92F5o)
- [ ] macOS has [Hardened Runtime](https://developer.apple.com/documentation/security/hardened_runtime) for user space code
- [ ] M1 Macs have [Kernel Integrity Protection](https://manuals.info.apple.com/MANUALS/1000/MA1902/en_US/apple-platform-security-guide.pdf#page=50) (KIP) for kernel code
- [ ] M1 Macs use an [improved implementation of ARM's Pointer Authentication Codes](https://developer.apple.com/documentation/security/preparing_your_app_to_work_with_pointer_authentication) (PAC), ensuring backward and forward-edge protection
- [ ] macOS requires that all applications are [sandboxed](https://developer.apple.com/documentation/security/app_sandbox)
