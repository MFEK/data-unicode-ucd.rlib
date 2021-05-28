# Unicode Character Database (UCD) Data

Data mirror of Unicode® Character Database (UCD) data-set
(<https://unicode.org/Public/>).

See <https://github.com/open-i18n/data-unicode> for more details.

# License

Please see Unicode® Terms of Use (<https://www.unicode.org/copyright.html>) for
License Agreement of these data files.

This is an unofficial repository and is not affiliated with the Unicode
Consortium. Unicode® is a trademark of the Unicode Consortium.

# This is a fork for Unicode 14.0

The original version of this is [here](https://github.com/open-i18n/data-unicode-ucd/tree/2a2044479b3c4915ef4213adf1dfd6236dba24c8).

Ran this to get the data:

```bash
# Unicode 14.0 is coming soon, and I wanted its names instead of the current names because I am responsible for a few of 'em.

rm -rf /tmp/unicode.org
OPWD=$PWD
cd /tmp
wget -r -l5 --no-parent https://unicode.org/Public/14.0.0/ucd/
find . -iname '*.txt' -type f | parallel mv {} {= '$_ =~ s/-14\.0\.0d\d+//;' =}
cd $OPWD/data
find /tmp/unicode.org/Public/14.0.0/ucd -type f | parallel mv {} {= '$_ =~ s@/tmp/unicode.org/Public/14.0.0/ucd/@@;' =}
cd ..
```
