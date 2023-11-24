# ![Kelvin](https://user-images.githubusercontent.com/512174/37403613-b56e883a-278f-11e8-848c-5366515e920d.png)

# About
This is a downstream fork of [stefanwichmann/kelvin](https://github.com/stefanwichmann/kelvin/) with the sole purpose of overriding the sunrise/set logic. The upstream's philosophy is to coordinate the light schedule based on sun position, where I prefer to keep a constant circadian light schedule based on my wake and sleep times, regardless of season.

A simple, lazy modification accomplishes this: the `astrotime` module that would normally calculate sunrise/set times is removed, and the `calculateSunrise` and `calculateSunset` functions always return `11:00` and `13:00` respectively. Now, the `defaultColorTemperature` and `defaultBrightness` configuration will only be active during that midday timespan, and the rest of the day can be freely customized using `beforeSunrise` and `afterSunset` schedules as normal.

## Notes on Values
Hue default scene values, found from [reddit](https://www.reddit.com/r/Hue/comments/asx5dl/color_temperature_brightness_level_of_philips_hue/):

>Assuming you're talking about the gen 3 A19 white and color ambiance bulb:
>
>```Scene	Color temp (K)	Brightness (lumens)
>Relax	2237	~200*
>Read	2890	~570
>Concentrate	4291	~800
>Energize	6410	~550
>```
>*The Relax scene is 56% brightness. Lumens calculated by multiplying brightness at 2000K (342 lm) by 0.56.
>
>And then for the gen 3 A19 white only bulb:
>```
>Scene	Color temp (K)	Brightness (lumens)
>Bright	2700	840
>Dimmed	2700	~252**
>Nightlight	2700	~84***
>```
>**Dimmed is 30% brightness. Lumens calculated by this formula: 840 x 0.30
>
>***Nightlight is 1% brightness, but there is no difference in brightness below 10%. Lumens calculated by this formula: 840 x 0.10
