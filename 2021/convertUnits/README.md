## convertUnits

### Overview

This script performs unit conversions between binary (IEC) and decimal (SI) data sizes, such as converting from GiB to GB or MiB to MB. It was created as part of the 2021 TwoToTheFifth Programming Contest, where entries must solve a problem in 32 lines or less (excluding blank lines and comments).
Features

  -  Supports bidirectional conversion between IEC and SI units.
  -  Accepts mixed-case input (e.g., 3GiB, 3Gib, 3gb).
  -  Avoids scientific notation in output.
  -  Trims trailing zeros after the decimal point.
  -  No external dependencies beyond POSIX tools and Perl.

```text
Usage

./convertUnits <amount><fromUnit> <toUnit>

Examples

./convertUnits 3GiB GB
3.221225GB

./convertUnits 1TB TiB
0.909495TiB

./convertUnits 500MB MiB
476.837MiB
```

**Notes**

Handles all four combinations of unit families:

 -  IEC → IEC
 -  IEC → SI
 -  SI → IEC
 -  SI → SI

Internally maps unit prefixes to powers of 10 or 2.

    Input units must be in the form of <prefix>B, such as MiB, GB, TiB.

### ⚠️ Limitations

No input validation or error checking is performed (e.g., malformed numbers or unknown units). This is intentional to stay within the contest’s 32-line constraint.

Units are case-sensitive. For example, MB (megabyte) is not the same as mb (which will not match any known unit).

 -  Recommended: Always use uppercase B and capitalized prefixes (e.g., GiB, MB, TiB).

### Origin

Written for the TwoToTheFifth Programming Contest, 2021 edition. This problem challenges contestants to write concise, elegant solutions within a strict line limit—pushing creative use of scripting tools.

