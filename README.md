![MacOS stable](https://badgen.net/badge/icon/MacOS%20Monterey%2012.3?icon=apple&label) ![Work in progress label](https://img.shields.io/badge/-Work%20in%20Progress-yellowgreen) ![GitHub last commit](https://img.shields.io/github/last-commit/beerisgood/macOS_Hardening?label=last%20update%3A)

# Device Recommendations
- Mac with Apple [M1 chip](https://en.wikipedia.org/wiki/Apple_M1) because of secure ARM architecture. M1, M1 Pro, M1 Max, M1 Ultra are all the same. Just core and performance changes.
 
- (Devices with [T2 chip](https://support.apple.com/guide/security/secf020d1074/1/web/1) are no longer recommend, because the A11 chip is vulnerable to checkm8, lacks some hardware security features A12 and above have and is vulnerable against Passware Kit Forensic T2 Add-on.)


# First steps

- Clean [NVRAM (nonvolatile random-access memory)/ PRAM (Parameter RAM)](https://support.apple.com/en-us/HT204063) and [SMC (system management controller)](https://support.apple.com/en-us/HT201295) after purchase
- [Clean install OS](https://support.apple.com/en-us/HT204904) after purchase
- Distrust all networks by disallowing all incoming connections in [Firewall settings](https://support.apple.com/en-us/HT201642) (stealth mode).
- Set your hostname to generic `MacBook` in Sharing settings.
- Check for updates and enable [automatic updates]((https://support.apple.com/guide/mac-help/get-macos-updates-mchlpx1065/mac)).
- Create an [unprivileged user for day to day use](https://help.apple.com/machelp/mac/10.12/index.html#/mh11389).
- [Enable FileVault](https://support.apple.com/en-us/HT204837) _after_ installation for increased entropy and also to [protect](https://support.apple.com/en-us/HT204455) your firmware

# General Tips
- Install software only from the App Store as there is [a mandatory sandbox for all App Store apps](https://developer.apple.com/documentation/security/app_sandbox).
- Check if all forms of [remote access](https://support.apple.com/guide/remote-desktop/enable-remote-management-apd8b1c65bd/mac) are disabled in Sharing settings.
- It may be better to install Google Chrome, Microsoft Edge, or Hexavalent as WebKit is not well-known for security - while only Safari supports [PrivateRelay](https://support.apple.com/en-us/HT212614)
- [Password protect](https://support.apple.com/guide/mac-help/require-a-password-after-waking-your-mac-mchlp2270/11.0/mac/11.0) your [screen saver](https://support.apple.com/guide/mac-help/use-a-screen-saver-mchl4b68853d/mac) and use a low time for locking and logout.
- Backup with [Time Machine](https://support.apple.com/en-us/HT201250) and make sure you have encryption turned on.
- While DNS encryption [isn't perfect](https://madaidans-insecurities.github.io/encrypted-dns.html) both [Quad9](https://www.quad9.net) and [AdGuard](https://adguard-dns.io) are recommend. Quad9 provide a [easy solution](https://www.quad9.net/news/blog/ios-mobile-provisioning-profiles) with Apple signed profiles. [NextDNS](https://nextdns.io/?from=qvnr8eu8) is another service, but it struggles with stability/performance and support issues.
- Avoid [Kernel extensions](https://support.apple.com/guide/deployment-reference-macos/kernel-extensions-in-macos-apd37565d329/web) (Catalina and earlier) and [System extensions](https://support.apple.com/en-us/HT210999) (Big Sur and later). Both add unnecessary attack surface.
- Consider using a [more stricter umask](https://support.apple.com/en-us/HT201684) such as 027 or 077 for both system processes and user apps.

## Reading/Informational Material
- macOS has [Hardened Runtime](https://developer.apple.com/documentation/security/hardened_runtime) for user space code. This is not required for App Store apps and not all apps enable this.
- M1 Macs have [Kernel Integrity Protection](https://manuals.info.apple.com/MANUALS/1000/MA1902/en_US/apple-platform-security-guide.pdf#page=50) (KIP) for kernel code
- M1 Macs use an [improved implementation of ARM's Pointer Authentication Codes](https://developer.apple.com/documentation/security/preparing_your_app_to_work_with_pointer_authentication) (PAC), ensuring backward and forward-edge protection
- Apple requires that all applications are [sandboxed](https://developer.apple.com/documentation/security/app_sandbox) _only from the App Store_.
- c3 event: [Escape the macOS sandbox and TCC](https://media.ccc.de/v/rc3-10175-escape_the_macos_sandbox_and_tcc)
- macOS IR (Incident Response) & Forensics [resources](https://gist.github.com/0xmachos/6e8b813cffc2035914606bd4cda491d2)
- CIS (Center for Internet Security, Inc) [Security Benchmarks](https://www.cisecurity.org/benchmark/apple_os/)
- NIST Security Technical Implementation [Guide](https://ncp.nist.gov/checklist/976)
- [About](https://support.apple.com/en-us/HT208394) speculative execution vulnerabilities in ARM-based and Intel CPUs
- About [System Integrity Protection](https://support.apple.com/en-us/HT204899) (SIP) on your Mac
