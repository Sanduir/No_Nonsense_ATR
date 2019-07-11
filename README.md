# No_Nonsense_ATR
## Overview

No Nonsense ATR is a tool designed to help the [NNFX Traders](https://nononsenseforex.com/) backtest strategies and trading in real time.

The indicator calculates the value of the SL/TP based on the [ATR](https://nononsenseforex.com/indicators/the-worlds-best-forex-indicator/) allowing to verify the historical data in a simple and practical way, showing not only the SL/TP values but also the place where they would be and if it was a gain or loss. 
The No Nonsense ATR also calculates the trading volume required for each trade according to the desired risk, the SL and using the account currency for the calculation thus giving a more accurate value.


 ![overview](./Images/overview.gif)

## Installation:
The No Nonsense ATR installation is exactly like any other indicator.
* In MT4 select "File" -> "Open Data Folder"
* Open the "MQL4" folder and then the "Indicators" folder
* Download the indicator by clicking "Clone or Download" and then "Download Zip"
* Copy the No_Nonsense_ATR.ex4 file to the "Indicators" folder
* Restart the MT4 or click Refresh in Navigator window
* Search for "No_Nonsense_ATR" in the Navigator window and double-click it
* Done!

 ![inicial](./Images/painel_inicial.png)
 
## How to Use:
The No Nonsense ATR offers several inputs in order to adapt to the trader's presonality.

 ![inputs](./Images/painel_inputs.png)

### Fillted ATR:
Fillted ATR mode allows you to filter out extreme events that affect the ATR value, such as the flash crash of January 3, 2019. Extreme events are detected if the candle size is greater than the "STANDARD DEVIATION MULTIPLIER" * [Standard deviation](https://en.wikipedia.org/wiki/Standard_deviation) (sigma σ) + the average ATR.
The average ATR is calculated for the number of candles placed in the input "SAMPLE SIZE".
If an extreme event is detected the candle size value is replaced by the average ATR on that candle thus creating the filtered ATR.

### Live Mode:
The Live Mode is designed to make it easier to use the indicator when trading in real time.
In this mode, the values of SL/TP and trading volume are always fixed to the most recent value.
This mode can be activated in two ways: by clicking on the area without candles in the right part of the graph (another clicks to disable the live mode) or changing the input "LIVE MODE" to true.

### Trading Volume:
The No Nonsense ATR can be configured to show the trading volume by activating the input "TRADING_VOLUME".
This feature is especially for real-time trading and not for backtest with or without simulators because for the trading volume calculation uses the current account balance and does not check the past balance or the balance of the simulator accounts.

It is possible to select the currency of the account making the calculation of trading volume more precise. If you select "COUNTER CURRENCY" then the calculation is made with the account basse currency equal to the counter currency of the pair you are trading.
If you select one of the currencies you have to enter the suffix and/or the prefix of the other forex symbols in the "CUREENCY_SUFFIX" and "CUREENCY_PREFIX" respectively. For example: if the names of the forex pairs are "GBPUSDpro", "EURUSDpro" Put the word "pro" in the input "CUREENCY_SUFFIX".

### Simulators:
The No Nonsense ATR has been tested on the Soft4FX and FXBlue simulators and can be used together with the No Nonsense ATR without any problem. However, if the simulators stop at the opening of the candle and the result of the SL/TP and Trading volume will include the value of the candle newly opened for the calculation of the ATR. To display the values of the SL/TP and the Trading volume of the previous candle on the most recent candle just put the value 1 in the "SHIFT" input.

### iCustom:
The No Nonsense ATR offers 3 buffers. The NNFX_SL (SL), the NNFX_TP (TP), and the NNFX_TRADING_VOL (trading volume), which can be read externally through the function [iCustom](https://docs.mql4.com/indicators/icustom).

**Attention**: The buffer NNFX_TRADING_VOL can only be read in candle 0 (shift=0) when the input "TRADING_VOLUME"=true

 ![buffers](./Images/painel_buffers.png)

**Examples**

Save the SL value of the previous candle in the variable SL
```c++
double SL=iCustom(NULL,0,"No Nonsense ATR ",14,1.0,14,1.5,0,0,"==========================",False,3.0,200,"==========================",false,0,14,Gold,Gold,false,Black,"==========================",false,false,false,false,false,0,DeepSkyBlue,0,Red,"==========================",false,1,0,"","","==========================",false,0,0,1);
```
 Save the Filter TP value of the current candle in the variable TP
```c++
double TP=iCustom(NULL,0,"No Nonsense ATR ",14,1.0,14,1.5,0,0,"==========================",True,3.0,200,"==========================",false,0,14,Gold,Gold,false,Black,"==========================",false,false,false,false,false,0,DeepSkyBlue,0,Red,"==========================",false,1,0,"","","==========================",false,0,1,0);
```
 Save the trading volume value (account currency = EUR and Risk = 3%) in the variable VOL
```c++
double VOL=iCustom(NULL,0,"No Nonsense ATR ",14,1.0,14,1.5,0,0,"==========================",False,3.0,200,"==========================",false,0,14,Gold,Gold,false,Black,"==========================",false,false,false,false,false,0,DeepSkyBlue,0,Red,"==========================",true,3,2,"","","==========================",false,0,2,0);
```

## Copyright and License
No Nonsense ATR is open source software: you can redistribute it and/or modify it under the terms of the 
GNU General Public License v3.0

No Nonsense ATR was made available in the hope that it will be useful for traders, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the ![GNU General Public License v3.0](./LICENSE) for more details.

ICON Used: Target market Icon 

Artist: [GraphicLoads](http://graphicloads.com) - Iconset: [Flat Finance Icons (50 icons)](http://www.iconarchive.com/show/flat-finance-icons-by-graphicloads.html) - License: Freeware - Commercial usage: Allowed

## Contributors

Please feel free to comment, report issues, or contribute!

Contact me by email: ruisilva.real@sapo.pt or in the [No Nonsense FOREX Discord](https://discordapp.com/invite/5TEY6h6)

Consider donating through [PAYPAL](https://paypal.me/rpsreal). Thank you!


Thanks to the [No Nonsense FOREX Discord](https://discordapp.com/invite/5TEY6h6) community for the suggestions to improve the No Nonsense ATR.

Thank you VP for everything. Check the No Nonsense Forex strategy at: https://nononsenseforex.com/

Developed by Rui Silva, Porto, Portugal
