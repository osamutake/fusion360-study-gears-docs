# Screw Gear

[[Go back to fusion360-study-gears Tutorials]](https://github.com/osamutake/fusion360-study-gears/#tutorials)

You can use two helical gears twisted in the same direction as a screw gear by placing them on a shaft twisted by the sum of the helix angles.

<a href="assets/screw-gear11.gif"><img src="assets/screw-gear11.gif" width="400" /></a>
<a href="assets/screw-gear10.gif"><img src="assets/screw-gear10.gif" width="400" /></a>

## Creation Procedure

Here, we will prepare two 45-degree helical gears and combine them by placing them on shafts intersecting at 90 degrees.

First, generate a 45-degree helical gear.
The reference circle diameter is 67.882 mm.

<a href="assets/screw_gear1.jpg"><img src="assets/screw_gear1.jpg" width="182" /></a>
<a href="assets/screw_gear2.jpg"><img src="assets/screw_gear2.jpg" width="300" /></a>

Duplicate the gear and move it to the meshing position.
Specifically, move by the reference circle diameter, rotate 90 degrees, and rotate by half a pitch.

<a href="assets/screw_gear4.jpg"><img src="assets/screw_gear4.jpg" width="500" /></a>

Create a rigid group including the root component and the two gears to fix the position of the gears. By not including child components, only the rotation axis is fixed, allowing rotation.

<a href="assets/screw_gear5.jpg"><img src="assets/screw_gear5.jpg" width="350" /></a>
<a href="assets/screw_gear6.jpg"><img src="assets/screw_gear6.jpg" width="200" /></a>

Select the two rotation axes and create a motion link.

<a href="assets/screw_gear7.jpg"><img src="assets/screw_gear7.jpg" width="350" /></a>

Now it rotates correctly.

<a href="assets/screw-gear11.gif"><img src="assets/screw-gear11.gif" width="400" /></a>
<a href="assets/screw-gear10.gif"><img src="assets/screw-gear10.gif" width="400" /></a>

----
[[Go back to fusion360-study-gears Tutorials]](https://github.com/osamutake/fusion360-study-gears/#tutorials)
