# Generate and Rotate Bevel Gears

[[Go back to fusion360-study-gears Tutorials]](https://github.com/osamutake/fusion360-study-gears/#tutorials)

Bevel gears are gears that can mesh at arbitrary angles between two rotational axes.

<a href="assets/bevel6.gif"><img src="assets/bevel6.gif" width="400"></a>

Bevel gears are challenging to manufacture through cutting, so various tooth profiles have been developed. Among these, when manufacturing constraints like cutting are not a concern, such as with 3D printing, bevel gears with a spherical involute curve as the tooth profile can be used, similar to how involute gears are used for planar gears. This approach is introduced in the following article:

https://thermalprocessing.com/computerized-design-of-straight-bevel-gears-with-optimized-profiles-for-forging-molding-or-3d-printing/

This script generates bevel gears with spherical involute curves as their tooth profiles.

- Fillets at the tooth root
- Undercutting for small gears
- Spiral teeth

are supported. However:

- Changing the fillet radius is not supported.
- Profile shifting is not supported.

Internally, the tooth profile is calculated on a spherical surface, as the name "spherical involute" suggests.

<a href="assets/bevel7.gif"><img src="assets/bevel7.gif" width="400"></a>

> While implementing this script, I realized that Fusion 360 allows creating gear tooth grooves by generating surface patches from tooth profiles drawn on a spherical surface, arranging them, and connecting them using lofts. I had mistakenly thought that only planar shapes recognized as profiles could be connected using loft feature.

## Generating Bevel Gears

Open the bevel tab and press OK to generate two bevel gears meshed together, as shown in the figure.

<a href="assets/bevel8.jpg"><img src="assets/bevel8.jpg" width="600"></a>

The size of the gears is determined by the module, number of teeth, and shaft angle. The width specifies the generated tooth width.

These gears are fixed with rotational joints, so you can set motion links to make them move together immediately.

## Detail of Tooth Profile

Here is a close-up of the contact area of gears created with zero backlash.

<a href="assets/bevel5.gif"><img src="assets/bevel5.gif" width="500"></a>

As mentioned earlier, the tooth profile of the bevel gears generated by this script is not a reused profile from standard spur gears. Instead, it is properly formed using spherical involute curves specifically for bevel gears.

This ensures that the two gears mesh correctly and precisely.

In this case, undercutting occurs on the smaller gear at the top.

Undercutting refers to the removal of material at the tooth root to prevent interference between the tip of the other gear. This results in appearance of a spherical trochoidal curve at the tooth root.

This script calculates not only the spherical involute region at the tooth tip but also the spherical trochoidal region at the tooth root, ensuring that the gears rotate smoothly even in the cases like this combination.

If the tooth profile were generated using only spherical involute curves without correctly calculating the trochoidal region, it would result in undefined shapes at the tooth root or interference between the two gears, preventing rotation.

The larger gear at the bottom in the figure does not experience undercutting, but a spherical trochoidal curve also appears as a fillet that smoothly connects the involute region at the tooth tip to the tooth bottom.

<a href="assets/bevel10.gif"><img src="assets/bevel10.gif" width="500"></a>

Bevel gears were generated with module 6 and numbers of teeth 30 and 15 with 90 deg between axes with backlash set to -0.03 mm. We can check the contact between the two gears by visualizing the interfering part during their combined rotation.

I wanted to have smaller values for backlash but smaller backlash caused errors in boolean operation of gear shapes. So, I set unwanted large negative backlash to have clear overlap between the gears.

It can be confirmed that the tooth shapes generated from the spherical involute curve contact nicely with each other.

## Supporting Spiral Teeth

By entering a none-zero value for the Spiral Angle, you can create bevel gears with spiral teeth.

<a href="assets/bevel4.gif"><img src="assets/bevel4.gif" width="500"></a>

Similar to helical gears, spiral teeth result in a larger gear size because the transverse module is larger than the normal module.

I tried to create bevel gears with spiral teeth and negative backlash to verify tooth contact through interference checks. However, probably due to the complexity of the tooth profile, boolean operations frequently report failures, and the calculations could not be completed successfully.

## Can It Replace Face Gears?

Since calculating the exact tooth profile of face gears (crown gears) is challenging, bevel gears might be used as a substitute.

Note that with bevel gears, the tooth contact changes when the smaller gear moves along the axis direction, so care must be taken in this regard.

<a href="assets/bevel3.gif"><img src="assets/bevel3.gif" width="400"></a>

----
[[Go back to fusion360-study-gears Tutorials]](https://github.com/osamutake/fusion360-study-gears/#tutorials)