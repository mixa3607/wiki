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
    Architecture:             x86_64
      CPU op-mode(s):         32-bit, 64-bit
      Address sizes:          46 bits physical, 57 bits virtual
      Byte Order:             Little Endian
    CPU(s):                   152
      On-line CPU(s) list:    0-151
    Vendor ID:                GenuineIntel
      Model name:             Genuine Intel(R) CPU 0000%@
        CPU family:           6
        Model:                106
        Thread(s) per core:   2
        Core(s) per socket:   38
        Socket(s):            2
        Stepping:             6
        CPU(s) scaling MHz:   24%
        CPU max MHz:          3400.0000
        CPU min MHz:          800.0000
        BogoMIPS:             4400.00
        Flags:                fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rd
                              tscp lm constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 ds_cpl vmx smx est t
                              m2 ssse3 sdbg fma cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowpre
                              fetch cpuid_fault epb cat_l3 intel_ppin ssbd mba ibrs ibpb stibp ibrs_enhanced tpr_shadow flexpriority ept vpid ept_ad fsgsbase tsc_adjust bm
                              i1 avx2 smep bmi2 erms invpcid cqm rdt_a avx512f avx512dq rdseed adx smap avx512ifma clflushopt clwb intel_pt avx512cd sha_ni avx512bw avx512
                              vl xsaveopt xsavec xgetbv1 xsaves cqm_llc cqm_occup_llc cqm_mbm_total cqm_mbm_local split_lock_detect wbnoinvd dtherm ida arat pln pts hwp hw
                              p_act_window hwp_epp hwp_pkg_req vnmi avx512vbmi umip pku ospke avx512_vbmi2 gfni vaes vpclmulqdq avx512_vnni avx512_bitalg tme avx512_vpopcn
                              tdq la57 rdpid fsrm md_clear pconfig flush_l1d arch_capabilities
    Virtualization features:
      Virtualization:         VT-x
    Caches (sum of all):
      L1d:                    3.6 MiB (76 instances)
      L1i:                    2.4 MiB (76 instances)
      L2:                     95 MiB (76 instances)
      L3:                     114 MiB (2 instances)
    NUMA:
      NUMA node(s):           2
      NUMA node0 CPU(s):      0-37,76-113
      NUMA node1 CPU(s):      38-75,114-151
    Vulnerabilities:
      Gather data sampling:   Mitigation; Microcode
      Itlb multihit:          Not affected
      L1tf:                   Not affected
      Mds:                    Not affected
      Meltdown:               Not affected
      Mmio stale data:        Mitigation; Clear CPU buffers; SMT vulnerable
      Reg file data sampling: Not affected
      Retbleed:               Not affected
      Spec rstack overflow:   Not affected
      Spec store bypass:      Mitigation; Speculative Store Bypass disabled via prctl
      Spectre v1:             Mitigation; usercopy/swapgs barriers and __user pointer sanitization
      Spectre v2:             Mitigation; Enhanced / Automatic IBRS; IBPB conditional; RSB filling; PBRSB-eIBRS SW sequence; BHI SW loop, KVM SW loop
      Srbds:                  Not affected
      Tsx async abort:        Not affected
      Vmscape:                Not affected
    ```

??? success "`$ dmidecode`"

    ```    
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
    ```
