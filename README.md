# 🍏 macOS Hardening Guide
![macOS stable](https://badgen.net/badge/icon/MacOS%20Sequoia%2015.4.1?icon=apple&label) ![GitHub last commit](https://img.shields.io/github/last-commit/beerisgood/macOS_Hardening?label=last%20update%3A) ![Status](https://img.shields.io/badge/status-active-brightgreen)

Secure your macOS system with this comprehensive hardening guide.  
Ideal for users who value **privacy**, **security**, and **performance**.

---

<details>
<summary>📚 <strong>Table of Contents (click to expand)</strong></summary>

- 🖥️ [Device Recommendations](#%EF%B8%8F-device-recommendations)
- 🛠️ [Preparation](#%EF%B8%8F-preparation)
- ⚙️ [System Settings](#%EF%B8%8F-system-settings)
- 🧑‍🤝‍🧑 [Users & Groups](#-users--groups)
- 🌐 [Network and Firewall](#-network-and-firewall)
- 🛡️ [Secure Browsing](#%EF%B8%8F-secure-browsing)
- 🧰 [Software](#-software)
- 📋 [General Tips](#-general-tips)
- 💪 [Advanced users/special use case](#-advanced-usersspecial-use-case)
- 📚 [Resources](#-resources)

</details>
</br>

## 🖥️ Device Recommendations
- Mac with **Apple Silicon** Chip ([M1](https://en.wikipedia.org/wiki/Apple_M1) or newer) because of it's secure [ARM architecture](https://en.wikipedia.org/wiki/ARM_architecture_family).
- Newer **chips**, starting with M2 have better [security features](https://help.apple.com/pdf/security/en_US/apple-platform-security-guide.pdf) like [Secure Page Table Monitor (SPTM) & Trusted Execution Monitor (TXM)](https://support.apple.com/guide/security/sec8b776536b/1/web/1#secd022396fb).
- M4 adds the [Secure Exclave](https://discussions.apple.com/thread/255753688). So it's best to stick with the **most recent ones**.
- Older devices (with T2 or T1 chips) are **no longer recommended** because they are vulnerable to [checkm8](https://en.wikipedia.org/wiki/Apple_T2#Security_vulnerabilities), Passware Kit Forensic T2 Add-on, and lack [some hardware security features](https://support.apple.com/guide/security/sec87716a080/1/web/1).

</br>

## 🛠️ Preparation
- create/ use an iCloud.com email address for your **Apple-ID** at first start.
- Check for **updates** and enable [automatic updates](https://support.apple.com/guide/mac-help/get-macos-updates-mchlpx1065/mac) for all options.
- Keep a **record** of the settings you modify.

</br>

## ⚙️ System Settings
- [Enable](https://support.apple.com/guide/mac-help/mh11785/mac)  **FileVault** (Full Disk Encryption) and backup the recovery key. You can [check](https://discussions.apple.com/thread/254809188?answerId=260077837022&sortBy=rank#260077837022) for an recovery key and [verify](https://discussions.apple.com/thread/254289127?answerId=258038445022&sortBy=rank#258038445022) if your saved key is valid.
  - Beside FileVault, (encrypted) [disk images](https://support.apple.com/guide/disk-utility/dskutl11888/mac#dsku7bb3d28c) can be created for **sensitive files**
  - Also [encrypt](https://support.apple.com/guide/mac-help/mh40593/) external media.
- Set **Gatekeeper** to "App Store and identified developers".
- Require a **password immediately** after sleep or screen saver begins.
- Enable [Two-factor authentication](https://support.apple.com/102660) for your Apple-ID and use **FIDO** [security keys](https://support.apple.com/HT213154) for it.
- Enable [Advanced Data Protection](https://support.apple.com/HT202303#advanced) for **iCloud**.
- Backup with [Time Machine](https://support.apple.com/HT201250) and make sure you have **encryption** turned on.
- Open [Terminal](https://support.apple.com/guide/terminal/apd5265185d-f365-44cb-8b09-71a064a42125/mac) and enable **Secure keyboard entry** at macOS menu bar to prevent other applications reading the keyboard input while using the terminal.
- [Password protect](https://support.apple.com/guide/mac-help/require-a-password-after-waking-your-mac-mchlp2270/11.0/mac) your [screen saver](https://support.apple.com/guide/mac-help/use-a-screen-saver-mchl4b68853d/mac) and use a **low time** for locking and logout.
- (Macbooks only) [control](https://support.apple.com/guide/deployment/depf8a4cb051/web) **accessory** security.
- Make sure **you have** [Full Firmware Security](https://support.apple.com/guide/mac-help/change-security-settings-startup-disk-a-mac-mchl768f7291/mac) and [System Integrity Protection](https://developer.apple.com/library/archive/documentation/Security/Conceptual/System_Integrity_Protection_Guide/ConfiguringSystemIntegrityProtection/ConfiguringSystemIntegrityProtection.html) enabled.

### 🧑‍🤝‍🧑 Users & Groups
- Disable **automatic login**.
- Disable the **Guest user** account.
- - If multiple people use your Mac, [limit](https://support.apple.com/guide/mac-help/flvlt003/mac) the number of users with **administrator privileges** and set up a user account for each person, so that one person can’t modify the files needed by another.

</br>

## 🌐 Network and Firewall
- [Turn on](https://support.apple.com/guide/mac-help/mh34041/mac) the **Firewall**, enable blocking all incoming connections for all network and activate stealth mode in [firewall settings](https://support.apple.com/guide/mac-help/mh11783/15.0/mac/).
- Disable all forms of [remote access](https://support.apple.com/guide/remote-desktop/enable-remote-management-apd8b1c65bd/mac) **sharing settings**.
- Limit **Location Services** to essential apps only.
- (iCloud+ needed) [Enable](https://support.apple.com/102602) Private Relay.
  -  Alternatives are: [Quad9](https://www.quad9.net) and [Cloudflare](https://developers.cloudflare.com/1.1.1.1/setup/ios/). Quad9 provides an [easy solution](https://docs.quad9.net/Setup_Guides/MacOS/Big_Sur_and_later_%28Encrypted%29/) with Apple signed profiles. [AdGuard](https://adguard-dns.io) and [NextDNS](https://nextdns.io/) are also options, but some users report problems like false positive filtering and stability/performance issues.
  - *Only [Private Relay](https://www.apple.com/privacy/docs/iCloud_Private_Relay_Overview_Dec2021.PDF) supports [Oblivious DNS over HTTPS](https://en.wikipedia.org/wiki/DNS_over_HTTPS#Oblivious_DNS_over_HTTPS) (ODoH)*

</br>

## 🛡️ Secure Browsing

- **Safari** settings:
  - [Block](https://support.apple.com/guide/safari/sfri40732/mac) cross-site **tracking**.
  - [Clear](https://support.apple.com/guide/safari/sfri11471/mac) history and **website Data** to get a fresh start, now with tracking protection.
  - Instead of using insecure, privacy-unfriendly (adblocker) browser **extensions**, use the [Reader](https://support.apple.com/guide/safari/sfri32632/mac) mode.
  - [Hide](https://support.apple.com/guide/safari/sfri35610/mac) **IP address** from trackers / *and Websites (if PrivateRelay is activated)*
  - **Enable** [Advanced Tracking and Fingerprinting Protection](https://support.apple.com/guide/safari/ibrw1075/)

- Safari **hardening**:
  - [Enable](https://support.apple.com/guide/safari/ibrw1074/mac/) protection against fraudulent websites
  - [Enable](https://support.apple.com/guide/safari/ibrw1074/mac/)  protection against non-encrypted HTTP sites

</br>

## 🧰 Software
- Install only from the App Store as there is [a mandatory sandbox for all App Store apps](https://developer.apple.com/documentation/security/app_sandbox). 
- If not possible, at least [Electron-based](https://www.electronjs.org/apps) programs [should](https://wojciechregula.blog/post/abusing-electron-apps-to-bypass-macos-security-controls/) [_be_](https://medium.com/@metnew/why-electron-apps-cant-store-your-secrets-confidentially-inspect-option-a49950d6d51f) [avoided](https://blog.xpnsec.com/macos-injection-via-third-party-frameworks/) - even in [2024](https://wojciechregula.blog/post/electroniz3r/). 
- [Avoid](https://sector7.computest.nl/post/2024-04-bringing-process-injection-into-view-exploiting-all-macos-apps-using-nib-files/) using Homebrew and remove [unmaintained](https://blog.kandji.io/twitch-privileged-helper) programs.
- Avoid [Kernel extensions](https://support.apple.com/guide/deployment/depa5fb8376f/1/web/1.0) (Catalina and earlier), [System extensions](https://support.apple.com/HT210999) (Big Sur and later) and [Rosetta](https://support.apple.com/guide/security/secebb113be1/web).
- Also VM software like Parallels aren't perfect in [2024](https://khronokernel.com/macos/2024/05/30/CVE-2024-34331.html) nor [2025](https://jhftss.github.io/Parallels-0-day/).

</br>

## 📋 General Tips

-   Regularly audit installed **apps and permissions**.
-   Where [PassKeys](https://support.apple.com/HT213305) isn't supported, use strong, unique passwords and enable  **2FA** everywhere. This is easily **manageable** with internal [Passwords program](https://support.apple.com/guide/passwords/mchl901b1b95/mac).
-   Periodically review  **Privacy Settings**.
- With **Activity Monitor** you can find Apps lacking the Sandbox and/ or Code injection Protection.
  - Just [enable](https://developer.apple.com/documentation/security/app_sandbox/protecting_user_data_with_app_sandbox#4098972) the "Sandbox" and "Restricted" **columns**.
 - With the [Terminal](https://github.com/beerisgood/macOS_Hardening/blob/main/Hardened%20Runtime%20Check), you can also **check** the [Hardened Runtime](https://developer.apple.com/documentation/security/hardened_runtime).
- Thunderbolt 4 cables enforce **DMA protection** [using](https://www.intel.com/content/www/us/en/content-details/753497/security-brief-thunderbolt-4.html) Directed I/O (Intel VT-d) technology that provides IO virtualization (**often referred** to as IO Memory Management Unit or IOMMU).
- If Bluetooth accessories like a keyboard or mouse are used, **stay** with official Apple ones as their firmware will automatically be updated by macOS, and Apple's SoCs focus on **minimizing attack surface** by relegating security functions to dedicated hardware with limited functionality.

</br>

## 💪 Advanced users/special use case
- **Enable** [Lockdown Mode](https://support.apple.com/105120).
- Consider using a [stricter umask](https://support.apple.com/HT201684) such as **027 or 077** for both system processes and user apps.

</br>

## 📚 Resources

-   [Security-announce](https://lists.apple.com/mailman/listinfo/security-announce) - Product security notifications and announcements from Apple
- Apple Platform Security [Overview](https://support.apple.com/guide/security/) - [PDF](https://help.apple.com/pdf/security/en_US/apple-platform-security-guide.pdf)
- Apple Security Research [Blog & Security Bounty](https://security.apple.com)
- Apple Safety [certifications](https://support.apple.com/guide/certifications/apc353b1b736/web)
- Safari provides [many](https://webkit.org/blog/category/privacy/) privacy features like [Tracking & Fingerprint Prevention](https://webkit.org/tracking-prevention/), Link Tracking Protection, [Privacy Report](https://support.apple.com/guide/safari/ibrw35004465/mac), [locked](https://support.apple.com/guide/safari/ibrw1069/mac) isolated and [ephemeral](https://developer.apple.com/documentation/foundation/urlsessionconfiguration/1410529-ephemeral) Private Browsing tabs and [more](https://support.apple.com/guide/safari/welcome/mac) and is also the only browser which is secure [against](https://github.com/moonD4rk/HackBrowserData?tab=readme-ov-file#macos) data extraction & decryption
- macOS has [Hardened Runtime](https://developer.apple.com/documentation/security/hardened_runtime) for user space code. This is not required for App Store apps, and not all apps enable this.
- M1 Macs have [Kernel Integrity Protection](https://support.apple.com/guide/security/secb7ea06b49/web) (KIP) for kernel code
- M1 Macs use an [improved implementation of ARM's Pointer Authentication Codes](https://developer.apple.com/documentation/security/preparing_your_app_to_work_with_pointer_authentication) (PAC), ensuring backward and forward-edge protection
- Apple requires that all applications are [sandboxed](https://developer.apple.com/documentation/security/app_sandbox) _only from the App Store_.
- Some [resources](https://github.com/houjingyi233/macOS-iOS-system-security) about macOS/iOS system security
- CIS (Center for Internet Security, Inc.) [Security Benchmarks](https://www.cisecurity.org/benchmark/apple_os/)
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
- [Let's talk about](https://theevilbit.github.io/posts/macos_authorization/) macOS Authorization
- [How](https://eclecticlight.co/2023/04/03/how-apfs-mounts-encrypted-volumes-snapshots-cryptexes-and-more/) APFS mounts encrypted volumes, snapshots, cryptexes, and more
- (since macOS 14.0) [implementations](https://developer.apple.com/documentation/macos-release-notes/macos-14-release-notes#File-System) of exFAT and MS-DOS file systems provided by services running in user space instead of by kernel extensions, [Link Tracking Protection](https://www.apple.com/newsroom/2023/06/apple-announces-powerful-new-privacy-and-security-features/) in Messages, Mail, and Safari
- (since Safari 17.x) [GPU Process](https://webkit.org/blog/14445/webkit-features-in-safari-17-0/) security, [Privacy changes](https://cunderwood.dev/2023/06/09/privacy-changes-coming-to-safari-17/), [blob partitioning](https://webkit.org/blog/14787/webkit-features-in-safari-17-2/#privacy)
- Managed Device Attestation - a [technical exploration](https://jedda.me/managed-device-attestation-a-technical-exploration/)
- [Built-in](https://www.huntress.com/blog/built-in-macos-security-tools) macOS Security (TCC, File Quarantine, Gatekeeper, XProtect, MRT, XPR)
- JNUC 2023: Securing Apple Devices in an [organization](https://www.youtube.com/watch?v=yxovR80sV7Y) with MDM
- Apple's [theft prevention system](https://support.apple.com/102541)
- [Runtime protection](https://developer.apple.com/news/?id=saqachfa) in macOS Sequoia
- CVE-2023-42929: Why do we [need](https://jhftss.github.io/CVE-2023-42929-Why-Do-We-Need-The-App-Container-Protection/) the App Container Protection
- [SLAP & FLOP](https://predictors.fail) speculative execution attack
- (since Safari 18.4) Cookies Having Independent Partitioned State ([CHIPS](https://webkit.org/blog/16574/webkit-features-in-safari-18-4/#networking))

---
---

**🔒 Stay Safe and Secure!**
