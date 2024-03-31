![macOS stable](https://badgen.net/badge/icon/MacOS%20Sonoma%2014.4.1?icon=apple&label) ![GitHub last commit](https://img.shields.io/github/last-commit/beerisgood/macOS_Hardening?label=last%20update%3A)

# Device Recommendations
- Mac with Apple Silicon Chip ([M1](https://en.wikipedia.org/wiki/Apple_M1) or newer) because of secure [ARM architecture](https://en.wikipedia.org/wiki/ARM_architecture_family). Newer chips have better security features, so it's best to stick with the most recent ones.
<br/>older devices (with T2 or T1 chips) are no longer recommended because they are vulnerable to [checkm8](https://en.wikipedia.org/wiki/Apple_T2#Security_vulnerabilities), Passware Kit Forensic T2 Add-on and lack [some hardware security features](https://support.apple.com/guide/security/sec87716a080/1/web/1).


# First steps
- Distrust all networks by disallowing all incoming connections in [Firewall settings](https://support.apple.com/guide/mac-help/mh34041/mac) (stealth mode).
- Check for updates and enable [automatic updates](https://support.apple.com/guide/mac-help/get-macos-updates-mchlpx1065/mac) for OS and also App Store.
- If multiple people use your Mac, [limit](https://support.apple.com/guide/mac-help/flvlt003/mac) the number of users with administrator privileges and set up a user account for each person, so that one person can’t modify the files needed by another
- [Enable](https://support.apple.com/guide/mac-help/mh11785/mac) FileVault

# General Tips
- make sure you have [Full Firmware Security](https://support.apple.com/guide/mac-help/change-security-settings-startup-disk-a-mac-mchl768f7291/mac) and [System Integrity Protection](https://developer.apple.com/library/archive/documentation/Security/Conceptual/System_Integrity_Protection_Guide/ConfiguringSystemIntegrityProtection/ConfiguringSystemIntegrityProtection.html) enabled
- enable [Two-factor authentication](https://support.apple.com/102660) for your Apple ID and use FIDO [security keys](https://support.apple.com/HT213154) for it
- enable [Advanced Data Protection](https://support.apple.com/HT202303) for iCloud
- beside FileVault, (encrypted) [disk images](https://support.apple.com/guide/disk-utility/dskutl11888/mac) can be created for sensitive files (search for "Create secure image file" at bottom)
- Install software only from the App Store as there is [a mandatory sandbox for all App Store apps](https://developer.apple.com/documentation/security/app_sandbox). If not possible, at least [Electron based](https://www.electronjs.org/apps) programs [should](https://wojciechregula.blog/post/abusing-electron-apps-to-bypass-macos-security-controls/) [_be_](https://medium.com/@metnew/why-electron-apps-cant-store-your-secrets-confidentially-inspect-option-a49950d6d51f) [avoided](https://blog.xpnsec.com/macos-injection-via-third-party-frameworks/) - even in [2024](https://wojciechregula.blog/post/electroniz3r/).
- Check if all forms of [remote access](https://support.apple.com/guide/remote-desktop/enable-remote-management-apd8b1c65bd/mac) are disabled in Sharing settings.
- [use](https://support.apple.com/guide/safari/ibrwa008/mac) only [Safari](https://www.apple.com/safari/) as your browser, because it supports [PrivateRelay](https://support.apple.com/HT212614), [PassKeys](https://support.apple.com/HT213305), [many](https://webkit.org/blog/category/privacy/) privacy features like [Tracking & Fingerprint Prevention](https://webkit.org/tracking-prevention/), Link Tracking Protection, [Privacy Report](https://support.apple.com/guide/safari/ibrw35004465/mac), [locked](https://support.apple.com/guide/safari/ibrw1069/mac) isolated and [ephemeral](https://developer.apple.com/documentation/foundation/urlsessionconfiguration/1410529-ephemeral) Private Browsing tabs and [more](https://support.apple.com/guide/safari/welcome/mac). Also enable [Cross-site tracking prevention](https://support.apple.com/guide/safari/sfri40732/) and [Advanced Tracking and Fingerprinting Protection](https://support.apple.com/guide/safari/ibrw1075/)
- [Password protect](https://support.apple.com/guide/mac-help/require-a-password-after-waking-your-mac-mchlp2270/11.0/mac/11.0) your [screen saver](https://support.apple.com/guide/mac-help/use-a-screen-saver-mchl4b68853d/mac) and use a low time for locking and logout.
- Backup with [Time Machine](https://support.apple.com/HT201250) and make sure you have encryption turned on.
- Instead of using insecure, privacy-unfriendly adblocker browser extensions or programs, use the [Reader](https://support.apple.com/guide/safari/sfri32632/16.0/mac) mode in Safari.
- If possible, use iCloud [Private Relay](https://support.apple.com/102602). Alternatives are: [Quad9](https://www.quad9.net) and [Cloudflare](https://developers.cloudflare.com/1.1.1.1/setup/ios/). Quad9 provide an [easy solution](https://www.quad9.net/news/blog/ios-mobile-provisioning-profiles) with Apple signed profiles. [AdGuard](https://adguard-dns.io) and [NextDNS](https://nextdns.io/) are also options, but some users report problems like false positive filtering and stability/performance issues. Only Private Relay supports [ODoH](https://www.apple.com/privacy/docs/iCloud_Private_Relay_Overview_Dec2021.PDF)!
- Avoid [Kernel extensions](https://support.apple.com/guide/deployment/depa5fb8376f/1/web/1.0) (Catalina and earlier), [System extensions](https://support.apple.com/HT210999) (Big Sur and later) and [Rosetta](https://support.apple.com/guide/security/secebb113be1/web). These add unnecessary attack surface.
- open Terminal and enable "Secure keyboard entry” at macOS menu bar to prevent other applications reading the keyboard input while using the terminal
- [encrypt](https://support.apple.com/guide/mac-help/mh40593/) external media
- (Macbooks only) [control](https://support.apple.com/guide/deployment/depf8a4cb051/web) accessory security
- with Activity Monitor you can find Apps lacking the Sandbox and/ or Code injection Protection. Just [enable](https://developer.apple.com/documentation/security/app_sandbox/protecting_user_data_with_app_sandbox#4098972) the "Sandbox" and "Restricted" column. With the [Terminal](https://github.com/beerisgood/macOS_Hardening/blob/main/Hardened%20Runtime%20Check) you can also check the [Hardened Runtime](https://developer.apple.com/documentation/security/hardened_runtime).
- Thunderbolt 4 cables enforces DMA protection [using](https://www.intel.com/content/www/us/en/content-details/753497/security-brief-thunderbolt-4.html) Directed I/O (Intel VT-d) technology that provides IO virtualization (often referred to as IO Memory Management Unit or IOMMU).

## Advanced users/special use case
- enable [Lockdown Mode](https://support.apple.com/105120)
- Consider using a [stricter umask](https://support.apple.com/HT201684) such as 027 or 077 for both system processes and user apps.

## Reading/Informational Material
- [Security-announce](https://lists.apple.com/mailman/listinfo/security-announce) - Product security notifications and announcements from Apple
- Apple Platform Security [PDF](https://help.apple.com/pdf/security/en_US/apple-platform-security-guide.pdf)
- Apple Security Research [Blog & Security Bounty](https://security.apple.com)
- Apple Safety [certifications](https://support.apple.com/guide/certifications/apc353b1b736/web)
- macOS has [Hardened Runtime](https://developer.apple.com/documentation/security/hardened_runtime) for user space code. This is not required for App Store apps and not all apps enable this.
- M1 Macs have [Kernel Integrity Protection](https://manuals.info.apple.com/MANUALS/1000/MA1902/en_US/apple-platform-security-guide.pdf#page=50) (KIP) for kernel code
- M1 Macs use an [improved implementation of ARM's Pointer Authentication Codes](https://developer.apple.com/documentation/security/preparing_your_app_to_work_with_pointer_authentication) (PAC), ensuring backward and forward-edge protection
- Apple requires that all applications are [sandboxed](https://developer.apple.com/documentation/security/app_sandbox) _only from the App Store_.
- some [resources](https://github.com/houjingyi233/macOS-iOS-system-security) about macOS/iOS system security
- CIS (Center for Internet Security, Inc) [Security Benchmarks](https://www.cisecurity.org/benchmark/apple_os/)
- NIST Security Technical Implementation [Guide](https://ncp.nist.gov/checklist/1069)
- [About](https://support.apple.com/HT208394) speculative execution vulnerabilities in ARM-based and Intel CPUs
- About [System Integrity Protection](https://support.apple.com/HT204899) (SIP) on your Mac
- About [Gatekeeper](https://support.apple.com/HT202491) (forerunner was [Quarantine](https://0xmachos.com/2019-02-01-Quarantine-Intro/)) - Safely open apps on your Mac
- Learn how Private Relay [protects](https://www.apple.com/privacy/docs/iCloud_Private_Relay_Overview_Dec2021.PDF) users’ privacy on the internet
- [Getting started](https://theevilbit.github.io/posts/getting_started_in_macos_security/) in macOS security / [forensics](https://gist.github.com/0xmachos/6e8b813cffc2035914606bd4cda491d2)
- Protecting [against malware](https://support.apple.com/guide/security/sec469d47bd8/web) in macOS
- (since macOS 13) [AMFI Launch Constraints](https://theevilbit.github.io/posts/launch_constraints_deep_dive/) - [First Quick Look](https://theevilbit.github.io/posts/amfi_launch_constraints/) and [Trust Cache](https://support.apple.com/guide/security/trust-caches-sec7d38fbf97/web)
- [Evolution](https://github.com/beerisgood/macOS_Hardening/blob/main/Evolution%20of%20privacy%20%26%20security.md) of privacy & security in macOS
- [Data Vault](https://support.apple.com/guide/security/secc01781f46/1/web/1) - Protecting app access to user data
- Why your macOS EDR solution [shouldn’t be](https://www.sentinelone.com/blog/why-your-macos-edr-solution-shouldnt-be-running-under-rosetta-2/) running under Rosetta 2
- PPL ([Page Protection Layer](https://support.apple.com/guide/security/sec8b776536b/1/web/1#sec314c3af61)) or: why iOS/ iPadOS is much more secure than macOS
- "what is": [Effaceable Storage](https://support.apple.com/guide/security/aside/sec0183122de/1/web/1), [sepOS](https://support.apple.com/guide/security/aside/secc3e4f7a43/1/web/1), [BIMI](https://support.apple.com/HT213155) support in Apple Mail, signed system volume ([SSV](https://support.apple.com/guide/mac-help/mchl0f9af76f/mac))
- The Complete Guide to Understanding Apple Mac Security [for Enterprise](https://assets.sentinelone.com/macos-security/enterprise-mac-security) aka Apple at [Work](https://www.apple.com/business/enterprise/security/)
- A Guide to macOS Threat Hunting and Incident [Response](https://assets.sentinelone.com/c/sentinal-one-mac-os-?x=fvgtlj)
- macOS Security & Privilege [Escalation](https://book.hacktricks.xyz/macos-hardening/macos-security-and-privilege-escalation)
- [Let's talk](https://theevilbit.github.io/posts/macos_authorization/) macOS Authorization
- [How](https://eclecticlight.co/2023/04/03/how-apfs-mounts-encrypted-volumes-snapshots-cryptexes-and-more/) APFS mounts encrypted volumes, snapshots, cryptexes and more
- (macOS Sonoma+) [implementations](https://developer.apple.com/documentation/macos-release-notes/macos-14-release-notes#File-System) of exfat and msdos file systems provided by services running in user-space instead of by kernel extensions
- (Safari 17.x) [GPU Process](https://webkit.org/blog/14445/webkit-features-in-safari-17-0/) security, [Privacy changes](https://cunderwood.dev/2023/06/09/privacy-changes-coming-to-safari-17/), [blob partitioning](https://webkit.org/blog/14787/webkit-features-in-safari-17-2/#privacy)
- (macOS 14.0+) [Link Tracking Protection](https://www.apple.com/newsroom/2023/06/apple-announces-powerful-new-privacy-and-security-features/) in Messages, Mail, and Safari
- Managed Device Attestation - a [technical exploration](https://jedda.me/managed-device-attestation-a-technical-exploration/)
- [Built-in](https://www.huntress.com/blog/built-in-macos-security-tools) macOS Security (TCC, File Quarantine, Gatekeeper, XProtect, MRT, XPR)
- JNUC 2023: Securing Apple Devices in [organization](https://www.youtube.com/watch?v=yxovR80sV7Y) with MDM
- Apple's [theft prevention system](https://support.apple.com/102541)
