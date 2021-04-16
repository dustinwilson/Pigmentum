Pigmentum
=========

[a]: https://en.wikipedia.org/wiki/CIE_1931_color_space
[b]: https://en.wikipedia.org/wiki/CIELAB_color_space
[c]: https://en.wikipedia.org/wiki/CIELUV
[d]: https://en.wikipedia.org/wiki/HSL_and_HSV
[e]: https://en.wikipedia.org/wiki/LMS_color_space
[f]: https://en.wikipedia.org/wiki/RGB_color_space

Library for manipulating color in PHP. Class exists to scratch my own itch, but maybe it'd be useful for others. There are other color classes out there, but they either work not how I'd like or the math is incorrect.

## Usage ##

Colors in Pigmentum is represented as a single color object. All color spaces in any application are converted to [XYZ][a] before converting back to another color. That's how it is handled here. At present Pigmentum handles [CIELAB][b], [CIELUV][c], [HSB/V][d], [LMS][e], [RGB][f], and [XYZ][a].

**This is a stub. The examples below only show a few things the library can do. In the future the class will be documented. **

### Convert from RGB Hex string to Lab ###

```php
namespace dW\Pigmentum;

$green = Color::withRGBHex('#00af32');
echo $green->Lab; // lab(52.953689965011, -41.955892552796, 35.496587588858)
```

### Convert from RGB Hex string in Adobe RGB (1998) color space to sRGB ###

```php
namespace dW\Pigmentum;

$green = Color::withRGBHex('#33903c', null, Color::PROFILE_ADOBERGB1998);
$green->RGB->convertToProfile(Color::PROFILE_SRGB);
echo $green->RGB; // rgb(0, 145.30458529644, 49.259546335093)
```