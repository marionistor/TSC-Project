# OpenBook

OpenBook este un cititor electronic open-source, construit pentru consum mic de energie și versatilitate. Folosește microcontrollerul ESP32-C6-WROOM-1-N8, un ecran e-paper, senzori ambientali, ceas în timp real și stocare extinsă, alimentate de o baterie reîncărcabilă.

## Bill of Materials

| Componentă | Descriere | Link Achiziție | Documentație |
|------------|-----------|----------------|--------------|
| ESP32-C6-WROOM-1-N8 | Microcontroler cu Wi-Fi 6, BLE 5.0 | [Mouser](https://ro.mouser.com/ProductDetail/Espressif-Systems/ESP32-C6-WROOM-1-N8) | [Datasheet](https://www.espressif.com/sites/default/files/documentation/esp32-c6-wroom-1_wroom-1u_datasheet_en.pdf) |
| BME680 | Senzor temperatură, umiditate, presiune, VOC | [Mouser](https://ro.mouser.com/ProductDetail/Bosch-Sensortec/BME680) | [Datasheet](https://www.bosch-sensortec.com/media/boschsensortec/downloads/datasheets/bst-bme680-ds001.pdf) |
| DS3231SN | Ceas în timp real | [Mouser](https://ro.mouser.com/ProductDetail/Analog-Devices/DS3231SN) | [Datasheet](https://www.analog.com/media/en/technical-documentation/data-sheets/DS3231.pdf) |
| W25Q512JVEIQ | Memorie Flash 64MB | [Mouser](https://ro.mouser.com/ProductDetail/Winbond/W25Q512JVEIQ) | [Datasheet](https://www.winbond.com/resource-files/W25Q512JV%20SPI%20RevB%2006252019%20KMS.pdf) |
| MicroSD Slot (112A-TAAR-R03) | Slot card microSD | [Mouser](https://ro.mouser.com/ProductDetail/Attend/112A-TAAR-R03) | [Datasheet](https://www.attend.com.tw/data/download/file/112A-TAAR-R03_Spec.pdf) |
| MCP73831T-5ACI/OT | Încărcător baterie | [Mouser](https://ro.mouser.com/ProductDetail/Microchip-Technology/MCP73831T-5ACI-OT) | [Datasheet](https://ww1.microchip.com/downloads/en/DeviceDoc/MCP73831-Family-Data-Sheet-DS20001984H.pdf) |
| MAX17048G+T10 | Indicator nivel baterie | [Mouser](https://ro.mouser.com/ProductDetail/Analog-Devices/MAX17048G%2BT10) | [Datasheet](https://www.analog.com/media/en/technical-documentation/data-sheets/MAX17048-MAX17049.pdf) |
| XC6220A331MR-G | Regulator 3.3V | [Mouser](https://ro.mouser.com/ProductDetail/Torex-Semiconductor/XC6220A331MR-G) | [Datasheet](https://www.torexsemi.com/file/xc6220/XC6220.pdf) |
| USB4110-GF-A | Conector USB-C | [Mouser](https://ro.mouser.com/ProductDetail/GCT/USB4110-GF-A) | [Datasheet](https://gct.co/files/drawings/usb4110.pdf) |
| CPH3225A | Supercondensator pentru ceas | [Mouser](https://ro.mouser.com/ProductDetail/Seiko-Instruments/CPH3225A) | [Datasheet](https://mm.digikey.com/Volume0/opasdata/d220001/medias/docus/6537/rev05-CPHCPM.pdf) |
| DMG2305UX-7 | MOSFET P-Channel | [Mouser](https://ro.mouser.com/ProductDetail/Diodes-Incorporated/DMG2305UX-7) | [Datasheet](https://www.diodes.com/assets/Datasheets/DMG2305UX.pdf) |
| SI1308EDL-T1-GE3 | MOSFET N-Channel | [Mouser](https://ro.mouser.com/ProductDetail/Vishay-Siliconix/SI1308EDL-T1-GE3) | [Datasheet](https://www.vishay.com/docs/63399/si1308edl.pdf) |
| USBLC6-2SC6Y | Protecție ESD USB | [Mouser](https://ro.mouser.com/ProductDetail/STMicroelectronics/USBLC6-2SC6Y) | [Datasheet](https://www.st.com/resource/en/datasheet/usblc6-2.pdf) |
| PGB1010603MR | Protecție ESD | [Mouser](https://ro.mouser.com/ProductDetail/Littelfuse/PGB1010603MR) | [Datasheet](https://www.littelfuse.com/~/media/electronics/datasheets/esd_protection/littelfuse_pulseguard_esd_pgb1_series_datasheet.pdf) |
| BD5229G-TR | Detector tensiune | [Mouser](https://ro.mouser.com/ProductDetail/ROHM-Semiconductor/BD5229G-TR) | [Datasheet](https://fscdn.rohm.com/en/products/databook/datasheet/ic/power/voltage_detector/bd52xxg-e.pdf) |
| FH34SRJ-24S-0.5SH(99) | Conector FFC/FPC e-paper | [Mouser](https://ro.mouser.com/ProductDetail/Hirose-Connector/FH34SRJ-24S-0.5SH99) | [Datasheet](https://www.hirose.com/product/document?clcode=&productname=&series=FH34SRJ&documenttype=Catalog&lang=en) |
| 744043680 | Inductor | [Mouser](https://ro.mouser.com/ProductDetail/Wurth-Elektronik/744043680) | [Datasheet](https://www.we-online.com/components/products/datasheet/744043680.pdf) |
| EVQPUJ02K | Buton tactil | [Mouser](https://ro.mouser.com/ProductDetail/Panasonic/EVQPUJ02K) | [Datasheet](https://www.lcsc.com/datasheet/lcsc_datasheet_2201121800_PANASONIC-EVQPUJ02K_C2936858.pdf) |
| KP-1608SURCK | LED indicator | [Mouser](https://ro.mouser.com/ProductDetail/Kingbright/KP-1608SURCK) | [Datasheet](https://media.elv.com/file/107153_led_surck1608_data.pdf) |

## Funcționalitate Hardware

### 1. Microcontroler ESP32-C6-WROOM-1-N8
* Rol: Gestionează toate funcțiile, de la afișaj la conectivitate wireless
* Specificații: Procesor 32-bit, 160 MHz, 512 KB SRAM, Wi-Fi 6, Bluetooth 5.0
* Conexiuni:
  * SPI: Conectează ecranul, memoria Flash și cardul SD
  * I²C: Interfațează senzorul, ceasul și indicatorul de baterie
  * GPIO: Controlează butoanele și alte funcții
  * UART: Utilizat pentru depanare
* Consum: 3.3V, sub 10 µA în mod repaus

### 2. Ecran E-Paper
* Tip: 7.5 inci, rezoluție 800x480 pixeli
* Conexiune: SPI, cu linii pentru date, control și stare
* Consum: 20-50 mA la reîmprospătare, aproape zero în mod static
* Rol: Afișează text clar, ideal pentru lectură prelungită

### 3. Stocare
* Memorie Flash (W25Q512JVEIQ):
  * Capacitate: 64 MB, conectată prin SPI
  * Scop: Stochează firmware și cărți
  * Consum: 10-20 mA
* Slot MicroSD:
  * Conexiune: SPI, pentru stocare suplimentară
  * Consum: 30-100 mA la citire/scriere

### 4. Ceas în Timp Real (DS3231SN)
* Conexiune: I2C, partajat cu alte module
* Consum: Sub 1 µA cu supercondensator
* Rol: Menține ora exactă pentru loguri sau programări

### 5. Senzor Ambiental (BME680)
* Măsurători: Temperatură, umiditate, presiune, compuși volatili
* Conexiune: I2C, viteză de 400 kHz
* Consum: 0.8-3.6 mA în funcționare, sub 1 µA în repaus
* Rol: Monitorizează mediul pentru ajustări sau date

### 6. Alimentare
* Baterie: Li-Po, 2500 mAh, 3.7V
* Încărcare: MCP73831, maxim 1A prin USB-C
* Monitorizare: MAX17048, consum ~50 µA
* Regulator: 3.3V stabil
* Protecție: Împotriva descărcărilor electrostatice și polarității greșite

### 7. Interfață Utilizator
* Butoane: Trei tactile pentru navigare
* LED: Indică starea dispozitivului

### 8. Extensii
* Conector Qwiic: Pentru senzori I2C suplimentari
* Pini GPIO: Pentru conectarea altor module

## Pini ESP32-C6

| Pin    | Semnal       | Funcție                          | Motiv                                  |
|--------|--------------|----------------------------------|----------------------------------------|
| EN     | RESET        | Resetare sistem                  | Pin standard pentru resetare           |
| IO0    | INT_RTC      | Întrerupere RTC                  | Capacitate de întrerupere low-power    |
| IO1    | 32KHZ        | Ieșire ceas RTC 32 kHz           | Asigură cronometrare precisă           |
| IO2    | MISO         | Intrare date SPI                 | Comun pentru magistrala SPI            |
| IO3    | EPD_BUSY     | Stare ocupat e-paper             | Verifică disponibilitatea afișajului   |
| IO4    | SS_SD        | Selectare card SD                | CS dedicat pentru card SD              |
| IO5    | EPD_DC       | Date/comenzi e-paper             | Distinge datele de comenzi             |
| IO6    | SCK          | Ceas SPI                         | Semnal comun de ceas pentru SPI        |
| IO7    | MOSI         | Ieșire date SPI                  | Comun pentru periferice SPI            |
| IO9    | IO/BOOT      | Buton pornire                    | Inițiază modul boot sau pornire        |
| IO10   | EPD_CS       | Selectare e-paper                | CS dedicat pentru afișaj               |
| IO11   | FLASH_CS     | Selectare Flash                  | CS dedicat pentru memoria Flash        |
| IO12   | USB_D-       | Date diferențiale USB -          | Pin fix pentru USB                     |
| IO13   | USB_D+       | Date diferențiale USB +          | Pin fix pentru USB                     |
| IO15   | IO/CHANGE    | Buton schimbare pagină           | Intrare utilizator pentru navigare     |
| IO18   | RTC_RST      | Resetare RTC                     | Resetare hardware pentru ceas          |
| IO21   | SDA          | Linie date I²C                   | Comun pentru senzori și RTC            |
| IO22   | SCL          | Linie ceas I²C                   | Semnal comun de ceas I²C               |
| IO23   | EPD_RST      | Resetare e-paper                 | Resetare hardware pentru afișaj        |
| TXD0   | TX           | Transmitere UART (depanare)      | Punct test pentru depanare             |
| RXD0   | RX           | Recepție UART (depanare)         | Punct test pentru depanare             |

## Decizii de Proiectare

* Alimentare stabilă: Liniile de putere au fost trasate cu prioritate pentru a garanta o funcționare fiabilă, restul semnalelor fiind optimizate automat.
* Conector USB-C: Configurat special pentru a elimina conflictele de design, permițând atât alimentare, cât și transfer de date.
* Afișaj e-paper: Ales pentru consum energetic minim și claritate, alimentat printr-un circuit dedicat cu tranzistor pentru eficiență.
* Extensibilitate: Include un port Qwiic și pini accesibili pentru viitoare modificări sau depanare ușoară.
* Protecție electrică: Adăugate circuite de siguranță pentru liniile de date și alimentare, asigurând rezistența dispozitivului.
