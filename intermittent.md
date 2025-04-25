# Intermittent Gear

[[Back to fusion360-study-gears tutorial]](https://github.com/osamutake/fusion360-study-gears/blob/main/README.md#tutorials)

Let's create and simulate an intermittent gear.

<a href="assets/intermittent40.gif"><img src="assets/intermittent40.gif" width="500"></a>

The intermittent gear created on this page has the following characteristics:

- When the right gear completes one revolution, the left gear rotates 1/4 turn.
- The left gear is based on an 8-tooth gear:
  - The upper half is an 8-tooth gear as is.
  - In the lower half, every other tooth is removed.
- The right gear is based on a 20-tooth gear:
  - The tip circle radius is reduced to avoid interference with the small gear.
  - The upper half retains only two teeth, with the rest removed.
  - The lower half has grooves cut only between the two teeth.
- Power is transmitted by the two teeth of the right gear.
- When the teeth are not meshing, the tip circle of the lower half of the right gear contacts the remaining teeth of the lower half of the small gear, preventing the small gear from rotating.

Below, we introduce the design method and simulation process in Fusion 360.

## Generating the Gears

Create an 8-tooth and a 20-tooth gear with module 4 and thickness 10 mm.

<a href="assets/intermittent1.jpg"><img src="assets/intermittent1.jpg" width="300"></a>
<a href="assets/intermittent2.jpg"><img src="assets/intermittent2.jpg" width="300"></a>

## Moving to the Meshing Position

Move the large gear component along the x-axis by $4\,\mathrm{mm}\times(8+20)/2$.

Rotate the small gear body around its axis by $360\,\mathrm{deg}/8/2$.

<a href="assets/intermittent3.jpg"><img src="assets/intermittent3.jpg" width="300"></a>
<a href="assets/intermittent4.jpg"><img src="assets/intermittent4.jpg" width="300"></a>

## Removing Every Other Tooth on the Lower Half of the Small Gear

Create a new sketch on the xy-plane:
- Capture the position of the gear component.

<a href="assets/intermittent5.jpg"><img src="assets/intermittent5.jpg" width="300"></a>
<a href="assets/intermittent6.jpg"><img src="assets/intermittent6.jpg" width="300"></a>

Project the outer shape of the small gear onto the sketch:
- Right-click on the small gear.
- Select "Sketch."
- Select "Project."
- Set the filter to "Body," select the gear, and click OK.

<a href="assets/intermittent7.jpg"><img src="assets/intermittent7.jpg" width="300"></a>
<a href="assets/intermittent8.jpg"><img src="assets/intermittent8.jpg" width="300"></a>
<a href="assets/intermittent9.jpg"><img src="assets/intermittent9.jpg" width="300"></a>

Draw the root circle.

<a href="assets/intermittent10.jpg"><img src="assets/intermittent10.jpg" width="300"></a>

Select the four teeth shown in the diagram and remove them using extrusion.

<a href="assets/intermittent11.jpg"><img src="assets/intermittent11.jpg" width="300"></a>
<a href="assets/intermittent12.jpg"><img src="assets/intermittent12.jpg" width="300"></a>

## Reducing the Tip of the Large Gear

Create a new sketch based on the reference circle of the large gear.

<a href="assets/intermittent13.jpg"><img src="assets/intermittent13.jpg" width="300"></a>

Project the tooth profile of the small gear and draw a curve offset by 0.1 mm.

<a href="assets/intermittent14.jpg"><img src="assets/intermittent14.jpg" width="300"></a>
<a href="assets/intermittent15.jpg"><img src="assets/intermittent15.jpg" width="300"></a>

Draw a circle from the center of the large gear (origin of the sketch).

Make it tangent to the offset curve created above:
- Since a tangent constraint cannot be set between them, adjust manually.

<a href="assets/intermittent16.jpg"><img src="assets/intermittent16.jpg" width="300"></a>
<a href="assets/intermittent17.jpg"><img src="assets/intermittent17.jpg" width="300"></a>

Extrude the circle infinitely in both directions and calculate intersection with the gear.

<a href="assets/intermittent18.jpg"><img src="assets/intermittent18.jpg" width="300"></a>

This trims the tip of the large gear.

## Creating the Lower Half of the Large Gear

Create a new sketch based on the reference circle of the large gear (diagram omitted).

Project the two points at the tip of the teeth onto the sketch.

Draw two radii and arcs based on these points.

Extrude the resulting profile to fill all but one tooth groove.

<a href="assets/intermittent19.jpg"><img src="assets/intermittent19.jpg" width="300"></a>
<a href="assets/intermittent22.jpg"><img src="assets/intermittent22.jpg" width="300"></a>
<a href="assets/intermittent23.jpg"><img src="assets/intermittent23.jpg" width="300"></a>

Switch the view to the opposite side for the next step.

<a href="assets/intermittent24.jpg"><img src="assets/intermittent24.jpg" width="300"></a>
<a href="assets/intermittent25.jpg"><img src="assets/intermittent25.jpg" width="300"></a>

## Creating the Upper Half of the Large Gear

Create a new sketch based on the reference circle of the large gear.

Draw a line tilted by $360\,\mathrm{deg}/20$ from the x-axis.

Mirror it across the x-axis.

Draw an arc larger than the tip circle.

<a href="assets/intermittent26.jpg"><img src="assets/intermittent26.jpg" width="300"></a>
<a href="assets/intermittent27.jpg"><img src="assets/intermittent27.jpg" width="300"></a>
<a href="assets/intermittent28.jpg"><img src="assets/intermittent28.jpg" width="300"></a>
<a href="assets/intermittent29.jpg"><img src="assets/intermittent29.jpg" width="300"></a>

Project the root point onto the sketch.

Draw an arc passing through the point and intersecting the two radii.

<a href="assets/intermittent30.jpg"><img src="assets/intermittent30.jpg" width="300"></a>
<a href="assets/intermittent31.jpg"><img src="assets/intermittent31.jpg" width="300"></a>

Extrude the profile to remove all but two teeth.

<a href="assets/intermittent32.jpg"><img src="assets/intermittent32.jpg" width="300"></a>

## Fixing the Rotation Axes of the Gears

Create a rigid group including the two gear components and the root component:
- Select the two gear components and choose "Create Rigid Group."
- When asked whether to include the rotation axes, select "Yes."
- Uncheck "Include child components."
- Add the root component and click OK.

<a href="assets/intermittent34.jpg"><img src="assets/intermittent34.jpg" width="260"></a>
<a href="assets/intermittent35.jpg"><img src="assets/intermittent35.jpg" width="240"></a>

<a href="assets/intermittent36.jpg"><img src="assets/intermittent36.jpg" width="200"></a>
<a href="assets/intermittent37.jpg"><img src="assets/intermittent37.jpg" width="200"></a>

## Setting a Contact Set Between the Gears

Select "Enable Contact Set" from the Assemble menu.

Select "New contact set".

Select the two gears and click OK.

<a href="assets/intermittent38.jpg"><img src="assets/intermittent38.jpg" width="400"></a>

<a href="assets/intermittent39.jpg"><img src="assets/intermittent39.jpg" width="300"></a>

<a href="assets/intermittent33.jpg"><img src="assets/intermittent33.jpg" width="300"></a>

## Testing the Rotation

I spend some time to obtain the video below because
somehow the simulation using the contact set does not to run smoothly.

<a href="assets/intermittent40.gif"><img src="assets/intermittent40.gif" width="600"></a>

It can be seen that the rotation speed of the small gear changes discontinuously, preventing smooth operation of gears.

This is significantly different from the [Geneva gear](geneva.md), which also performs intermittent motion but accelerates gradually from zero speed.

The intermittent gear with missing teeth shown here is likely only suitable for light loads and slow speeds.

----
[[Back to fusion360-study-gears tutorial]](https://github.com/osamutake/fusion360-study-gears/blob/main/README.md#tutorials)
