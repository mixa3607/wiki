# Axiomtek IMB760
На самом деле речь не о ней напрямую, но о [Плата системная DPC627A, ДАЦН.469535.031](https://gisp.gov.ru/goods/#/product/3700848) что по факту и есть тот самый аксиомтек. Даже на заставке биоса написано `IMB760`.

![board](./image.png)

В общем и целом борда по железу ОК, без проблем тянет QWAT'ы на 270 ватт, но биос и бмц просто караул, шаром покати, даже выбьора частоты озу нет.

## Docs
- [Release info](./imb760.pdf)
- [IMB760 User's Manual VA1_06-02-2022.pdf](./IMB760%20User's%20Manual%20VA1_06-02-2022.pdf)

## Specs
- mosfets 7x MP86956 delivers 70A per socket ([source](https://forum.ixbt.com/topic.cgi?id=9:70249:141#141))
- all es 4-6 stepping cpus works
- bmc web ui - Megarac SP ([screenshot](image-1.png))
    - ver 2.02.76714
    - build date Aug 8 2022 14:45:58 CST
- only 24 pin + two cpu 8 pin is required

??? success "`$ biosdecode`"

    ```
    # biosdecode 3.5
    SMBIOS 3.3 present.
            Structure Table Length: 7692 bytes
            Structure Table Address: 0x000E6E00
            Number Of Structures: 97
            Maximum Structure Size: 184 bytes
    SMBIOS 3.3.0 present.
            Structure Table Maximum Length: 7692 bytes
            Structure Table 64-bit Address: 0x00000000000E6E00
    PNP BIOS 1.0 present.
            Event Notification: Not Supported
            Real Mode 16-bit Code Address: F000:BE16
            Real Mode 16-bit Data Address: F000:0000
            16-bit Protected Mode Code Address: 0x000FBE3E
            16-bit Protected Mode Data Address: 0x000F0000
    PCI Interrupt Routing 1.0 present.
            Router Device: 00:1f.0
            Exclusive IRQs: None
            Compatible Router: 8086:27b8
            Device: 00:01, on-board
            Device: 00:02, on-board
            Device: 00:11, on-board
            Device: 00:14, on-board
            Device: 00:16, on-board
            Device: 00:17, on-board
            Device: 01:00, slot 3
            Device: 00:1c, on-board
            Device: 02:00, on-board
            Device: 00:1d, on-board
            Device: 05:00, slot 238
            Device: 04:00, on-board
            Device: 06:00, on-board
            Device: 65:00, on-board
            Device: 64:02, on-board
            Device: 80:01, on-board
            Device: 00:00, on-board
            Device: e3:00, slot 238
            Device: e2:04, on-board
    ```

??? success "`$ dmidecode`"

    ```
    # dmidecode 3.5
    Getting SMBIOS data from sysfs.
    SMBIOS 3.3.0 present.
    Table at 0x000E6E00.

    Handle 0x0000, DMI type 0, 26 bytes
    BIOS Information
            Vendor: American Megatrends International, LLC.
            Version: IMB760 V1.00
            Release Date: 05/17/2022
            Address: 0xF0000
            Runtime Size: 64 kB
            ROM Size: 32 MB
            Characteristics:
                    PCI is supported
                    BIOS is upgradeable
                    BIOS shadowing is allowed
                    Boot from CD is supported
                    Selectable boot is supported
                    BIOS ROM is socketed
                    EDD is supported
                    Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
                    Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
                    5.25"/360 kB floppy services are supported (int 13h)
                    5.25"/1.2 MB floppy services are supported (int 13h)
                    3.5"/720 kB floppy services are supported (int 13h)
                    3.5"/2.88 MB floppy services are supported (int 13h)
                    Print screen service is supported (int 5h)
                    8042 keyboard services are supported (int 9h)
                    Serial services are supported (int 14h)
                    Printer services are supported (int 17h)
                    CGA/mono video services are supported (int 10h)
                    USB legacy is supported
                    BIOS boot specification is supported
                    Targeted content distribution is supported
                    UEFI is supported
            BIOS Revision: 5.21

    Handle 0x0001, DMI type 1, 27 bytes
    System Information
            Manufacturer: Intel Corporation
            Product Name: WHITLEY
            Version: 1.0
            Serial Number: Default string
            UUID: 6d5c8060-bfde-1000-0491-000000000000
            Wake-up Type: Power Switch
            SKU Number: Default string
            Family: Family

    Handle 0x0002, DMI type 2, 15 bytes
    Base Board Information
            Manufacturer: Intel Corporation
            Product Name: WHITLEY
            Version: Default string
            Serial Number: Default string
            Asset Tag: Base Board Asset Tag
            Features:
                    Board is a hosting board
                    Board is replaceable
            Location In Chassis: Part Component
            Chassis Handle: 0x0003
            Type: Motherboard
            Contained Object Handles: 0

    Handle 0x0003, DMI type 3, 22 bytes
    Chassis Information
            Manufacturer: Not Specified
            Type: Desktop
            Lock: Not Present
            Version: 0.1
            Serial Number: Default string
            Asset Tag: Chassis Asset Tag
            Boot-up State: Safe
            Power Supply State: Safe
            Thermal State: Safe
            Security Status: None
            OEM Information: 0x00000000
            Height: Unspecified
            Number Of Power Cords: 1
            Contained Elements: 0
            SKU Number: Default string

    Handle 0x0004, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J1A1
            Internal Connector Type: None
            External Reference Designator: PS2Mouse
            External Connector Type: PS/2
            Port Type: Mouse Port

    Handle 0x0005, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J1A1
            Internal Connector Type: None
            External Reference Designator: Keyboard
            External Connector Type: PS/2
            Port Type: Keyboard Port

    Handle 0x0006, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J2A1
            Internal Connector Type: None
            External Reference Designator: TV Out
            External Connector Type: Mini Centronics Type-14
            Port Type: Other

    Handle 0x0007, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J2A2A
            Internal Connector Type: None
            External Reference Designator: COM A
            External Connector Type: DB-9 male
            Port Type: Serial Port 16550A Compatible

    Handle 0x0008, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J2A2B
            Internal Connector Type: None
            External Reference Designator: Video
            External Connector Type: DB-15 female
            Port Type: Video Port

    Handle 0x0009, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J3A1
            Internal Connector Type: None
            External Reference Designator: USB1
            External Connector Type: Access Bus (USB)
            Port Type: USB

    Handle 0x000A, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J3A1
            Internal Connector Type: None
            External Reference Designator: USB2
            External Connector Type: Access Bus (USB)
            Port Type: USB

    Handle 0x000B, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J3A1
            Internal Connector Type: None
            External Reference Designator: USB3
            External Connector Type: Access Bus (USB)
            Port Type: USB

    Handle 0x000C, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J9A1 - TPM HDR
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x000D, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J9C1 - PCIE DOCKING CONN
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x000E, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J2B3 - CPU FAN
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x000F, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J6C2 - EXT HDMI
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x0010, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J3C1 - GMCH FAN
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x0011, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J1D1 - ITP
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x0012, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J9E2 - MDC INTPSR
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x0013, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J9E4 - MDC INTPSR
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x0014, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J9E3 - LPC HOT DOCKING
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x0015, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J9E1 - SCAN MATRIX
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x0016, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J9G1 - LPC SIDE BAND
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x0017, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J8F1 - UNIFIED
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x0018, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J6F1 - LVDS
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x0019, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J2F1 - LAI FAN
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x001A, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J2G1 - GFX VID
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x001B, DMI type 8, 9 bytes
    Port Connector Information
            Internal Reference Designator: J1G6 - AC JACK
            Internal Connector Type: Other
            External Reference Designator: Not Specified
            External Connector Type: None
            Port Type: Other

    Handle 0x001C, DMI type 9, 17 bytes
    System Slot Information
            Designation: Slot C
            Type: x4 PCI Express 3 x4
            Current Usage: In Use
            Length: Long
            ID: 3
            Characteristics:
                    3.3 V is provided
                    PME signal is supported
            Bus Address: 0000:00:1c.0

    Handle 0x001D, DMI type 9, 17 bytes
    System Slot Information
            Designation: Slot B
            Type: x16 PCI Express
            Current Usage: Unknown
            Length: Long
            ID: 1
            Characteristics:
                    3.3 V is provided
                    PME signal is supported
            Bus Address: 0000:4a:02.0

    Handle 0x001E, DMI type 9, 17 bytes
    System Slot Information
            Designation: Slot D
            Type: x16 PCI Express
            Current Usage: Unknown
            Length: Long
            ID: 2
            Characteristics:
                    3.3 V is provided
                    PME signal is supported
            Bus Address: 0000:97:02.0

    Handle 0x001F, DMI type 9, 17 bytes
    System Slot Information
            Designation: Slot 3
            Type: x16 PCI Express
            Current Usage: Unknown
            Length: Long
            ID: 3
            Characteristics:
                    3.3 V is provided
                    PME signal is supported
            Bus Address: 0000:30:02.0

    Handle 0x0020, DMI type 9, 17 bytes
    System Slot Information
            Designation: Slot 1
            Type: x16 PCI Express
            Current Usage: Unknown
            Length: Long
            ID: 4
            Characteristics:
                    3.3 V is provided
                    PME signal is supported
            Bus Address: 0000:16:02.0

    Handle 0x0021, DMI type 9, 17 bytes
    System Slot Information
            Designation: Slot 6
            Type: x16 PCI Express
            Current Usage: Unknown
            Length: Long
            ID: 5
            Characteristics:
                    3.3 V is provided
                    PME signal is supported
            Bus Address: 0000:b0:02.0

    Handle 0x0022, DMI type 9, 17 bytes
    System Slot Information
            Designation: Slot 4
            Type: x16 PCI Express
            Current Usage: Unknown
            Length: Long
            ID: 6
            Characteristics:
                    3.3 V is provided
                    PME signal is supported
            Bus Address: 0000:c9:02.0

    Handle 0x0023, DMI type 10, 6 bytes
    On Board Device Information
            Type: Video
            Status: Enabled
            Description:    To Be Filled By O.E.M.

    Handle 0x0024, DMI type 11, 5 bytes
    OEM Strings
            String 1: Default string

    Handle 0x0025, DMI type 12, 5 bytes
    System Configuration Options
            Option 1: Default string

    Handle 0x0026, DMI type 32, 20 bytes
    System Boot Information
            Status: No errors detected

    Handle 0x0027, DMI type 26, 22 bytes
    Voltage Probe
            Description: LM78A
            Location: Power Unit
            Status: OK
            Maximum Value: Unknown
            Minimum Value: Unknown
            Resolution: Unknown
            Tolerance: Unknown
            Accuracy: Unknown
            OEM-specific Information: 0x00000000
            Nominal Value: Unknown

    Handle 0x0028, DMI type 28, 22 bytes
    Temperature Probe
            Description: LM78A
            Location: Power Unit
            Status: OK
            Maximum Value: Unknown
            Minimum Value: Unknown
            Resolution: Unknown
            Tolerance: Unknown
            Accuracy: Unknown
            OEM-specific Information: 0x00000000
            Nominal Value: Unknown

    Handle 0x0029, DMI type 27, 15 bytes
    Cooling Device
            Temperature Probe Handle: 0x0028
            Type: Power Supply Fan
            Status: OK
            Cooling Unit Group: 1
            OEM-specific Information: 0x00000000
            Nominal Speed: Unknown Or Non-rotating
            Description: Cooling Dev 1

    Handle 0x002A, DMI type 29, 22 bytes
    Electrical Current Probe
            Description: ABC
            Location: Power Unit
            Status: OK
            Maximum Value: Unknown
            Minimum Value: Unknown
            Resolution: Unknown
            Tolerance: Unknown
            Accuracy: Unknown
            OEM-specific Information: 0x00000000
            Nominal Value: Unknown

    Handle 0x002B, DMI type 39, 22 bytes
    System Power Supply
            Power Unit Group: 1
            Location: To Be Filled By O.E.M.
            Name: To Be Filled By O.E.M.
            Manufacturer: To Be Filled By O.E.M.
            Serial Number: To Be Filled By O.E.M.
            Asset Tag: To Be Filled By O.E.M.
            Model Part Number: To Be Filled By O.E.M.
            Revision: To Be Filled By O.E.M.
            Max Power Capacity: Unknown
            Status: Present, OK
            Type: Switching
            Input Voltage Range Switching: Auto-switch
            Plugged: Yes
            Hot Replaceable: No
            Input Voltage Probe Handle: 0x0027
            Cooling Device Handle: 0x0029
            Input Current Probe Handle: 0x002A

    Handle 0x002C, DMI type 44, 9 bytes
    Unknown Type
            Header and Data:
                    2C 09 2C 00 FF FF 01 01 00

    Handle 0x002D, DMI type 38, 18 bytes
    IPMI Device Information
            Interface Type: KCS (Keyboard Control Style)
            Specification Version: 2.0
            I2C Slave Address: 0x10
            NV Storage Device: Not Present
            Base Address: 0x0000000000000CA2 (I/O)
            Register Spacing: Successive Byte Boundaries

    Handle 0x002E, DMI type 42, 17 bytes
    Management Controller Host Interface
            Host Interface Type: KCS: Keyboard Controller Style

    Handle 0x002F, DMI type 16, 23 bytes
    Physical Memory Array
            Location: System Board Or Motherboard
            Use: System Memory
            Error Correction Type: Single-bit ECC
            Maximum Capacity: 12 TB
            Error Information Handle: Not Provided
            Number Of Devices: 32

    Handle 0x0030, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_A1
            Bank Locator: NODE 0
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1616-4180660C
            Asset Tag: CPU0_DIMM_A1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x0031, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_A2
            Bank Locator: NODE 0
            Type: Unknown
            Type Detail: Unknown

    Handle 0x0032, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_B1
            Bank Locator: NODE 0
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1616-4180662F
            Asset Tag: CPU0_DIMM_B1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x0033, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_B2
            Bank Locator: NODE 0
            Type: Unknown
            Type Detail: Unknown

    Handle 0x0034, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_C1
            Bank Locator: NODE 1
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1549-2574A4F2
            Asset Tag: CPU0_DIMM_C1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x0035, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_C2
            Bank Locator: NODE 1
            Type: Unknown
            Type Detail: Unknown

    Handle 0x0036, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_D1
            Bank Locator: NODE 1
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1549-2574A5A8
            Asset Tag: CPU0_DIMM_D1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x0037, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_D2
            Bank Locator: NODE 1
            Type: Unknown
            Type Detail: Unknown

    Handle 0x0038, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_E1
            Bank Locator: NODE 2
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1536-24B3A042
            Asset Tag: CPU0_DIMM_E1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x0039, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_E2
            Bank Locator: NODE 2
            Type: Unknown
            Type Detail: Unknown

    Handle 0x003A, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_F1
            Bank Locator: NODE 2
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1536-24B3A042
            Asset Tag: CPU0_DIMM_F1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x003B, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_F2
            Bank Locator: NODE 2
            Type: Unknown
            Type Detail: Unknown

    Handle 0x003C, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_G1
            Bank Locator: NODE 3
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1536-24B3A042
            Asset Tag: CPU0_DIMM_G1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x003D, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_G2
            Bank Locator: NODE 3
            Type: Unknown
            Type Detail: Unknown

    Handle 0x003E, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_H1
            Bank Locator: NODE 3
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1536-24B3A042
            Asset Tag: CPU0_DIMM_H1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x003F, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU0_DIMM_H2
            Bank Locator: NODE 3
            Type: Unknown
            Type Detail: Unknown

    Handle 0x0040, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_A1
            Bank Locator: NODE 4
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1616-41806820
            Asset Tag: CPU1_DIMM_A1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x0041, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_A2
            Bank Locator: NODE 4
            Type: Unknown
            Type Detail: Unknown

    Handle 0x0042, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_B1
            Bank Locator: NODE 4
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1616-41806812
            Asset Tag: CPU1_DIMM_B1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x0043, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_B2
            Bank Locator: NODE 4
            Type: Unknown
            Type Detail: Unknown

    Handle 0x0044, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_C1
            Bank Locator: NODE 5
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1535-24B09F2B
            Asset Tag: CPU1_DIMM_C1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x0045, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_C2
            Bank Locator: NODE 5
            Type: Unknown
            Type Detail: Unknown

    Handle 0x0046, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_D1
            Bank Locator: NODE 5
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2133 MT/s
            Manufacturer: Hynix
            Serial Number: 1536-24B3A042
            Asset Tag: CPU1_DIMM_D1_AssetTag
            Part Number: HMA42GR7MFR4N-TF
            Rank: 2
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x0047, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_D2
            Bank Locator: NODE 5
            Type: Unknown
            Type Detail: Unknown

    Handle 0x0048, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_E1
            Bank Locator: NODE 6
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2666 MT/s
            Manufacturer: Hynix
            Serial Number: 1826-4295CC3B
            Asset Tag: CPU1_DIMM_E1_AssetTag
            Part Number: HMA82GR7JJR4N-VK
            Rank: 1
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x0049, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_E2
            Bank Locator: NODE 6
            Type: Unknown
            Type Detail: Unknown

    Handle 0x004A, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_F1
            Bank Locator: NODE 6
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2666 MT/s
            Manufacturer: Hynix
            Serial Number: 1826-4295CC52
            Asset Tag: CPU1_DIMM_F1_AssetTag
            Part Number: HMA82GR7JJR4N-VK
            Rank: 1
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x004B, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_F2
            Bank Locator: NODE 6
            Type: Unknown
            Type Detail: Unknown

    Handle 0x004C, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_G1
            Bank Locator: NODE 7
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2666 MT/s
            Manufacturer: Hynix
            Serial Number: 1826-4295CC38
            Asset Tag: CPU1_DIMM_G1_AssetTag
            Part Number: HMA82GR7JJR4N-VK
            Rank: 1
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x004D, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_G2
            Bank Locator: NODE 7
            Type: Unknown
            Type Detail: Unknown

    Handle 0x004E, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: 72 bits
            Data Width: 64 bits
            Size: 16 GB
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_H1
            Bank Locator: NODE 7
            Type: DDR4
            Type Detail: Synchronous Registered (Buffered)
            Speed: 2666 MT/s
            Manufacturer: Hynix
            Serial Number: 1826-4295CC40
            Asset Tag: CPU1_DIMM_H1_AssetTag
            Part Number: HMA82GR7JJR4N-VK
            Rank: 1
            Configured Memory Speed: 2133 MT/s
            Minimum Voltage: 1.2 V
            Maximum Voltage: 1.2 V
            Configured Voltage: 1.2 V
            Memory Technology: DRAM
            Memory Operating Mode Capability: Volatile memory
            Firmware Version: 0000
            Module Manufacturer ID: Bank 1, Hex 0xAD
            Module Product ID: Unknown
            Memory Subsystem Controller Manufacturer ID: Unknown
            Memory Subsystem Controller Product ID: Unknown
            Non-Volatile Size: None
            Volatile Size: 16 GB
            Cache Size: None
            Logical Size: None

    Handle 0x004F, DMI type 17, 92 bytes
    Memory Device
            Array Handle: 0x002F
            Error Information Handle: Not Provided
            Total Width: Unknown
            Data Width: Unknown
            Size: No Module Installed
            Form Factor: DIMM
            Set: None
            Locator: CPU1_DIMM_H2
            Bank Locator: NODE 7
            Type: Unknown
            Type Detail: Unknown

    Handle 0x0050, DMI type 19, 31 bytes
    Memory Array Mapped Address
            Starting Address: 0x00000000000
            Ending Address: 0x0007FFFFFFF
            Range Size: 2 GB
            Physical Array Handle: 0x002F
            Partition Width: 8

    Handle 0x0051, DMI type 19, 31 bytes
    Memory Array Mapped Address
            Starting Address: 0x00100000000
            Ending Address: 0x0207FFFFFFF
            Range Size: 126 GB
            Physical Array Handle: 0x002F
            Partition Width: 8

    Handle 0x0052, DMI type 19, 31 bytes
    Memory Array Mapped Address
            Starting Address: 0x02080000000
            Ending Address: 0x0407FFFFFFF
            Range Size: 128 GB
            Physical Array Handle: 0x002F
            Partition Width: 8

    Handle 0x0053, DMI type 133, 12 bytes
    OEM-specific Type
            Header and Data:
                    85 0C 53 00 00 D0 E6 6A 00 40 00 00

    Handle 0x0054, DMI type 7, 27 bytes
    Cache Information
            Socket Designation: L1-Cache
            Configuration: Enabled, Not Socketed, Level 1
            Operational Mode: Write Back
            Location: Internal
            Installed Size: 3040 kB
            Maximum Size: 3040 kB
            Supported SRAM Types:
                    Synchronous
            Installed SRAM Type: Synchronous
            Speed: Unknown
            Error Correction Type: Single-bit ECC
            System Type: Unified
            Associativity: 8-way Set-associative

    Handle 0x0055, DMI type 7, 27 bytes
    Cache Information
            Socket Designation: L2-Cache
            Configuration: Enabled, Not Socketed, Level 2
            Operational Mode: Varies With Memory Address
            Location: Internal
            Installed Size: 48640 kB
            Maximum Size: 48640 kB
            Supported SRAM Types:
                    Synchronous
            Installed SRAM Type: Synchronous
            Speed: Unknown
            Error Correction Type: Single-bit ECC
            System Type: Unified
            Associativity: 20-way Set-associative

    Handle 0x0056, DMI type 7, 27 bytes
    Cache Information
            Socket Designation: L3-Cache
            Configuration: Enabled, Not Socketed, Level 3
            Operational Mode: Varies With Memory Address
            Location: Internal
            Installed Size: 57 MB
            Maximum Size: 57 MB
            Supported SRAM Types:
                    Synchronous
            Installed SRAM Type: Synchronous
            Speed: Unknown
            Error Correction Type: Single-bit ECC
            System Type: Unified
            Associativity: 12-way Set-associative

    Handle 0x0057, DMI type 4, 48 bytes
    Processor Information
            Socket Designation: CPU0
            Type: Central Processor
            Family: Xeon
            Manufacturer: Intel(R) Corporation
            ID: A6 06 06 00 FF FB EB BF
            Signature: Type 0, Family 6, Model 106, Stepping 6
            Flags:
                    FPU (Floating-point unit on-chip)
                    VME (Virtual mode extension)
                    DE (Debugging extension)
                    PSE (Page size extension)
                    TSC (Time stamp counter)
                    MSR (Model specific registers)
                    PAE (Physical address extension)
                    MCE (Machine check exception)
                    CX8 (CMPXCHG8 instruction supported)
                    APIC (On-chip APIC hardware supported)
                    SEP (Fast system call)
                    MTRR (Memory type range registers)
                    PGE (Page global enable)
                    MCA (Machine check architecture)
                    CMOV (Conditional move instruction supported)
                    PAT (Page attribute table)
                    PSE-36 (36-bit page size extension)
                    CLFSH (CLFLUSH instruction supported)
                    DS (Debug store)
                    ACPI (ACPI supported)
                    MMX (MMX technology supported)
                    FXSR (FXSAVE and FXSTOR instructions supported)
                    SSE (Streaming SIMD extensions)
                    SSE2 (Streaming SIMD extensions 2)
                    SS (Self-snoop)
                    HTT (Multi-threading)
                    TM (Thermal monitor supported)
                    PBE (Pending break enabled)
            Version: Genuine Intel(R) CPU 0000%@
            Voltage: 1.6 V
            External Clock: 100 MHz
            Max Speed: 4000 MHz
            Current Speed: 2200 MHz
            Status: Populated, Enabled
            Upgrade: Socket LGA4189
            L1 Cache Handle: 0x0054
            L2 Cache Handle: 0x0055
            L3 Cache Handle: 0x0056
            Serial Number: Not Specified
            Asset Tag: UNKNOWN
            Part Number: Not Specified
            Core Count: 38
            Core Enabled: 38
            Thread Count: 76
            Characteristics:
                    64-bit capable
                    Multi-Core
                    Hardware Thread
                    Execute Protection
                    Enhanced Virtualization
                    Power/Performance Control

    Handle 0x0058, DMI type 7, 27 bytes
    Cache Information
            Socket Designation: L1-Cache
            Configuration: Enabled, Not Socketed, Level 1
            Operational Mode: Write Back
            Location: Internal
            Installed Size: 3040 kB
            Maximum Size: 3040 kB
            Supported SRAM Types:
                    Synchronous
            Installed SRAM Type: Synchronous
            Speed: Unknown
            Error Correction Type: Single-bit ECC
            System Type: Unified
            Associativity: 8-way Set-associative

    Handle 0x0059, DMI type 7, 27 bytes
    Cache Information
            Socket Designation: L2-Cache
            Configuration: Enabled, Not Socketed, Level 2
            Operational Mode: Varies With Memory Address
            Location: Internal
            Installed Size: 48640 kB
            Maximum Size: 48640 kB
            Supported SRAM Types:
                    Synchronous
            Installed SRAM Type: Synchronous
            Speed: Unknown
            Error Correction Type: Single-bit ECC
            System Type: Unified
            Associativity: 20-way Set-associative

    Handle 0x005A, DMI type 7, 27 bytes
    Cache Information
            Socket Designation: L3-Cache
            Configuration: Enabled, Not Socketed, Level 3
            Operational Mode: Varies With Memory Address
            Location: Internal
            Installed Size: 57 MB
            Maximum Size: 57 MB
            Supported SRAM Types:
                    Synchronous
            Installed SRAM Type: Synchronous
            Speed: Unknown
            Error Correction Type: Single-bit ECC
            System Type: Unified
            Associativity: 12-way Set-associative

    Handle 0x005B, DMI type 4, 48 bytes
    Processor Information
            Socket Designation: CPU1
            Type: Central Processor
            Family: Xeon
            Manufacturer: Intel(R) Corporation
            ID: A6 06 06 00 FF FB EB BF
            Signature: Type 0, Family 6, Model 106, Stepping 6
            Flags:
                    FPU (Floating-point unit on-chip)
                    VME (Virtual mode extension)
                    DE (Debugging extension)
                    PSE (Page size extension)
                    TSC (Time stamp counter)
                    MSR (Model specific registers)
                    PAE (Physical address extension)
                    MCE (Machine check exception)
                    CX8 (CMPXCHG8 instruction supported)
                    APIC (On-chip APIC hardware supported)
                    SEP (Fast system call)
                    MTRR (Memory type range registers)
                    PGE (Page global enable)
                    MCA (Machine check architecture)
                    CMOV (Conditional move instruction supported)
                    PAT (Page attribute table)
                    PSE-36 (36-bit page size extension)
                    CLFSH (CLFLUSH instruction supported)
                    DS (Debug store)
                    ACPI (ACPI supported)
                    MMX (MMX technology supported)
                    FXSR (FXSAVE and FXSTOR instructions supported)
                    SSE (Streaming SIMD extensions)
                    SSE2 (Streaming SIMD extensions 2)
                    SS (Self-snoop)
                    HTT (Multi-threading)
                    TM (Thermal monitor supported)
                    PBE (Pending break enabled)
            Version: Genuine Intel(R) CPU 0000%@
            Voltage: 1.6 V
            External Clock: 100 MHz
            Max Speed: 4000 MHz
            Current Speed: 2200 MHz
            Status: Populated, Enabled
            Upgrade: Socket LGA4189
            L1 Cache Handle: 0x0058
            L2 Cache Handle: 0x0059
            L3 Cache Handle: 0x005A
            Serial Number: Not Specified
            Asset Tag: UNKNOWN
            Part Number: Not Specified
            Core Count: 38
            Core Enabled: 38
            Thread Count: 76
            Characteristics:
                    64-bit capable
                    Multi-Core
                    Hardware Thread
                    Execute Protection
                    Enhanced Virtualization
                    Power/Performance Control

    Handle 0x0060, DMI type 13, 22 bytes
    BIOS Language Information
            Language Description Format: Long
            Installable Languages: 1
                    en|US|iso8859-1
            Currently Installed Language: en|US|iso8859-1

    Handle 0x0068, DMI type 41, 11 bytes
    Onboard Device
            Reference Designation: Onboard SATA Controller
            Type: SATA Controller
            Status: Enabled
            Type Instance: 1
            Bus Address: 0000:00:11.5

    Handle 0x0069, DMI type 41, 11 bytes
    Onboard Device
            Reference Designation: Onboard SATA Controller
            Type: SATA Controller
            Status: Enabled
            Type Instance: 2
            Bus Address: 0000:00:17.0

    Handle 0x006A, DMI type 41, 11 bytes
    Onboard Device
            Reference Designation: Onboard ETHERNET Controller
            Type: Ethernet
            Status: Enabled
            Type Instance: 1
            Bus Address: 0000:06:00.0

    Handle 0x006B, DMI type 127, 4 bytes
    End Of Table
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

## BMC / BIOS
Программно вытащить прошивки из флешек не удалось
