---
title: How to identify fake calculators
layout: default
---

# How to identify fake calculators
{: .no_toc }
From Calcupedia, the free calculator encyclopedia
{: .fs-2 }

{: .warning-title }
> This page focuses on Casio calculators.
>
> If you are not using Casio calculators, this is *not* the page for you.

Nowadays, it is very easy to find fake [Casio](https://wikipedia.org/wiki/Casio) calculators on online shopping sites. Because of this, here are some methods to check if your Casio calculator is a legitimate one.

<details open markdown="block">
<summary>
    Contents
  </summary>
  {: .text-delta }
1. TOC
{:toc}
</details>

## Clones and fakes
In this wiki, calculator clones and fake calculators are **not** the same:
- **Calculator clones** are calculators that copy Casio's scientific calculators, but with some things (or nothing) changed, removed and/or added, and actually markets itself as a calculator from a third-party. Examples include Vinacal (Vietnam), Deli (China), Gasid, etc.
- **Fake calculators** are calculators that try to 100% mimic Casio's scientific calculators, and tries to market itself as a genuine Casio calculator.

## Appearance method
Fake calculators are often of poor quality, and many fakes can be spotted just by observing it. For example:
- The characters on the keyboard are printed skewed, and the font is incorrect;
- The calculator is made of poor material, is easily damaged, or is uncomfortable to the touch;
- The color of the display screen is wrong or the font of the indicator light on the top line is wrong, which makes it uncomfortable to watch;
- The installation position of the display screen is incorrect or the screen is not stable;
- The calculator smells strongly of plastic, or other odors, etc.

These are the characteristics of some fakes, but not all fakes have these characteristics. Therefore, unless it is a professional who often identifies fakes, it is difficult for ordinary consumers to distinguish the genuine from the fakes at first glance.

## Anti-counterfeit labels
At the beginning, anti-counterfeit labels were the key to distinguishing the genuine from the fakes. They usually change color when looked at from different angles.

Bitex (page not archived yet) has their own anti-counterfeit labels that have more features that can assist in identifying a fake Casio calculator. They have the infamous quote "*Máy tính Casio không dán tem hoặc dán các loại tem khác thì không đảm bảo là hàng thật*" (Casio calculators that do not have labels or have other types of labels are not guaranteed to be genuine).

Unfortunately, this comes with some drawbacks:
- Anti-counterfeit labels of many calculators have fallen off after long-term wear and tear and cannot be identified;
- Some fake also have fake anti-counterfeit labels, and ordinary people cannot tell the authenticity at a glance.

## "4 presses, 1 release" method
**NOTE:** This method only works on the Casio ES series and up (includes the ES, ES PLUS, EX and CW series).

This method is **very accurate**.

1. Make sure you are on the <span class="esps">COMP</span>/Calculate mode, and that no characters are typed on the screen.
2. Hold <span class="k_es">1</span>. <span class="espl">1</span> should show up on the screen.
3. Now hold down the <span class="k_es">0</span>, <span class="k_es">p</span> and <span class="k_es">=</span> keys, while still holding down <span class="k_es">1</span>.
4. Release <span class="k_es">1</span>. If <span class="espl">cos(</span> shows up next to <span class="espl">1</span>, the calculator **must** be genuine.

On the CW series, when releasing <span class="k_cw">1</span>, <span class="cwcwd">²</span> shows up instead of <span class="cwcwd">cos(</span>.

## Precision method
1. Make sure you are on the <span class="esps">COMP</span>/Calculate mode, and that the angle unit is set to degrees.
2. Evaluate the expression <span class="espl">sin⁻(cos⁻(tan⁻(tan(cos(sin(9</span>.
3. Check the result of the expression:<br>
- The MS series and below will display `8.999998637`.
- The ES, ES PLUS and EX series will display <span class="espl">9.000000007</span>.
- The CW series will display <span class="cwcwd">9</span>.
- If the result does not match, it must be a fake.
4. Now:
- On an original MS, subtract 8.99999 from the result. The result should be `8.63704e-06`.
- On all calculators after MS (including revised MS and MS 2nd edition), subtract 9 from the result. The result should be <span class="espl">7.33338⁹</span>.
  - On CW models, the result will be <span class="cwcwd">7.5528¹⁸</span>.

## Battery law
Normally, Casio calculators use either [AA](https://wikipedia.org/wiki/AA_battery), [AAA](https://wikipedia.org/wiki/AAA_battery), or [LR44](https://wikipedia.org/wiki/LR44) batteries. One battery of one of these types has 1.5 [volts](https://wikipedia.org/wiki/Volt).

Check the battery and voltage that the calculator uses in the power specification (usually found on the back of the calculator). Open it up, and if the battery and/or voltage does not match the specification (for example, a 3-volt battery is used, i.e. a [CR2025](https://wikipedia.org/wiki/CR2025) battery), it must be a fake.

## The DIAGNOSTIC/self-test mode
See [Calculator self-test](/calcupedia_backup/docs/diagnostic.html#casio-calculators).
