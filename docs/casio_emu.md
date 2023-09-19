---
title: Casio calculator emulators
layout: default
---

# Casio calculator emulators
{: .no_toc }
From Calcupedia, the free calculator encyclopedia
{: .fs-2 }

Over the years, [Casio](https://wikipedia.org/wiki/Casio) has made emulators of their [scientific calculators](https://wikipedia.org/wiki/Scientific_calculator). On their [software](https://edu.casio.com/softwarelicense) page, there are downloads of calculator emulator subscriptions (for Windows) that have a 90-day trial period.

<details open markdown="block">
<summary>
    Contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Emulator subscriptions
### What is currently known ###
If you have started a trial period, downloading another evaluation emulator would actually use the same trial period. For example, if you have opened an evaluation Casio fx-570/991EX emulator and used it for a day, downloading and opening a Casio fx-580VN X evaluation emulator will show that you have 89 days left before a license is required. Uninstalling will not affect anything. This is because the trial license actually uses the same application name and version, therefore it is treated as one single application.

Casio uses SafeNet Sentinel technology as the license system. You can see this by going to `C:\ProgramData` (`ProgramData` is a system folder), where you will see a folder titled `SafeNet Sentinel`. The official guide to set up a network server made by Casio also tells you to download "Sentinel RMS License Manager". Not much is known about this SafeNet Sentinel technology, other than the fact that it definitely was secure *for the average user*.

Deleting the `C:\ProgramData\SafeNet Sentinel` folder will immediately invalidate the trial period. If the trial period gets invalidated, on startup, this will appear:<br>
*A problem was detected with the license.<br>Use the procedure displayed on the next screen that appears to recover the license.*

You are then prompted to download a file named `lscgcln.txt` and send it to Casio's customer support team. After a few days, the support team would give you a `recovery.lic` file that you would use to re-activate the software.[^1]

### Bypassing activation
#### Using a sandbox
The easiest way to bypass activation is by using a [sandbox](https://wikipedia.org/wiki/Sandbox) like Windows Sandbox or [Sandboxie](https://wikipedia.org/wiki/Sandboxie). This way, you will never run out of trial time.

The basic steps to do this with Windows Sandbox are:
1. [Enable Windows Sandbox.](https://learn.microsoft.com/en-us/windows/security/application-security/application-isolation/windows-sandbox/windows-sandbox-overview#installation)
2. Open Windows Sandbox, which will create a sandbox environment. Now install the emulator in the sandbox.
3. When you're done, close the sandbox. Keep in mind that **everything** will be deleted.

This method is easy to perform, but is very slow, and very frustrating because you have to set up the sandbox every time. Some have worked around this by preparing a folder with all the required software and simply copying it to the sandbox, however it is still very frustrating. This method is only recommended if you are perfectly okay with setting up a sandbox multiple times, or if you need to mass-install a lot of emulators and don't need them much.

#### Modifying the emulator code
The harder but more efficient way to bypass activation is to patch the emulator to run the main emulator code no matter what. This way, you do not need a sandbox environment.

##### Pre-patched versions
If you search hard enough, you can find pre-patched/cracked versions of these emulators. However, these cracks usually don't use the latest version.

The only known cracked version of these emulators to exist is the cracked version of the Casio fx-580VN X emulator (version 02.00.0000.0000), which you can easily find by searching for `fx-580vn x emulator crack`. The websites are obviously in Vietnamese, since the fx-580VN X model is common among the Vietnamese. The Vietnamese are also usually very generous and don't lead you to viruses.<br>
The crack can be downloaded [here](https://bit.ly/fx-580-VN-X). <span class="text-red-300">If your country bans piracy, **do not download this crack** if you haven't legally purchased a license.</span><br>
If you cannot read the Vietnamese install instructions, installing it is pretty straightforward: simply install the evaluation version using the provided installer, then copy `Crack\fx-580VN X Emulator.exe` to the emulator's install directory. The "cracked" `CLASSWIZ_P20.dll` is just a bitmap swap, so you don't have to copy it over.

You can also find a standalone cracked fx-570VN PLUS emulator  named *RC fx-570VN PLUS Emulator*. It's a heavily modified version of the fx-570VN PLUS Emulator from the fx-ES PLUS Emulator pack (version 3.02.1.0) by QLam Xmaster (according to the about dialog). Here's what's different from the regular version:
- The interface is almost completely modified to be Vietnamese.
- At the bottom of the main window is a message saying: *cracked version for HTKC :)* (it is currently unknown what HTKC means)
- Some options are disabled for some reason; specifically *x3 Zoom*, *Emulator Manual*, and *License* (changed to *License hacked*). You can force x3 zoom with a simple registry hack (open Command Prompt as an administrator, paste in `reg add "HKCU\Software\CASIO\U8EMU\Casio fx570vn plus\RC fx-570VN PLUS" /v ZOOM /t REG_DWORD /d 3 /f` and press Enter).
- The about dialog has some Vietnamese added, which appears to only using ASCII characters. It says: *Giả lập sử dụng y như máy thiệt! Có thể chụp màn hình phục vụ cho trao đổi toán học.* (Use the emulator just like the real calculator! You can capture screenshots for math exchange.)
You can download this version [below](#downloads).

If you search for "QLam Xmaster", eventually you'll find two more versions of this mod also named *RC fx-570VN PLUS Emulator*, a version with the modded Vietnamese UI, and a version with the UI intact. They are functionally identical to the version mentioned above. Both have the same content in the about dialog, however there are links to QLam's website and Facebook page. The bottom of the main window now says *Rebuilded by QLam Xmaster* in both versions, and the EXE filename in both versions has a `_patched` suffix. The version mentioned above was probably a modified version of QLam's mod with the Vietnamese UI, as evident by the first part in the about dialog in the modified mod using Unicode Vietnamese characters rather than ASCII.<br>
Both of these versions are also linked [below](#downloads).

##### DIY patching
Since it's very hard to find cracked versions of these emulators, you probably need to patch it yourself.

This guide below uses [Ghidra](https://wikipedia.org/wiki/Ghidra), an open-source reverse-engineering tool developed by the [National Security Agency](https://wikipedia.org/wiki/National_Security_Agency) of the United States, to patch the DLL file `ActivationFx.dll` to bypass activation.<br>
<span class="text-red-300"><u><b>DISCLAIMER:</b></u> Casio's emulators are **[proprietary software](https://wikipedia.org/wiki/Proprietary_software)**. If your country bans [piracy](https://wikipedia.org/wiki/Piracy), please **do not** follow the guide below if you haven't legally purchased a license. The guide below is for **educational and informational purposes only**.</span>

Please read the following before doing the guide below:
- This guide is only recommended if you need to install 1 or 2 emulators so you can use them as long as you want, because this guide takes, at minimum, around **20 minutes** to do. A majority of that time is spent waiting for auto-analyzation to finish, and the auto-analyzation time can change depending on your computer's speed.
- The guide applies to all Casio calculator emulators with a trial period.
- While the guide uses Ghidra, you can use any reverse-engineering tool to patch the EXE and bypass the activation process.

1. Navigate to where the emulator you want to patch is installed. Create a backup of the DLL `ActivationFx.dll`, then copy its path (on Windows: click on the *original* (not the backup) `ActivationFx.dll`, right-click and select *Copy as path*.)
2. [Download Ghidra](https://github.com/NationalSecurityAgency/ghidra/releases/latest).
3. Open Ghidra and create a new project (name it whatever you want).
4. In the newly created project, press I to bring up an *Import File* window. In the *File name* field, paste the path to `ActivationFx.dll` that you copied from earlier. Click on *Select File To Import*, then click OK. Wait for the file to import.
5. Double-click on the file you just imported to open the file with the *Code Browser*.
6. Click *Yes* when you are prompted to analyze the file. Then in the window that appears click *Analyze*. Wait for the auto-analyzation to finish. You can look at the bottom right of the *Code Browser*, and if you see no progress bar, auto-analyzation is done, and you can move on.
7. After auto-analyzation is done, in the *Symbol Tree* tab, click on *Functions* > `AcvFx_` > `AcvFx_IsActivationDialog2`.
8. Look at the Decompile tab. You should see some C code. Click on the very first line in the function. Press Ctrl+Shift+G, close the window that pops up, and wait for Ghidra to construct an assembler.
9. When done, you'll see two fields. Make sure the first field is `MOV` and the second field is `EAX, 0x1`. Press Enter.
10. Under the instruction you patched is a hex byte. Select it and Ctrl+Shift+G again. Now make sure the first field is `RET` and the second field is `0xc`. Press Enter.
11. Press O to bring up the *Export Program* dialog. Select the output as *PE* or *Original File*, and set the output filename to the path to `ActivationFx.dll`. You can repeat step 1 to grab the path again (don't create a backup this time, unless you haven't).
12. Press *OK*. In the dialog box that appears click *Overwrite*. **Make sure you have saved a backup of `ActivationFx.dll`!**
13. Wait for Ghidra to export the DLL. When it's done, a big dialog box will appear. Press Escape to close it. You can now close Ghidra, and delete Ghidra and the project you just made if you want.
14. Profit!

Now, when starting the patched emulator, no activation dialogs will appear, even if the trial period has expired or has been invalidated.

## Version numbers
Casio usually uses different version numbers, in their emulators and in the emulator box/listing page. Here are some version number formats that Casio uses in their emulators:
- Emulators from the fx-ES PLUS Emulator pack use the version number formats `X.X.X.X Y` and `X.XX.X.X` (ex. `3.0.0.0 B` for version 3.0 B emulators and `4.00.0.0` for version 4.0 emulators).
- Modern emulators such as the ClassWiz (EX) emulators and fx-ES PLUS re-release emulators use the version number format `XX.XX.XXXX.XXXX` (ex. `02.01.0030.0000` for ClassWiz emulator version 2.01.0030).

## ClassPad ClassWiz emulators
On October 20, 2022, Casio released [ClassPad](https://classpad.net) version 4, which added a ClassWiz emulator feature. These emulators are not investigated thoroughly, however they definitely use the same ROM from the emulator subscription versions. EX and CW model emulators are included, alongside some extra EX models that didn't have an emulator subscription available.

Of course, the ClassWiz emulator feature is paid, however you can easily unlock the feature (and all VIP features) by installing [Tampermonkey](https://www.tampermonkey.net), then installing [this userscript](https://gamingwithevets.github.io/stuff/vip.user.js).

## Lost and unreleased emulators
Some of Casio's emulators/emulator packs are currently lost or kept private for probably forever. These are some currently and/or used to be lost or unreleased Casio emulators:

- **fx-ES Emulator** (ES model emulator pack):
  - <span class="text-red-300">**Partially found.**</span>
  - Contains emulators for 4 models: fx-82ES, fx-83ES, fx-300ES, and fx-82AU. Only a leaked fx-82ES emulator (1.00 Sample) is available on the internet, while version 1.1 emulators are completely lost.
  - Casio no longer sells this pack, and it wasn't archived by most. No ISO images and *almost* no emulators from the pack have resurfaced on the internet. Instead, you can only find some images of the version 1.1 box and CD, as well as some manuals showing what the emulator looks like and how it would've been installed and uninstalled.
- **FC-x00V Emulator** (financial calculator emulator):
  - <span class="text-red-300">**Lost.**</span>
  - These emulators are also part of Casio's paid products, and they met the same fate just like with the fx-ES Emulator pack. These emulators are largely unpopular partly because it's for finance rather than something you'd use in math class, and probably only a very small number of people actually bought them. To this day, no copies of the emulators were found. The only evidence of them existing are some YouTube videos showcasing the emulators.
- **fx-ES PLUS Emulator** (ES PLUS model emulator pack):
  - <span class="text-red-300">**Partially found.**</span>
  - This pack also met the same fate as the fx-ES Emulator pack, however we do have a full (cracked) version 4.0 pack, as well as a version 3.02.1.0 (albeit modified) fx-570VN PLUS Emulator.
- **ClassWiz Emulator Subscription** (EX model emulator collection):
  - <span class="text-red-300">**Partially found.**</span>
  - 6 versions are known to exist:
    - 01.00.0000.0000 (possibly unreleased)[^3]
    - 02.00.0000.0000 (v2.00)
    - 02.00.0010.0000 (v2.00.0010)
    - 02.01.0000.0000 (v2.01.0000)
    - 02.01.0020.0000 (v2.01.0020)
    - 02.01.0030.0000 (v2.01.0030) (latest version as of 2023)
  - When Casio releases new emulator versions, they replace the old versions with the new ones, and these are not well archived, so the old versions are very easily lost.
- **fx-ES PLUS Emulator Subscription** (ES PLUS re-release model emulator collection):
  - <span class="text-red-300">**Partially found.**</span>
  - 3 versions are known to exist:
    - 05.00.0000.0000 (v5.00)
    - 05.00.0010.0000 (v5.00.0010)
    - 05.00.0020.0000 (v5.00.0020) (latest version as of 2023)
  - Same situation as the ClassWiz evaluation emulators.
- **fx-ClassWiz Emulator** (CW model emulator collection):
  - <span class="text-red-300">**Unreleased.**</span>
  - Known to exist from [this image](https://nhutnguyenminh.com/wp-content/uploads/2022/09/gia-lap-casio-fx-880-btg-2.png) of an offline fx-880BTG emulator. According to the blog post that contains this image, this emulator was given to Bitex, and they probably won't release it for copyright reasons. Meanwhile, Casio hasn't yet released any official offline ClassWiz (CW) emulators, and currently only online ones on ClassPad.

## Downloads
This section will (and aims to) contain downloads for all **official** Casio emulators.

<table>
<caption>Emulator downloads
</caption>
<tbody><tr>
<th>Name</th>
<th>Download</th>
<th>Notes
</th></tr>
<tr>
<td>fx-82ES for Windows</td>
<td><a href="https://www.omnimaga.org/other-calculator-discussion-and-news/the-way-to-upgrade-casio-fx-82es-to-fx-991es-for-version-b/?action=dlattach;attach=9039">Download (1.00 Sample)</a>
</td></tr>
<tr>
<td rowspan="4">fx-ES PLUS Emulator</td>
<td><a href="https://bit.ly/fx-ES">Download (4.00.0.0)</a></td>
<td>If prompted for an installation key, you can just input an invalid one and click <i>Next</i>.
</td></tr>
<tr>
<td><a href="https://4share.vn/f/7043464246434144/Casio%20fx-570VN%20PLUS.rar">RC fx-570VN PLUS Emulator (3.02.1.0)</a> (modded mod, Vietnamese UI)</td>
<td>If you cannot read Vietnamese: scroll down, solve the reCAPTCHA, then click on the button right below that says <i>TẢI XUỐNG</i>.
</td></tr>
<tr>
<td><a href="https://www.mediafire.com/download/f9vzhflpjlm2bv1/Casio_fx-570VN_plus_qlam_eng.7z">RC fx-570VN PLUS Emulator (3.02.1.0)</a> (original mod, English UI)
</td></tr>
<tr>
<td><a href="https://www.mediafire.com/download/003i6c6c8dgsb8w/Casio_fx-570VN_plus_qlam.7z">RC fx-570VN PLUS Emulator (3.02.1.0)</a> (original mod, Vietnamese UI)
</td></tr>
<tr>
<td><span title="Models: fx-82ES PLUS-BK, fx-85/350ES PLUS (A); fx-82ES PLUS-WE (AW); fx-95SG PLUS (E); fx-82AU PLUS (F); fx-500VN PLUS (G); fx-92B Collège 2D+ (H); fx-86DE PLUS (I); fx-92 Collège 2D+ (J)" style="border-bottom:1px dotted">fx-ES PLUS Emulator (Trial)</span></td>
<td><a href="https://cdn.discordapp.com/attachments/840569630950424626/1102952139417980989/fx-ES_PLUS_Emulator_Trial.7z">Download (3.0.0.0 B)</a></td>
<td>Requires <a href="https://www.microsoft.com/en-us/download/confirmation.aspx?id=26347">Microsoft Visual C++ 2005 SP1 (x86)</a>
</td></tr>
<tr>
<td>fx-82/85/350EX Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19568">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-570/991EX Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19567">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-82/85/350CN X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20139">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-991CN X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20140">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-530AZ Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19578">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-92B Spéciale Collège Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19574">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-87DE X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19572">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-991DE X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19571">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-82AR X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19577">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-95AR X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19576">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-570/991AR X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19575">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-82/85/350SP X/X II Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19570">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-570/991SP X/X II Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19569">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-82/350LA X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19671">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-570/991LA X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19670">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-82/85/350CE X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19911">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-991CE X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19912">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-92+ Spéciale Collège Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=19573">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-97SG X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20107">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td rowspan="3">fx-580VN X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20109">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td><a href="https://drive.google.com/file/d/18JQeSgeRuoHaG01__aL0dqzHLwIf71Sx/view?usp=drive_link">Download (02.01.0020.0000)</a>
</td></tr>
<tr>
<td><a href="https://drive.google.com/file/d/1HUneXUdPzDAROu2ZDv6rjiVufpb1t21l/view?usp=drive_link">Download (02.00.0000.0000)</a>
</td></tr>
<tr>
<td>fx-83/85GT X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20134">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-82/85DE X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20150">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-991RS X Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20430">Download (02.01.0030.0000)</a>
</td></tr>
<tr>
<td>fx-82/85/350ES PLUS 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20141">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td>fx-570/991ES PLUS 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20142">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td>fx-300ES PLUS 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20143">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td>fx-115ES PLUS 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20144">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td>fx-991ES PLUS C 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20145">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td>fx-82ZA PLUS II Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20146">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td>fx-991ZA PLUS II Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20147">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td>fx-82/350LA PLUS 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20148">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td>fx-570/991LA PLUS 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20149">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td>fx-87DE PLUS 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20151">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td>fx-991ID PLUS 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20152">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td>fx-570VN PLUS 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20153">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td rowspan="2">fx-82AU PLUS II 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20154">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td><a href="https://casioeducation.com.au/wp-content/uploads/softwares/fx_82AUPLUSII_2ndEd_setup.exe">Download (05.00.0010.0000)</a>
</td></tr>
<tr>
<td rowspan="2">fx-100AU PLUS 2nd edition Emulator</td>
<td><a href="https://edu.casio.com/freetrial/en/download2.php?lang=1&amp;file_no=20155">Download (05.00.0020.0000)</a>
</td></tr>
<tr>
<td><a href="https://casioeducation.com.au/wp-content/uploads/softwares/fx_100AUPLUS_2ndEd_setup.exe">Download (05.00.0010.0000)</a>
</td></tr></tbody></table>

## Notes
[^1]: Information taken from Casio's [license recovery](https://edu.casio.com/softwarelicense/activation_licenserecovery) page.
[^2]: This code change is to prevent a `0xF0000005` error (*Connection to the server where the CASIO Network License Server is running failed.*) which will close the emulator immediately if it gets triggered.
[^3]: Known to exist from [this image](https://edu.casio.com/assets/images/softwarelicense/importantinformation/ja/img04.png).
[^4]: [Extra note] the "Copying the emulator EXE path" step.
