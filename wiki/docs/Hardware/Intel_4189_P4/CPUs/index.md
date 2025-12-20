# CPUs ES/QS

## Table
{{ read_excel('./4189_ES.xlsx', keep_default_na=False) }}

[raw xlsx](./4189_ES.xlsx)

## QWAT
```
Sample name: QWAT
Release name: 8368
Average price: 900-1200Y
```

??? success "`$ lscpu`"

    ```
    --8<-- "docs/Hardware/Intel_4189_P4/CPUs/QWAT/lscpu.txt"
    ```

??? success "`$ dmidecode`"

    ```
    --8<-- "docs/Hardware/Intel_4189_P4/CPUs/QWAT/dmidecode.txt"
    ```

??? success "`max/min freqs`"

    ```
    --8<-- "docs/Hardware/Intel_4189_P4/CPUs/QWAT/freqs-test.txt"
    ```


## Template
```
Sample name: <code name>
Release name: <release model name>
Average price: <avg price>
```

??? success "`$ lscpu`"

    ```
    lscpu > lscpu.txt
    --8<-- "docs/Hardware/Intel_4189_P4/CPUs/<code name>/lscpu.txt"
    ```

??? success "`$ dmidecode`"

    ```
    lscpu > dmidecode.txt
    --8<-- "docs/Hardware/Intel_4189_P4/CPUs/<code name>/dmidecode.txt"
    ```

??? success "`max/min freqs`"

    ```
     echo "MAX freq" >> freqs-test.txt
     echo 5000000 | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_min_freq
     sleep 1s
     cat /proc/cpuinfo | grep "MHz" | sed -E 's|.* ([0-9]+)\..*|\1|1' | sort -hr | uniq -c >> freqs-test.txt

     echo "MIN freq" >> freqs-test.txt
     echo 1 | sudo tee /sys/devices/system/cpu/cpu*/cpufreq/scaling_min_freq
     sleep 1s
     cat /proc/cpuinfo | grep "MHz" | sed -E 's|.* ([0-9]+)\..*|\1|1' | sort -hr | uniq -c >> freqs-test.txt
    
    --8<-- "docs/Hardware/Intel_4189_P4/CPUs/<code name>/freqs-test.txt"
    ```

