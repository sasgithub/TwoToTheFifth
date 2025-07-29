## stripUnits — Convert Human-Readable Sizes to Bytes

This script, `stripUnits`, is a concise Bash utility for converting common human-readable byte sizes into raw bytes. It was created as a compact utility for the **Cerner 2⁵ (Two to the Fifth) 2021 Programming Contest**.

### Purpose

The `stripUnits` function parses a size string (e.g., `23MB`, `4 GiB`) and converts it into the equivalent number of bytes. It supports both **decimal** (e.g., MB, GB) and **binary** (e.g., MiB, GiB) prefixes in accordance with [IEEE 1541-2002](https://en.wikipedia.org/wiki/Binary_prefix).

This utility is useful in scripts where you want to perform arithmetic with human-friendly size strings, particularly when calculating storage or memory requirements.

### Usage

You can either **source** the script to use the `stripUnits` function or execute it directly as a command-line tool.

#### Function Usage

```bash
source stripUnits
val=$(stripUnits "23 MiB")
echo $val  # Outputs 24117248
```

#### Command-Line Usage

```bash
$ ./stripUnits 4GiB
4294967296
```

#### Supported Units

|Unit|Description|Multiplier|
| B  |   Bytes   |   1|
|----|--------|------|
|KB|Kilobytes|1000|
|Ki|Kibibytes|1024|
|MB|Megabytes|1000^2|
|MiB|Mebibytes|1024^2|
|GB|Gigabytes|1000^3|
|GiB|Gibibytes|1024^3|
|TB|Terabytes|1000^4|
|TiB|Tebibytes|1024^4|
|PB|Petabytes|1000^5|
|PiB|Pebibytes|1024^5|
|EB|Exabytes|1000^6|
|EiB|Exbibytes|1024^6|

### Input Flexibility

The script accepts:

  - A single argument with or without space: 4GiB, 4 GiB
  - Two arguments: 4 GiB

### Notes & Caveats

  -  ❗ Case Sensitivity: Unit matching is case-sensitive (e.g., MiB is valid, mib is not).
  -  ❗ No Error Checking: In keeping with the 2⁵ contest's 32-line constraint, this script includes no input validation beyond basic parsing. Incorrect formats will result in a default return of 0 and exit status 1.

Author: Scott Sesher
Contest: Cerner 2⁵ 2021
Lines of logic (excluding comments and whitespace): 29
