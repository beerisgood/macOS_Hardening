![MacOS stable](https://badgen.net/badge/icon/MacOS%20Big%20Sur%2011.5?icon=apple&label) ![Work in progress label](https://img.shields.io/badge/-Work%20in%20Progress-yellowgreen) ![GitHub last commit](https://img.shields.io/github/last-commit/beerisgood/macOS_Hardening?label=last%20update%3A)

# Device Recommendations
- Mac with Apple [M1 chip](https://en.wikipedia.org/wiki/Apple_M1) because of secure ARM architecture, but at least a device with [T2 chip](https://support.apple.com/guide/security/secf020d1074/1/web/1) and Touch Bar. T2 chip physical security may be questionable as it uses the A11 chip which is vulnerable to checkm8 and lacks some hardware security features A12 and above have.
- M1, M1 Pro, and M1 Max are all the same. Just core and performance changes.

# Do First

- Clean [NVRAM (nonvolatile random-access memory)/ PRAM (Parameter RAM)](https://support.apple.com/en-us/HT204063) and [SMC (system management controller)](https://support.apple.com/en-us/HT201295) after purchase
- [Clean install OS](https://support.apple.com/en-us/HT204904) after purchase
- T2 Macs, enable firmware password and disable firmware password reset using `firmwarepasswd -disable-reset-capability`. M1 Macs use admin accounts for administrative recovery tasks.
- Macs with Intel chips, [***disable hyperthreading/SMT***](https://support.apple.com/en-us/HT210108).
- Enable FileVault _after_ installation for increased entropy
- Distrust all networks by disallowing all incoming connections in [Firewall settings](https://support.apple.com/en-us/HT201642) (stealth mode).
- Set your hostname to generic `MacBook` in Sharing settings.
- Disable all forms of [remote access](https://support.apple.com/guide/remote-desktop/enable-remote-management-apd8b1c65bd/mac) in Sharing settings.
- Check for updates and enable [automatic updates]((https://support.apple.com/guide/mac-help/get-macos-updates-mchlpx1065/mac)).
- Create an [unprivileged user for day to day use](https://help.apple.com/machelp/mac/10.12/index.html#/mh11389).

# General Tips
- Install software only from the App Store as there is [a mandatory sandbox for all App Store apps](https://developer.apple.com/documentation/security/app_sandbox).
- It may be better to install Google Chrome, Microsoft Edge, or Hexavalent as WebKit is not well-known for security.
- [Password protect](https://support.apple.com/guide/mac-help/require-a-password-after-waking-your-mac-mchlp2270/11.0/mac/11.0) your [screen saver](https://support.apple.com/guide/mac-help/use-a-screen-saver-mchl4b68853d/mac) and use a low time for locking and logout.
- Backup with [Time Machine](https://support.apple.com/en-us/HT201250) and make sure you have encryption turned on.
- [NextDNS](https://nextdns.io/?from=qvnr8eu8) provide a [easy solution](https://apple.nextdns.io/) for encrypting DNS (even if DNS encryption [isn't perfect](https://madaidans-insecurities.github.io/encrypted-dns.html)), but also protects against malware, ads, trackers and more - with [top marks](https://www.youtube.com/watch?v=wSAWCMTwPiU&t=1094s)
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
