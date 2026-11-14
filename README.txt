Lenovo Legion 82WK / RTX 4060 Laptop - 140 W TGP Unlock on Linux
================================================================

Public notes from a real 140 W unlock on a Lenovo Legion Y9000P IRX8 (82WK,
i9-13900HX, RTX 4060 Laptop 8 GB, BIOS KWCN54WW, Ubuntu 22.04, NVIDIA 595.99.02).

Result: 140 W GPU power budget unlocked; 140.43 W peak, 137-139 W sustained
heavy load. No ACPI table override, no VBIOS mod, no patched NVIDIA module.

The real limiter was the EC value gpu_power_target_offset (NVPCF TPPA, total
CPU+GPU power on AC), clamped to 110 W by the LegionLinux sysfs attribute.
A raw ACPI WMAE call sets it to 255 W, which gives cTGP 115 W + PPAB 25 W = 140 W.

Full plain-text write-up, including every dead end and pitfall:
  legion-4060-140w-linux-unlock.txt

Key topics: Dynamic Boost, NVPCF, NPCF _DSM, TPPA, TGPA, MAGA, cTGP, PPAB,
LegionLinux, acpi_call, WMAE, thermal throttling, fan_fullspeed.
