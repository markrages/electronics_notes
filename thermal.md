# Design with power dissipation

## Why bother?

Energy is a useful abstraction to design with. The laws of
thermodynamics are expressed in energy, and power (energy/time) is
easily calculated for most electrical circuits and mechanical circuits.

A good knowledge of this stuff will help to immediately dismiss
impractical ideas about energy generation or driving motors from coin
cells.

## Electronic packages

All manufacturers have to work with the same laws of physics, and build their semiconductors out of the same materials, and the package sizes are standardized, so we can construct a table of specific thermal responses of different 3-terminal electronics devices.

| Package | θja | Source |
| SOT-23 | 417 °C/W | [ON MMTBT2222](https://www.onsemi.com/pub/Collateral/MMBT2222LT1-D.PDF) |
| TO-92 | 200 °C/W  | [ST LM317](http://www.st.com/content/ccc/resource/technical/document/datasheet/ee/4d/b2/bd/25/fe/44/2c/CD00000469.pdf/files/CD00000469.pdf/jcr:content/translations/en.CD00000469.pdf)
| TO-92 | 180 °C/W  | [ON LM317](http://www.onsemi.com/pub/Collateral/LM317L-D.PDF) |
| DPAK | 92 °C/W | [ON LM317](http://www.onsemi.com/pub/Collateral/LM317M-D.PDF) |
| TO-220, no heatsink | 80 °C/W  | [IR IRF510](http://www.qsl.net/n4xy/PDFs/Semiconductor_Data_Sheets/irf-510.pdf) |
| TO-220, no heatsink | 70 °C/W  | [ON LM317](http://www.onsemi.com/pub/Collateral/LM317M-D.PDF) |
| TO-220, no heatsink | 65 °C/W | [Fair LM7805](https://www.fairchildsemi.com/datasheets/LM/LM7805.pdf) |
| SOT-223 | 62 °C/W  | [TI LM340](http://www.ti.com/lit/ds/symlink/lm340.pdf) |
| SOIC-8 | 55 °C/W  | [ST LM317](http://www.st.com/content/ccc/resource/technical/document/datasheet/ee/4d/b2/bd/25/fe/44/2c/CD00000469.pdf/files/CD00000469.pdf/jcr:content/translations/en.CD00000469.pdf) |
| SOIC-8 | 45 °C/W  | [ON LM317](http://www.onsemi.com/pub/Collateral/LM317L-D.PDF) |
| TO-263 | 45 °C/W  | [TI LM340](http://www.ti.com/lit/ds/symlink/lm340.pdf) |
| TO-3, no heatsink | 39 °C/W  | [TI LM340](http://www.ti.com/lit/ds/symlink/lm340.pdf) |
| TO-220, no heatsink | 24 °C/W  | [TI LM340](http://www.ti.com/lit/ds/symlink/lm340.pdf) |
| TO-220, heatsink | 21 °C/W | [Fair LM7805](https://www.fairchildsemi.com/datasheets/LM/LM7805.pdf) |
| TO-220, heatsink | 18 °C/W | [Fair LM7805](https://www.fairchildsemi.com/datasheets/LM/LM7805.pdf) |
| TO-220, heatsink | 14.7 °C/W  | [TI LM340](http://www.ti.com/lit/ds/symlink/lm340.pdf) |
| TO-3, heatsink | 8.2 °C/W  | [TI LM340](http://www.ti.com/lit/ds/symlink/lm340.pdf) |

(TO220 heatsink: AAVID 577202B00000G 13 °C/W in still air, 6°C/W in moving air)
(TO3 heatsink: AAVID 500203B00000G 6.2 °C/W in still air)

## Example

Suppose I want to choose a linear regulator to take 12 V input and output 3.3 V. The product is for an office environment, and the maximum current supplied is 100 mA.

It is for an office environment, so let's say the maximum ambient temperature is 30 °C, and the maximum component temperature we'd like to see is 50 °C.

From the first specification, the power dissipated will be (12-3.3)*0.100, or 0.87 watts.

From the second specification, the maximum thermal response we can tolerate is 20 °C / 0.87 W, or 23 °C/W.

We can look at the chart above and know that a heatsinked TO-220 device will be appropriate. Now we can jump directly to choosing appropriate devices.  This is a much better approach than starting out by looking up Pdmax figures in the datasheets, or (worse) looking up maximum currents and voltages in the datasheets.
