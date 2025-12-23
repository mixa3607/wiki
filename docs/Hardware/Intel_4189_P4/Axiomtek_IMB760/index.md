# Axiomtek IMB760
На самом деле речь не о ней напрямую, но о [Плата системная DPC627A, ДАЦН.469535.031](https://gisp.gov.ru/goods/#/product/3700848) что по факту и есть тот самый аксиомтек. Даже на заставке биоса написано `IMB760`.

![board](./image.png)

В общем и целом борда по железу ОК, без проблем тянет QWAT'ы на 270 ватт, но биос и бмц просто караул, шаром покати, даже выбора частоты озу нет (upd. см. мод биос).

## Docs
- [Release info](./imb760.pdf)
- [IMB760 User's Manual VA1_06-02-2022.pdf](./IMB760%20User's%20Manual%20VA1_06-02-2022.pdf)

## Specs
- mosfets 7x MP86956 delivers 70A per socket ([source](https://forum.ixbt.com/topic.cgi?id=9:70249:141#141))
- all es 4-6 stepping cpus works
- bmc web ui - Megarac SP ([screenshot](./bmc-screenshot.png))
    - ver 2.02.76714
    - build date Aug 8 2022 14:45:58 CST
- only 24 pin + two cpu 8 pin is required

??? success "`$ biosdecode`"

    ```
    --8<-- "docs/Hardware/Intel_4189_P4/Axiomtek_IMB760/biosdecode.txt"
    ```

??? success "`$ dmidecode`"

    ```
    --8<-- "docs/Hardware/Intel_4189_P4/Axiomtek_IMB760/dmidecode.txt"
    ```

## Проблемы и их решения (?)
- Q: Винтики для М2 больше стандартных?
    - A: Да, используются M3 (5mm+-)
- Q: Кажется или в BMC неверные данные по температурам?
    - A: Не кажется. Не смотрим на попугаи в BMC, но вольтаж и обороты вертушек там правильно показывает (с округлением до сотен)
- Q: Тесты подсистемы памяти в AIDA64 показывают какие то странные цифры
    - A: Бывает, используйте [intel mlc](../Tools/index.md#intel-mlc)
- Q: UEFI не видит csm boot devices?
    - A: Завести не удалось

## BMC / BIOS
Дампы снятые прищепкой:

| Type | Name | User | BIN      | Info |
| ---- | ---- | ---- | -------- | ---- |
| BIOS | mod A1 RC1 | mixa3607  | [github: mixa3607/ami-patching-infra](https://github.com/mixa3607/ami-patching-infra/releases)  | based on `stock-2`    |
| BIOS | stock-1    | mixa3607  | [AMIBCP log + dump](./bios/IMB760_BIOS_mixa3607_stock-1.tgz)                | many boots => dump    |
| BIOS | stock-2    | mixa3607  | [AMIBCP log + dump](./bios/IMB760_BIOS_mixa3607_stock-2.tgz)                | reset => save => dump |
| BIOS | stock-1    | EvILLIDAN | [AMIBCP log + dump](./bios/IMB760_BIOS_EvILLIDAN_stock-1.tgz)               |                       |
| BMC  | stock-1    | EvILLIDAN | [dump](./bmc/IMB760_BMC_EvILLIDAN_stock-1.tgz)                              |                       |

BIOS свободно открывается через AMIBCP ([tools](../../Tools/index.md#amibcp)) и UEFITool ([tools](../../Tools/index.md#uefitool))

### Подробнее про мод биос и прошивку
Программно вытащить прошивки из флешек не удалось. На данный момент не известно ни одной прошивки которая бы прошилась через бмц.

Микросхема памяти биоса рядом с мостом, память бмц рядом с ast2500. Что бы прочитать/зашить чипы достаточно прищепки и обесточить плату, выпаивать не нужно.

!!! danger "CH341"
    Им можно шить, но проверьте что он у вас либо с завода на 3,3в, либо что вы его переделали. Мануалы есть в интернете к примеру [https://wiki.chucknemeth.com/usb-devices/ch341a/3v-ch341a-mod](https://wiki.chucknemeth.com/usb-devices/ch341a/3v-ch341a-mod)

Пока есть много неизвестных моментов что работает, а что нет, вэлкам ту PR на [github: mixa3607/ami-patching-infra](https://github.com/mixa3607/ami-patching-infra?tab=readme-ov-file#%D1%81%D1%82%D0%B0%D1%82%D1%83%D1%81-%D0%BF%D0%BE-%D0%BC%D0%B5%D0%BD%D1%8E)

## Sensors
### All sensors
??? success "`$ sensors`"

    ```
    nct7802-i2c-0-2f
    Adapter: SMBus I801 adapter at 0780
    in0:           3.36 V  (min =  +0.00 V, max =  +4.09 V)
    in1:         664.00 mV
    FAN4:           0 RPM  (min =    0 RPM)
    FAN5:           0 RPM  (min =    0 RPM)
    FAN6:           0 RPM  (min =    0 RPM)
    temp1:        +30.1°C  (low  =  +0.0°C, high = +85.0°C)
                           (crit = +100.0°C)  sensor = thermistor
    temp2:        +36.0°C  (low  =  +0.0°C, high = +85.0°C)
                           (crit = +100.0°C)  sensor = thermistor
    temp3:        +36.1°C  (low  =  +0.0°C, high = +85.0°C)
                           (crit = +100.0°C)  sensor = thermistor
    temp4:        +30.0°C  (low  =  +0.0°C, high = +85.0°C)
                           (crit = +100.0°C)
    temp5:         +0.0°C  (low  =  +0.0°C, high = +85.0°C)
                           (crit = +100.0°C)

    power_meter-acpi-0
    Adapter: ACPI interface
    power1:           N/A  (interval = 4294967.29 s)

    f81768d-isa-0a20
    Adapter: ISA adapter
    in0:           1.65 V
    in1:           1.60 V  (max =  +2.04 V)
    in2:         984.00 mV
    in3:           2.04 V
    in4:           2.04 V
    in5:           0.00 V
    in6:           0.00 V
    in7:           1.65 V
    in8:           1.65 V
    in9:           1.66 V
    in10:          1.65 V
    FAN-CPU1:    1347 RPM
    FAN-CPU2:    1178 RPM
    temp1:        +31.0°C  (high = +85.0°C, hyst = +81.0°C)
                           (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
    temp2:        +32.0°C  (high = +85.0°C, hyst = +81.0°C)
                           (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
    temp3:          FAULT  (high = +70.0°C, hyst = +68.0°C)
                           (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor

    coretemp-isa-0000
    Adapter: ISA adapter
    Package id 0:  +32.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 0:        +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 1:        +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 2:        +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 3:        +27.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 4:        +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 5:        +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 6:        +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 7:        +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 8:        +32.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 9:        +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 10:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 11:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 12:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 13:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 14:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 15:       +32.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 16:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 17:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 18:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 19:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 20:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 21:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 22:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 23:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 24:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 25:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 26:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 27:       +32.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 28:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 29:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 30:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 31:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 32:       +32.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 33:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 34:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 35:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 36:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 37:       +30.0°C  (high = +97.0°C, crit = +107.0°C)

    nct7802-i2c-0-28
    Adapter: SMBus I801 adapter at 0780
    in0:           3.37 V  (min =  +0.00 V, max =  +4.09 V)
    in1:         680.00 mV
    FAN1:           0 RPM  (min =    0 RPM)
    FAN2:        1036 RPM  (min =    0 RPM)
    FAN3:           0 RPM  (min =    0 RPM)
    temp1:        +30.8°C  (low  =  +0.0°C, high = +85.0°C)
                           (crit = +100.0°C)  sensor = thermistor
    temp2:        +33.1°C  (low  =  +0.0°C, high = +85.0°C)
                           (crit = +100.0°C)  sensor = thermistor
    temp3:        +39.6°C  (low  =  +0.0°C, high = +85.0°C)
                           (crit = +100.0°C)  sensor = thermistor
    temp4:        +31.0°C  (low  =  +0.0°C, high = +85.0°C)
                           (crit = +100.0°C)
    temp5:         +0.0°C  (low  =  +0.0°C, high = +85.0°C)
                           (crit = +100.0°C)

    pch_lewisburg-virtual-0
    Adapter: Virtual device
    temp1:        +36.0°C

    coretemp-isa-0001
    Adapter: ISA adapter
    Package id 1:  +32.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 0:        +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 1:        +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 2:        +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 3:        +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 4:        +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 5:        +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 6:        +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 7:        +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 8:        +32.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 9:        +32.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 10:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 11:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 12:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 13:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 14:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 15:       +32.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 16:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 17:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 18:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 19:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 20:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 21:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 22:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 23:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 24:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 25:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 26:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 27:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 28:       +28.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 29:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 30:       +31.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 31:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 32:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 33:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 34:       +30.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 35:       +28.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 36:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    Core 37:       +29.0°C  (high = +97.0°C, crit = +107.0°C)
    ```

### Sesors matching
```console
$ cat /etc/sensors.d/imb760.conf
bus "i2c-0" "SMBus I801 adapter at 0780"

chip "nct7802-i2c-0-28"
label fan1 "FAN1"
label fan2 "FAN2"
label fan3 "FAN3"

chip "nct7802-i2c-0-2f"
label fan1 "FAN4"
label fan2 "FAN5"
label fan3 "FAN6"

chip "f81768d-isa-0a20"
label fan1 "FAN-CPU1"
label fan2 "FAN-CPU2"
ignore fan3
```


## Manual fan control
Способа крутить обороты из BMC найдено не было, все стандартные и не очень `impi raw` команды не проходят
### Cpu fans
Если я правильно понимаю то настроить поведение вертушек на цпу можно только через меню в биосе (см. маунал)

### Sys fans
Системные вертушки можно легко крутить из системы. Всё достаточно стандартно

```console
$ echo 1  | sudo tee /sys/class/hwmon/hwmon7/pwm2_enable  #enable FAN2 manual mode
$ echo 50 | sudo tee /sys/class/hwmon/hwmon7/pwm2         #set FAN2 to 50 (allowed 0-255)
```

### Change BMC fan thresholds

```console
$ sudo ipmitool sensor thresh FAN1 lower  0 0 0 
Locating sensor record 'FAN1'...
Setting sensor "FAN1" Lower Non-Recoverable threshold to 0.000
Setting sensor "FAN1" Lower Critical threshold to 0.000
Setting sensor "FAN1" Lower Non-Critical threshold to 0.000

$ # run prev command for all FANx
$ sudo ipmitool sensor list all
+12V             | 12.100     | Volts      | ok    | 9.600     | 10.200    | 10.800    | 13.200    | 13.800    | 14.400
+5V              | 4.928      | Volts      | ok    | 4.510     | 4.620     | 4.752     | 5.258     | 5.368     | 5.500
+3.3V            | 3.300      | Volts      | ok    | 2.978     | 3.051     | 3.139     | 3.460     | 3.548     | 3.635
+5VSB            | 4.906      | Volts      | ok    | 4.510     | 4.620     | 4.752     | 5.258     | 5.368     | 5.500
+3VSB            | 3.285      | Volts      | ok    | 2.978     | 3.051     | 3.139     | 3.460     | 3.548     | 3.635
SYS1_TEMP        | 31.000     | degrees C  | ok    | -40.000   | -30.000   | -20.000   | 70.000    | 90.000    | 100.000
CPU1_TEMP        | 37.000     | degrees C  | ok    | -40.000   | -30.000   | -20.000   | 100.000   | 110.000   | 120.000
SYS2/CPU2_TEMP   | 37.000     | degrees C  | ok    | -40.000   | -30.000   | -20.000   | 100.000   | 110.000   | 120.000
FAN1             | 1200.000   | RPM        | ok    | 0.000     | 0.000     | 0.000     | 31000.000 | 32000.000 | 33000.000
FAN2             | 1000.000   | RPM        | ok    | 0.000     | 0.000     | 0.000     | 31000.000 | 32000.000 | 33000.000
FAN3             | 0.000      | RPM        | nr    | 0.000     | 0.000     | 0.000     | 31000.000 | 32000.000 | 33000.000
FAN4             | 1000.000   | RPM        | ok    | 0.000     | 0.000     | 0.000     | 31000.000 | 32000.000 | 33000.000
FAN5             | 0.000      | RPM        | nr    | 0.000     | 0.000     | 0.000     | 31000.000 | 32000.000 | 33000.000
FAN6             | 0.000      | RPM        | nr    | 0.000     | 0.000     | 0.000     | 31000.000 | 32000.000 | 33000.000
FAN7             | 0.000      | RPM        | nr    | 0.000     | 0.000     | 0.000     | 31000.000 | 32000.000 | 33000.000
FAN8             | 0.000      | RPM        | nr    | 0.000     | 0.000     | 0.000     | 31000.000 | 32000.000 | 33000.000
```

Как заставить материнку считать 0 оборотов нормой не нашёл, они всегда вываливаются в `non rec` mode
