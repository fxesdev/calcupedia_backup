---
title: Calculator self-test
layout: default
---

# Calculator self-test
{: .no_toc }
From Calcupedia, the free calculator encyclopedia
{: .fs-2 }

{: .warning-title }
> The information on this page may be incorrect.
>
> If you think something on this page was incorrect, please edit the corresponding page on Calcupedia with the correct information.<br>
> For protected pages, you can contact the administrators to fix the information on the page.

The calculator self-test mode is a special mode used to diagnose and fix bugs before release. It can also be used to [identify fake calculators](/docs/identify_fakes.html).

<details open markdown="block">
<summary>
    Contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## General layout
The self-test mode of a scientific calculator usually consists of 3 tests:
- **Display test**: Self-explanatory.
- **Version check**: Displays the version from the ROM and, on most models, checks if the calculated checksum matches the checksum in the ROM.
- **Key test**: A number is displayed. You will have to press keys in the right order for the number to increase, and no key is ever repeated. The key test finishes when all keys are pressed.

In addition to the above, a graphing calculator's self-test mode generally includes:
- Memory check
- I/O interface check (may include non-contact data interface such as infrared)
- Battery status check

## Casio calculators
On [Casio](https://wikipedia.org/wiki/Casio) calculators (and their clones and fakes), the button combination for accessing the self-test mode is usually <span class="k_es">q</span>+<span class="k_es">7</span>+<span class="k_es">W</span>, which means to hold <span class="k_es">q</span> and <span class="k_es">7</span> and press <span class="k_es">W</span>.

Casio's self-test modes are **never translated**. Usually, only the contrast screen in the ES PLUS series is translated because the text is hard-coded into its strings, and the diagnostic mode just displays the regular contrast screen with the contrast hex value displayed and a larger range (see below).

### MS series
1. Press <span class="k_ms">q</span>+<span class="k_ms">7</span>+<span class="k_ms">W</span>. All the LCD segments should light up. Press <span class="k_ms">q</span> to cycle through the display tests.
2. After pressing <span class="k_ms">q</span> enough times, you will see the number 0 on the screen. This is the key test. Here is what you want to press:<br>
- First press <span class="k_ms">q</span> then <span class="k_ms">Q</span>. The number should increase to 2.
- Press <span class="k_ms">w</span>. If the number doesn't change to 3 even though your <span class="k_ms">w</span> button works fine outside of the self-test mode, you are unfortunately stuck and unable to continue the key test.
- Press in order: <span class="k_ms">!E$</span>, then the 4-key row (left to right), then <span class="k_ms">R</span>. The number should be increased to 11.
- Now press (from the row under the 4-key row) each key in each row, left to right. When all keys are pressed, a screen with `OK` should appear.

#### Revised MS series
On revised MS models, the code was based on the ES PLUS series codebase. The new diagnostic mode was also ported over to work on the revised MS series' displays.

After pressing <span class="k_ms">q</span>+<span class="k_ms">7</span>+<span class="k_ms">W</span>, you will first see a screen looking like this:
```
DIAGNOSTIC
AC
```
Then, you would press <span class="k_ms">9</span> just like in the ES PLUS models (there isn't even a timer to kick you out if you aren't fast enough), then <span class="k_ms">q</span> 5 times. You would see this screen that looks something like this:
```
ROM506  P000
AC
```
This screen looks similar to the [ES series self-test mode](#es-series), where the ROM version number and the mode is displayed (`Pxxx` in this case). There are only 2 known ROM version numbers: `ROM506` and `ROM509`.

After pressing <span class="k_ms">C</span> the contrast screen should appear but with some things added and (obviously) a greater range. You can <span class="k_ms">C</span> through it to get to the key test, which is the same as the ES PLUS series, with the same key order (<span class="k_ms">qQE$w</span> etc.) and key number placement (top left instead of the usual bottom right). Finally you should see this screen:
```
TEST OK
AC
```

##### MS PLUS 2nd edition series
The MS PLUS 2nd edition models use the ES PLUS 2nd edition codebase, retaining most of the revised diagnostic mode. The fake diagnostic screen was also changed to look something like this:
```
1+1=?
AC
```
Internally, the diagnostic mode locking works just like the ES PLUS 2nd edition series. The revised MS diagnostic mode was also copied over.

### ES series
*Not to be confused with the [ES PLUS series self-test mode](#es-plus-series).*
{: .hatnote }

1. Press <span class="k_es">q</span>+<span class="k_es">7</span>+<span class="k_es">W</span>. The entire screen and the top bar should all light up. Press <span class="k_es">q</span> to cycle through the display tests.
2. After pressing <span class="k_es">q</span> enough times, you will see a screen looking something like this (fx-500ES used as example):<br><span class="esps">ROM 018<br>MODE P2<br>Press AC</span>
<ol start="3">
<li>Press <span class="k_es">C</span>. You will see a contrast setting screen, but with <span class="esps">XXh</span> displayed, which is the contrast value in hexadecimal. The allowed range in the self-test mode (<span class="esps">00h</span> - <span class="esps">1Ah</span>) is also larger than the normal intended range (<span class="esps">04h</span> - <span class="esps">1Ah</span>).</li>
<li>Press <span class="k_es">C</span>, and you will see <span class="esps">0</span> on the screen, which is the key test. Press in order: <span class="k_es">qQE$w</span>, then the two keys under <span class="k_es">q</span> and <span class="k_es">Q</span> (left to right), <span class="k_es">!R</span>, then the two keys under <span class="k_es">w</span> and <span class="k_es">W</span> (left to right). Now simply press the remaining keys, top to bottom, left to right.</li>
</ol>

If you change the contrast in self-test mode, you will have to exit the self-test (without pressing <span class="k_es">W</span>) to keep the setting, or else it'll just be reset to the default (<span class="esps">11h</span>). Also, if the contrast was set outside the intended range when exiting the self-test, pressing <span class="k_es">W</span> or using the contrast menu will reset the contrast setting.

### ES PLUS series
*Not to be confused with the [ES series self-test mode](#es-series) or the [ES PLUS 2nd edition series self-test mode](#es-plus-2nd edition-series).*
{: .hatnote }

Pressing <span class="k_es">q</span>+<span class="k_es">7</span>+<span class="k_es">W</span> displays this screen:<br><span class="esps">DIAGNOSTIC<br><br><br>Press AC</span>

Here, most would likely press <span class="k_es">C</span>, but it just exits self-test mode. You are actually required to press <span class="k_es">9</span> within 5.5 seconds to continue.

Then, the display test is the same as the ES series. The version check is different; the screen doesn't appear all at once. The entire fully-drawn screen should look like this (fx-570ES PLUS used as example):<br><span class="esps">GY454X VerE<br>SUM 8929 OK<br>Pd- Read OK<br>Press AC</span><br>
Where:
- <span class="esps">GY454X</span>: Version.
- <span class="esps">VerE</span>: Revision.
- <span class="esps">SUM 8929 OK</span>: Calculated checksum. <span class="esps">OK</span> means the checksum matches the one in the ROM.

You can use the table below to check if the version and checksum is for the correct model.

After pressing <span class="k_es">C</span>, the contrast setting screen appears just like in the ES series models. The allowed range in the self-test mode (<span class="esps">00h</span> - <span class="esps">1Fh</span>) is changed, but is still larger than the normal intended range (<span class="esps">04h</span> - <span class="esps">1Dh</span>). The contrast resetting in the ES models is still in ES PLUS models.

There's no change to the key test in the ES PLUS series models.

<table>
<caption>Version + checksum list
</caption>
<tbody><tr>
<th>Version</th>
<th>Revision</th>
<th>Checksum</th>
<th>Corresponding model(s)
</th></tr>
<tr>
<td rowspan="3"><span class="esps">GY-450</span></td>
<td>A</td>
<td><span class="esps">713C</span></td>
<td rowspan="4">fx-82ES PLUS
</td></tr>
<tr>
<td>B</td>
<td><span class="esps">0E3F</span>
</td></tr>
<tr>
<td>E</td>
<td><span class="esps">6370</span>
</td></tr>
<tr>
<td><span class="esps">GY450X</span></td>
<td>E</td>
<td><span class="esps">6379</span>
</td></tr>
<tr>
<td><span class="esps">GY-451</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-85ES PLUS
</td></tr>
<tr>
<td><span class="esps">GY-452</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-350ES PLUS
</td></tr>
<tr>
<td><span class="esps">GY-453</span></td>
<td>B</td>
<td><span class="esps">70CA</span></td>
<td rowspan="2">fx-95ES PLUS
</td></tr>
<tr>
<td><span class="esps">GY453X</span></td>
<td>E</td>
<td><span class="esps">E677</span>
</td></tr>
<tr>
<td><span class="esps">GY-454</span></td>
<td>A</td>
<td><span class="esps">F929</span></td>
<td rowspan="2">fx-570ES PLUS
</td></tr>
<tr>
<td><span class="esps">GY454X</span></td>
<td>E</td>
<td><span class="esps">8929</span>
</td></tr>
<tr>
<td rowspan="2"><span class="esps">GY-455</span></td>
<td>A</td>
<td><span class="esps">CD04</span></td>
<td rowspan="4">fx-991ES PLUS
</td></tr>
<tr>
<td>B</td>
<td><span class="esps">87ED</span>
</td></tr>
<tr>
<td rowspan="2"><span class="esps">GY455X</span></td>
<td>E</td>
<td><span class="esps">8928</span>
</td></tr>
<tr>
<td>F</td>
<td><span class="esps">A33D</span>
</td></tr>
<tr>
<td><span class="esps">GY456X</span></td>
<td>B</td>
<td><span class="esps">7A95</span></td>
<td>fx-373ES
</td></tr>
<tr>
<td><span class="esps">GY-458</span></td>
<td>B</td>
<td><span class="esps">4C05</span></td>
<td>fx-95SG PLUS
</td></tr>
<tr>
<td rowspan="2"><span class="esps">GY-459</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td rowspan="3">fx-82AU PLUS
</td></tr>
<tr>
<td>B</td>
<td><i>Unknown</i>
</td></tr>
<tr>
<td><span class="esps">GY459X</span></td>
<td>E</td>
<td><i>Unknown</i>
</td></tr>
<tr>
<td><span class="esps">GY-460</span></td>
<td>C</td>
<td><i>Unknown</i></td>
<td rowspan="2">fx-500VN PLUS
</td></tr>
<tr>
<td><span class="esps">GY460X</span></td>
<td>F</td>
<td><span class="esps">D29B</span>
</td></tr>
<tr>
<td><span class="esps">GY-461</span></td>
<td>B</td>
<td><i>Unknown</i></td>
<td rowspan="2">fx-92B Collège 2D+
</td></tr>
<tr>
<td><span class="esps">GY461X</span></td>
<td>E</td>
<td><i>Unknown</i>
</td></tr>
<tr>
<td><span class="esps">GY-462</span></td>
<td>C</td>
<td><i>Unknown</i></td>
<td>fx-86DE PLUS (launch models)
</td></tr>
<tr>
<td><span class="esps">GY465X</span></td>
<td>G</td>
<td><span class="esps">7A03</span></td>
<td>fx-83GT PLUS
</td></tr>
<tr>
<td><span class="esps">GY-467</span></td>
<td>A</td>
<td><span class="esps">23F8</span></td>
<td rowspan="2">fx-993ES, fx-510AZ
</td></tr>
<tr>
<td><span class="esps">GY467X</span></td>
<td>B</td>
<td><span class="esps">3D37</span>
</td></tr>
<tr>
<td><span class="esps">GY-468</span></td>
<td>A</td>
<td><span class="esps">D884</span></td>
<td rowspan="2">fx-92 Collège 2D+
</td></tr>
<tr>
<td><span class="esps">GY468X</span></td>
<td>B</td>
<td><span class="esps">BEA8</span>
</td></tr>
<tr>
<td><span class="esps">GY477X</span></td>
<td>F</td>
<td><span class="esps">6301</span></td>
<td>OH-300ES PLUS (projector model)
</td></tr>
<tr>
<td><span class="esps">LY-707</span></td>
<td>A</td>
<td><span class="esps">FC53</span></td>
<td>fx-55 PLUS
</td></tr>
<tr>
<td><span class="esps">LY708X</span></td>
<td>A</td>
<td><span class="esps">71F1</span></td>
<td>fx-96SG PLUS
</td></tr>
<tr>
<td><span class="esps">LY709X</span></td>
<td>A</td>
<td><span class="esps">7524</span></td>
<td>fx-991ID PLUS
</td></tr>
<tr>
<td><span class="esps">LY710X</span></td>
<td>A</td>
<td><span class="esps">D457</span></td>
<td>fx-570VN PLUS
</td></tr>
<tr>
<td><span class="esps">LY711X</span></td>
<td>A</td>
<td><span class="esps">0A69</span></td>
<td>fx-82AU PLUS II
</td></tr>
<tr>
<td><span class="esps">LY712X</span></td>
<td>A</td>
<td><span class="esps">B7C6</span></td>
<td>fx-100AU PLUS
</td></tr>
<tr>
<td><span class="esps">LY713X</span></td>
<td>A</td>
<td><span class="esps">F854</span></td>
<td>fx-82ES PLUS A
</td></tr>
<tr>
<td><span class="esps">LY717X</span></td>
<td>A</td>
<td><span class="esps">6A23</span></td>
<td>fx-375ES
</td></tr>
<tr>
<td><span class="esps">LY718X</span></td>
<td>A</td>
<td><span class="esps">F0E2</span></td>
<td>fx-915ES
</td></tr>
<tr>
<td><span class="esps">LY719X</span></td>
<td>A</td>
<td><span class="esps">D6D0</span></td>
<td>fx-995ES, fx-520AZ
</td></tr>
<tr>
<td><span class="esps">LY720X</span></td>
<td>G</td>
<td><span class="esps">7A04</span></td>
<td>fx-85GT PLUS
</td></tr>
<tr>
<td><span class="esps">LY721X</span></td>
<td>A</td>
<td><span class="esps">59CB</span></td>
<td>fx-82DE PLUS
</td></tr>
<tr>
<td><span class="esps">LY722X</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-85DE PLUS
</td></tr>
<tr>
<td><span class="esps">LY723X</span></td>
<td>A</td>
<td><span class="esps">5D78</span></td>
<td>fx-86DE PLUS (later models)
</td></tr>
<tr>
<td rowspan="2"><span class="esps">LY724X</span></td>
<td>A</td>
<td><span class="esps">0B80</span></td>
<td rowspan="2">fx-991DE PLUS
</td></tr>
<tr>
<td>B</td>
<td><span class="esps">D5F1</span>
</td></tr>
<tr>
<td><span class="esps">LY725X</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-82ZA PLUS
</td></tr>
<tr>
<td><span class="esps">LY726X</span></td>
<td>A</td>
<td><span class="esps">341B</span></td>
<td>fx-300ES PLUS
</td></tr>
<tr>
<td rowspan="2"><span class="esps">LY727X</span></td>
<td>A</td>
<td><span class="esps">11B4</span></td>
<td rowspan="2">fx-115ES PLUS, fx-991ES PLUS C
</td></tr>
<tr>
<td>B</td>
<td><span class="esps">2D4E</span>
</td></tr></tbody></table>

#### ES PLUS 2nd edition series

The ES PLUS 2nd edition series self-test mode is pretty much unchanged from the regular ES PLUS series. However, there are some differences:
<ul>
<li>The <span class="esps">DIAGNOSTIC</span> screen has been replaced with a screen that looks something like this:<br><span class="esps">1+1=?&nbsp; &nbsp; &nbsp; 00/01<br><br><br>Press AC</span>
<ul>
<li><span class="esps">1+1=?</span> is a random addition/subtraction math problem that only uses 2 single-digit numbers, and with the result between 1 and 5.</li>
<li><span class="esps">00/01</span> is a counter that keeps track of the number of problems you solved, and the total amount of problems generated. Both numbers are unsigned hex bytes (they do overflow) and are saved to RAM. They are reset if the diagnostic mode or the debug menu (see below) is activated, as that clears the entire RAM.</li>
<li>Pressing the key with the right answer will change the screen to display <span class="esps">TEST OK</span>. For wrong answers, you're just kicked out instantly.</li>
</ul></li>
<li>A debug menu can be accessed by pressing <span class="k_es">6</span> and behaves just like in the EX series. Two key test options were added (<span class="esps">Key1</span> and <span class="esps">Key2</span>), which allows testing of only the first 29 keys (excluding <span class="k_es">W</span>) or the last 20 keys. Currently only known to exist on the fx-570VN PLUS 2nd edition model. There is no battery/solar model check on the ES PLUS 2nd edition models.</li>
<li>If at least one math problem is solved, another byte stored right before the 2 math problem bytes (see above) is set to 1. If this byte is non-zero, the main diagnostic mode and debug menu are both unaccessible (pressing their keys just kick you out), unless certain criteria is met which causes this byte to reset to 0.</li>
</ul>

Version screens in ES PLUS 2nd edition models (and normal ES PLUS models as well) typically look like this (fx-570VN PLUS 2nd edition used as example):<br><span class="esps">CY-860 VerA<br>SUM 940B OK IDOK<br>Pd- Read OK<br>Press AC</span><br>
Where:
- <span class="esps">CY-860</span>: Version.
- <span class="esps">VerA</span>: Revision.
- <span class="esps">SUM 940B OK IDOK</span>: Calculated checksum. <span class="esps">OK</span> means the checksum matches the one in the ROM. The exact purpose of the "ID" check is unknown, but it will display <span class="esps">ID-\-</span> if the checksum was bad.

You can verify the version and checksum using the table below.

<table class="wikitable">
<caption>Version + checksum list
</caption>
<tbody><tr>
<th>Version</th>
<th>Revision</th>
<th>Checksum</th>
<th>Corresponding model(s)
</th></tr>
<tr>
<td><span class="esps">CY-840</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-82ES PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-841</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-85ES PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-842</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-350ES PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-844</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-570ES PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-845</span></td>
<td>A</td>
<td><span class="esps">7064</span></td>
<td>fx-991ES PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-846</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-300ES PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-847</span></td>
<td>A</td>
<td><span class="esps">3C5D</span></td>
<td>fx-115ES PLUS 2nd edition, fx-991ES PLUS C 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-848</span></td>
<td>B</td>
<td><i>Unknown</i></td>
<td>fx-82ZA PLUS II
</td></tr>
<tr>
<td><span class="esps">CY-849</span></td>
<td>B</td>
<td><span class="esps">06B3</span></td>
<td>fx-991ZA PLUS II
</td></tr>
<tr>
<td><span class="esps">CY-850</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-82LA PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-851</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-350LA PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-852</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-570LA PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-853</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-991LA PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-856</span></td>
<td>A</td>
<td><span class="esps">3E89</span></td>
<td>fx-87DE PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-857</span></td>
<td>A</td>
<td><span class="esps">A4DB</span></td>
<td>fx-375ES A
</td></tr>
<tr>
<td><span class="esps">CY-858</span></td>
<td>A</td>
<td><span class="esps">4C20</span></td>
<td>fx-82ES PLUS A 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-859</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-991ID PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-860</span></td>
<td>A</td>
<td><span class="esps">940B</span></td>
<td>fx-570VN PLUS 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-863</span></td>
<td>A</td>
<td><span class="esps">D958</span></td>
<td>fx-82AU PLUS II 2nd edition
</td></tr>
<tr>
<td><span class="esps">CY-864</span></td>
<td>A</td>
<td><span class="esps">8A4E</span></td>
<td>fx-100AU PLUS 2nd edition
</td></tr></tbody></table>

### ClassWiz series
#### EX models
Press <span class="k_ex">q</span>+<span class="k_ex">7</span>+<span class="k_ex">W</span>. You will see:<br><span class="cwxd">DIAGNOSTIC<br><br><br>Press AC</span>

Here, there are some menus you can access by pressing a key (except <span class="k_ex">C</span>) within 5 seconds:
- <span class="k_ex">8</span>: **Battery/solar model check.** A list of 8 keys is shown, and you will have to press them all. The key list assumes the key layout of ES PLUS models with the base-N logarithm function, such as the fx-991ES PLUS. After that, <span class="cwxd">Battery MODEL OK!</span> will appear under the key list. On models with a solar panel, if solar power is being used (that is, the panel isn't covered), <span class="cwxd">Solar MODEL OK!</span> will appear instead, and to get both messages to appear at the same time, you have to do the key presses with the solar panel covered, then remove the cover after <span class="cwxd">Battery MODEL OK!</span> appears.
- <span class="k_ex">6</span>: **Debug menu (some models only).** Allows you to choose between the display test, the version check screen, the key test, and the contrast screen.

The original diagnostic mode accessed by pressing <span class="k_ex">9</span> is still accessible, albeit with some differences from the ES PLUS series:
<ul>
<li>After pressing <span class="k_ex">9</span> you will see a precision test:<br><span class="cwxd">8888888888888888<br><br><br></span> &nbsp; &nbsp; &nbsp; <span class="cwxd">8.888888889¹⁵</span><br>Here you can press <span class="k_ex">q</span> for the display test.</li>
<li>
The version check initially only displays the version (fx-580VN X used as example):<br>
<span class="cwxd">CY-298 VerA<br><br><br>Press AC</span><br>
To actually view the checksum, you will have to press <span class="k_ex">w</span>, after that the screen will display the below (fx-580VN X used as example):<br>
<span class="cwxd">CY-298 VerA<br>SUM BB26 OK<br>P00 Read OK<br>Press AC</span><br>
Where:
<ul>
<li><span class="cwxd">CY-298</span>: Version.</li>
<li><span class="cwxd">VerA</span>: Revision.</li>
<li><span class="cwxd">SUM BB26 OK</span>: Calculated checksum. <span class="cwxd">OK</span> means the checksum matches the one in the ROM.</li>
</ul>
The checksum is displayed immediately if this screen is accessed through the debug menu.<br>You can verify the version and checksum using the table below.</li>
<li>The contrast setting is set to display after the key test.</li>
<li>If <span class="k_ex">w</span> was not pressed during the version check screen, pressing <span class="k_ex">C</span> goes to the key test. If it was pressed, pressing <span class="k_ex">C</span> will display the calculator's serial number. Pressing it again will take you to the key test.</li>
<li>The contrast setting in self-test mode has a range of <span class="cwxd">00h</span> - <span class="cwxd">2Ah</span>, while the intended range is <span class="cwxd">0Bh</span> -<span class="cwxd">1Fh</span>. The default setting is 14h. The contrast resetting still applies.</li>
</ul>

<table>
<caption>Version + checksum list
</caption>
<tbody><tr>
<th>Version</th>
<th>Revision</th>
<th>Checksum</th>
<th>Corresponding model(s)
</th></tr>
<tr>
<td><span class="cwxd">CY-230</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-82EX
</td></tr>
<tr>
<td><span class="cwxd">CY-231</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-85EX
</td></tr>
<tr>
<td><span class="cwxd">CY-232</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-350EX
</td></tr>
<tr>
<td rowspan="2"><span class="cwxd">CY-234</span></td>
<td>A</td>
<td><span class="cwxd">40B0</span></td>
<td rowspan="2">fx-570EX
</td></tr>
<tr>
<td>F</td>
<td><i>Unknown</i>
</td></tr>
<tr>
<td rowspan="3"><span class="cwxd">CY-235</span></td>
<td>A</td>
<td><span class="cwxd">3FB0</span></td>
<td rowspan="3">fx-991EX
</td></tr>
<tr>
<td>B</td>
<td><span class="cwxd">FC54</span>
</td></tr>
<tr>
<td>F</td>
<td><span class="cwxd">8F18</span>
</td></tr>
<tr>
<td rowspan="2"><span class="cwxd">CY-236</span></td>
<td>A</td>
<td><span class="cwxd">068B</span></td>
<td rowspan="2">fx-82CN X
</td></tr>
<tr>
<td>B</td>
<td><i>Unknown</i>
</td></tr>
<tr>
<td><span class="cwxd">CY-237</span></td>
<td>A</td>
<td><span class="cwxd">058B</span></td>
<td>fx-350CN X
</td></tr>
<tr>
<td><span class="cwxd">CY-238</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-95CN X
</td></tr>
<tr>
<td rowspan="3"><span class="cwxd">CY-239</span></td>
<td>A</td>
<td><span class="cwxd">EC3F</span></td>
<td rowspan="3">fx-991CN X
</td></tr>
<tr>
<td>B</td>
<td><span class="cwxd">7C9C</span>
</td></tr>
<tr>
<td>C</td>
<td><span class="cwxd">04A8</span>
</td></tr>
<tr>
<td><span class="cwxd">CY-240</span></td>
<td>A</td>
<td><span class="cwxd">20A1</span></td>
<td>fx-530AZ
</td></tr>
<tr>
<td rowspan="2"><span class="cwxd">CY-241</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td rowspan="2">fx-JP500
</td></tr>
<tr>
<td>B</td>
<td><span class="cwxd">A340</span>
</td></tr>
<tr>
<td><span class="cwxd">CY-242</span></td>
<td>A</td>
<td><span class="cwxd">6A2B</span></td>
<td>fx-JP700
</td></tr>
<tr>
<td rowspan="2"><span class="cwxd">CY-243</span></td>
<td>A</td>
<td><span class="cwxd">A0B7</span></td>
<td rowspan="2">fx-JP900
</td></tr>
<tr>
<td>F</td>
<td><span class="cwxd">8542</span>
</td></tr>
<tr>
<td><span class="cwxd">CY-246</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-92 Spéciale Collège
</td></tr>
<tr>
<td><span class="cwxd">CY-247</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-92B Spéciale Collège
</td></tr>
<tr>
<td rowspan="2"><span class="cwxd">CY-250</span></td>
<td>A</td>
<td><span class="cwxd">3D9C</span></td>
<td rowspan="2">fx-87DE X
</td></tr>
<tr>
<td>F</td>
<td><span class="cwxd">8142</span>
</td></tr>
<tr>
<td rowspan="3"><span class="cwxd">CY-251</span></td>
<td>A</td>
<td><span class="cwxd">D906</span></td>
<td rowspan="3">fx-991DE X
</td></tr>
<tr>
<td>E</td>
<td><span class="cwxd">ACE6</span>
</td></tr>
<tr>
<td>F</td>
<td><span class="cwxd">AD05</span>
</td></tr>
<tr>
<td><span class="cwxd">CY-252</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-82SP X
</td></tr>
<tr>
<td><span class="cwxd">CY-253</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-350SP X
</td></tr>
<tr>
<td><span class="cwxd">CY-254</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-570SP X
</td></tr>
<tr>
<td><span class="cwxd">CY-255</span></td>
<td>A</td>
<td><span class="cwxd">1FF7</span></td>
<td>fx-991SP X
</td></tr>
<tr>
<td><span class="cwxd">CY-256</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-82AR X
</td></tr>
<tr>
<td><span class="cwxd">CY-257</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-95AR X
</td></tr>
<tr>
<td><span class="cwxd">CY-258</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-570AR X
</td></tr>
<tr>
<td><span class="cwxd">CY-259</span></td>
<td>A</td>
<td><span class="cwxd">097B</span></td>
<td>fx-991AR X
</td></tr>
<tr>
<td><span class="cwxd">CY-266</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-82SP X II
</td></tr>
<tr>
<td><span class="cwxd">CY-267</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-350SP X II
</td></tr>
<tr>
<td><span class="cwxd">CY-268</span></td>
<td>F</td>
<td><i>Unknown</i></td>
<td>fx-570SP X II
</td></tr>
<tr>
<td><span class="cwxd">CY-269</span></td>
<td>F</td>
<td><span class="cwxd">EEE4</span></td>
<td>fx-991SP X II
</td></tr>
<tr>
<td><span class="cwxd">CY-270</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-82LA X
</td></tr>
<tr>
<td><span class="cwxd">CY-271</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-350LA X
</td></tr>
<tr>
<td><span class="cwxd">CY-272</span></td>
<td>F</td>
<td><i>Unknown</i></td>
<td>fx-570LA X
</td></tr>
<tr>
<td><span class="cwxd">CY-273</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-991LA X
</td></tr>
<tr>
<td><span class="cwxd">CY-291</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-82CE X
</td></tr>
<tr>
<td><span class="cwxd">CY-292</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-85CE X
</td></tr>
<tr>
<td><span class="cwxd">CY-293</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-350CE X
</td></tr>
<tr>
<td><span class="cwxd">CY-294</span></td>
<td>F</td>
<td><span class="cwxd">B28D</span></td>
<td>fx-991CE X
</td></tr>
<tr>
<td><span class="cwxd">CY-295</span></td>
<td>A</td>
<td><span class="cwxd">4502</span></td>
<td>fx-92+ Spéciale Collège
</td></tr>
<tr>
<td><span class="cwxd">CY-296</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-85SP X II
</td></tr>
<tr>
<td><span class="cwxd">CY-297</span></td>
<td>E</td>
<td><span class="cwxd">6F25</span></td>
<td>fx-97SG X
</td></tr>
<tr>
<td><span class="cwxd">CY-298</span></td>
<td>A</td>
<td><span class="cwxd">BB26</span></td>
<td>fx-580VN X
</td></tr>
<tr>
<td><span class="cwxd">CY-213</span></td>
<td>A</td>
<td><span class="cwxd">01D3</span></td>
<td>fx-83GT X
</td></tr>
<tr>
<td><span class="cwxd">CY-214</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-85GT X
</td></tr>
<tr>
<td><span class="cwxd">CY-215</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-82DE X
</td></tr>
<tr>
<td><span class="cwxd">CY-216</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-85DE X
</td></tr>
<tr>
<td><span class="cwxd">CY-217</span></td>
<td>A</td>
<td><span class="cwxd">2F15</span></td>
<td>fx-991RS X
</td></tr></tbody></table>

#### CW models
In the CW models, <span class="k_cw">q</span>+<span class="k_cw">7</span>+<span class="k_cw">W</span> does not work. You have to hold <span class="k_cw">T</span> in addition to <span class="k_cw">q</span> and <span class="k_cw">7</span>, which makes the combination <span class="k_cw">q</span>+<span class="k_cw">7</span>+<span class="k_cw">T</span>+<span class="k_cw">W</span>.<br>
In addition to the updated key combination, a new key combination was added, which is <span class="k_cw">T</span>+<span class="k_cw">C</span>+<span class="k_cw">W</span>. Most people in China know this key combination instead of the updated old one above.

<ul>
<li>Pressing <span class="k_cw">q</span>+<span class="k_cw">7</span>+<span class="k_cw">T</span>+<span class="k_cw">W</span> or <span class="k_cw">T</span>+<span class="k_cw">C</span>+<span class="k_cw">W</span> brings up the same math problem screen as the ES PLUS 2nd edition series. The only difference is that when you're kicked out on this screen, the <span class="k_cw">w</span>HOME menu pops up. The RAM is not cleared on the math problem screen, so all settings are retained.</li>
<li>The battery/solar model check and the debug menu make a return. The battery/solar model check has different keys displayed and actually refers to the CW models' keymap. The debug menu replaced the key test with <span class="espl">Key1 test</span> and <span class="espl">Key2 test</span>, which allows testing of only the first 27 keys (excluding <span class="k_cw">W</span>) or the last 20 keys.</li>
<li>The main diagnostic mode can still be accessed with <span class="k_cw">9</span>. There are some differences to the EX models:
<ul>
<li>After the final display test screen, the calculator freezes for about 1 second, then displays this screen (fx-880BTG used as example):<br><span class="cwcwd">EY-023<br>V.B&nbsp; Bt OK<br>SUM8113 OK<br>Press AC</span><br>Where:
<ul>
<li><span class="cwcwd">EY-023</span>: Version.</li>
<li><span class="cwcwd">V.B</span>: Revision.</li>
<li><span class="cwcwd">Bt OK</span>: It is assumed that <span class="cwcwd">Bt</span> stands for Battery, so this may be a battery model check.</li>
<li><span class="cwcwd">SUM8113 OK</span>: Calculated checksum. <span class="cwcwd">OK</span> means the checksum matches the one in the ROM.</li>
</ul>

A QR code is displayed next to the text, which when decoded, shows: <code>EY-___ V._ Bt OK SUM____ OK &lt;serial number&gt;</code> (underscores are blanks)<br>
You can verify the version and checksum with the table below.</li>
<li>Pressing <span class="k_cw">C</span> displays the serial number. Pressing <span class="k_cw">C</span> again will take you to the key test. After that, everything is the same as the EX models.</li>
</ul></li></ul>

<table>
<caption>Version + checksum list
</caption>
<tbody><tr>
<th>Version</th>
<th>Revision</th>
<th>Checksum</th>
<th>Corresponding model(s)
</th></tr>
<tr>
<td><span class="cwcwd">EY-001</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-82CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-002</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-85CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-003</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-350CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-004</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-570CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-005</span></td>
<td>A</td>
<td><span class="cwcwd">E05B</span></td>
<td>fx-991CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-006</span></td>
<td>A</td>
<td><span class="cwcwd">E111</span></td>
<td>fx-92 Collège
</td></tr>
<tr>
<td><span class="cwcwd">EY-007</span></td>
<td>A</td>
<td><span class="cwcwd">6930</span></td>
<td>fx-92B Secondaire
</td></tr>
<tr>
<td><span class="cwcwd">EY-008</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-82SP CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-009</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-85SP CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-010</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-570SP CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-011</span></td>
<td>A</td>
<td><span class="cwcwd">B293</span></td>
<td>fx-991SP CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-012</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-82DE CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-013</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-85DE CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-014</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-87DE CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-015</span></td>
<td>A</td>
<td><span class="cwcwd">A55F</span></td>
<td>fx-991DE CW
</td></tr>
<tr>
<td rowspan="2"><span class="cwcwd">EY-016</span></td>
<td>S2 (sample)</td>
<td><span class="cwcwd">8FCD</span></td>
<td>fx-800DE Z (pre-release model)
</td></tr>
<tr>
<td>A</td>
<td><span class="cwcwd">BC9D</span></td>
<td>fx-800DE CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-021</span></td>
<td>B</td>
<td><i>Unknown</i></td>
<td>fx-82NL
</td></tr>
<tr>
<td><span class="cwcwd">EY-023</span></td>
<td>B</td>
<td><span class="cwcwd">8113</span></td>
<td>fx-880BTG
</td></tr>
<tr>
<td><span class="cwcwd">EY-024</span></td>
<td>A</td>
<td><span class="cwcwd">6657</span></td>
<td>fx-82CN CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-025</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-350CN CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-026</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-95CN CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-027</span></td>
<td>A</td>
<td><span class="cwcwd">B5F6</span></td>
<td>fx-991CN CW
</td></tr>
<tr>
<td rowspan="2"><span class="cwcwd">EY-028</span></td>
<td>A</td>
<td><span class="cwcwd">AEF6</span></td>
<td rowspan="2">fx-999CN CW
</td></tr>
<tr>
<td>B</td>
<td><span class="cwcwd">D7BB</span>
</td></tr>
<tr>
<td><span class="cwcwd">EY-029</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-JP500CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-030</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-JP700CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-031</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-JP900CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-032</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-550AZ
</td></tr>
<tr>
<td><span class="cwcwd">EY-036</span></td>
<td>B</td>
<td><i>Unknown</i></td>
<td>fx-82LA CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-038</span></td>
<td colspan="2"><i>No known revisions</i></td>
<td>fx-570LA CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-039</span></td>
<td>C</td>
<td><i>Unknown</i></td>
<td>fx-991LA CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-040</span></td>
<td>A</td>
<td><span class="cwcwd">DA5C</span></td>
<td>fx-83GT CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-041</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-85GT CW
</td></tr>
<tr>
<td><span class="cwcwd">EY-044</span></td>
<td>A</td>
<td><span class="cwcwd">6366</span></td>
<td>fx-8200 AU
</td></tr>
<tr>
<td><span class="cwcwd">EY-047</span></td>
<td>A</td>
<td><i>Unknown</i></td>
<td>fx-810DE CW
</td></tr></tbody></table>
