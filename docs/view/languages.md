# Languages

WoltLab Suite offers full i18n support with its integrated language system,
including but not limited to dynamic phrases using template scripting and the
built-in support for right-to-left languages.

Phrases are deployed using the [language](../package/pip/language.md) package
installation plugin, please also read the [naming conventions for language items](languages-naming-conventions.md).

## Special Phrases

### `wcf.date.dateFormat`

!!! warning "Many characters in the format have a special meaning and will be replaced with date fragments. If you want to include a literal character, you'll have to use the backslash `\` as an escape sequence to indicate that the character should be output as-is rather than being replaced. For example, `Y-m-d` will be output as `2018-03-30`, but `\Y-m-d` will result in `Y-03-30`."

_Defaults to `M jS Y`._

The date format without time using PHP's format characters for the
[`date()`](https://secure.php.net/manual/en/function.date.php) function. This
value is also used inside the JavaScript implementation, where the characters
are mapped to an equivalent representation.

### `wcf.date.timeFormat`

_Defaults to `g:i a`._

The date format that is used to represent a time, but not a date. Please see the
explanation on `wcf.date.dateFormat` to learn more about the format characters.

### `wcf.date.firstDayOfTheWeek`

_Defaults to `0`._

Sets the first day of the week:
* `0` - Sunday
* `1` - Monday

### `wcf.global.pageDirection` - RTL support

_Defaults to `ltr`._

Changing this value to `rtl` will reverse the page direction and enable the
right-to-left support for phrases. Additionally, a special version of the
stylesheet is loaded that contains all necessary adjustments for the reverse
direction.
