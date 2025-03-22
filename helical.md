# Combining Two Helical Gears and Checking Their Meshing

[[Back to fusion360-study-gears tutorial]](https://github.com/osamutake/fusion360-study-gears/blob/main/README.md#tutorial)

## Generating Two Helical Gears

The parameters are as follows:

<table>
<tr><th><th>First Gear<th>Second Gear
<tr><th>Module<td colspan="2" align="center">4 mm
<tr><th>Num. Teeth<td align="center">12<td align="center">6
<tr><th>Thickness<td colspan="2" align="center">20 mm
<tr><th>Helix Angle<td colspan="2" align="center">45 deg
<tr><th>Helix Direction<td align="center">Right<td align="center">Left
<tr><th>Backlash<td colspan="2" align="center">-0.01 mm
</table>

- The helix directions of the two meshing helical gears need to be opposite.
- A negative backlash is set to check the meshing condition.
  - These two gears cannot be placed at the standard center distance due to interference, but Fusion 360 can visualize the interference areas that helps checking the contact area of the two gears.

The pitch diameters of helical gears are elongated compared to the standard spur gears by a factor of $1/\cos(45\mathrm{\,deg})$ in this case:

- First Gear: 67.882 mm = 4 mm * 12 / cos(45 deg)
- Second Gear: 33.941 mm = 4 mm * 6 / cos(45 deg)

Thus, the second gear should be positioned by:

- Moving 50.9115 mm in the X direction = 4 * 18 / cos(45 deg) / 2
- Rotating 30 deg around the center axis

The movement can be written as 4 mm * (12 + 6) / cos(45 deg) / 2 instead of copying 50.9115 mm.

<a href="assets/helical1.jpg"><img src="assets/helical1.jpg" width="300"></a>
<a href="assets/helical2.jpg"><img src="assets/helical2.jpg" width="250"></a>

## Checking Tooth Contact

Invoke the "Interference" tool from the "Inspect" menu.

When asked "Do you want to capture the position of the moved components?", select "Capture Position" to keep the current position of gears.

<a href="assets/helical3.jpg"><img src="assets/helical3.jpg" width="300"></a>
<a href="assets/helical4.jpg"><img src="assets/helical4.jpg" width="200"></a>

Select the two gear bodies. Then, click "Compute" to display the interfering regions and calculate their volume.

<a href="assets/helical5.png"><img src="assets/helical5.png" width="250"></a>
<a href="assets/helical6.png"><img src="assets/helical6.png" width="250"></a>

## Advantages of Helical Gears

Helical gears can be considered as multiple spur gears with different rotation directions stacked along the gear thickness. Therefore, even if some parts are not meshing, other parts often are. The timing of tooth contact and separation is distributed along the thickness. These characteristics results in stable meshing and low noise.

To see it, the two gears are rotated step by step while calculating the interference on each step:

<a href="assets/helical7.gif"><img src="assets/helical7.gif" width="500"></a>

Here, the smaller gear on the right has small involute region due to large undercut, which results in some part of rotation period missing meshing. However, as the gears rotate, the contact area moves continuously along the gear thickness and even when some part lost meshing, some other part maintains meshing. The contact area increases and decreases gradually, suggesting low noise. 

(By the way, this video was manually created by connecting the results of the "Interference" inspection. Unfortunately, there is no automatic function to create such a video.)

Comparing this with spur gears, the difference is clear. Spur gears have periods with no contact and sudden changes in contact area, likely causing vibration and noise.

<a href="assets/helical8.gif"><img src="assets/helical8.gif" width="500"></a>

# Double Helical Gears: Eliminating Helical Gear Disadvantages

Helical gears have significant advantages but also generate unfavorable axial thrust loads.

Double helical gears, which combine two helical gears with opposite helix angles, cancel out the thrust loads. Its only one disadvantage might be increased thickness.

Double helical gears can be easily created by mirroring a helical gear along its top surface.

<a href="assets/helical9.jpg"><img src="assets/helical9.jpg" width="200"></a>
<a href="assets/helical10.jpg"><img src="assets/helical10.jpg" width="270"></a>

Mirroring both gears completes the double helical gear.

<a href="assets/helical11.gif"><img src="assets/helical11.gif" width="400"></a>

## Creating a Gap

The kink part of the teeth of the double helical gears may cause tight contact when combined.

To create some gap there, extruding the top surface of the gear with a negative taper angle before mirroring may help.

<a href="assets/helical12.jpg"><img src="assets/helical12.jpg" width="400"></a>

<a href="assets/helical13.jpg"><img src="assets/helical13.gif" width="400"></a>

Although the shape is a bit weird, a 45-degree taper angle allows 3D printing without support, making it a viable option.

[[Back to fusion360-study-gears tutorial]](https://github.com/osamutake/fusion360-study-gears/blob/main/README.md#tutorial)
