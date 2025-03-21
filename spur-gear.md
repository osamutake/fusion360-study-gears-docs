# Spur Gear

Let's create four spur gears and combine them as shown in the figure to see how they rotate.

<a href="assets/spur.gif"><img src="assets/spur.gif" width="200"/></a>

## Create the First Gear

Create the first gear with the default settings.

Create a new document, press `Shift+S` to run `study_gears`, and click OK.

The created gear will have a module $m=\mathrm{4\,mm}$ and a number of teeth $z=12$, so the pitch circle diameter will be $mz=\mathrm{48\,mm}$.

You can check this pitch circle diameter by clicking the dashed line representing the pitch circle around the gear. The diameter will be displayed at the bottom right of the screen.

<a href="assets/spur1.png"><img src="assets/spur1.png" height="200"/></a>
<a href="assets/spur2.jpg"><img src="assets/spur2.jpg" height="200"/></a>

## Create the Second Gear

Create the second gear with the number of teeth set to $z=6$.

The pitch circle diameter will be $\mathrm{24\,mm}$ for it.

<a href="assets/spur3.png"><img src="assets/spur3.png" height="200"/></a>
<a href="assets/spur4.jpg"><img src="assets/spur4.jpg" height="200"/></a>

## Combine the Gears

To set the center distance to $(12+6)\times \mathrm{4\,mm}/2$, select the 6-tooth gear in the browser, press $m$ to move it freely, i.e. translate it by the distance $(12+6)\times \mathrm{4\,mm}/2$ along the $x$-axis, and then rotate it around the $z$-axis by half a pitch $\mathrm{360\,deg}/6/2$ to mesh properly.

<a href="assets/spur5.jpg"><img src="assets/spur5.jpg" height="200"/></a>
<a href="assets/spur6.png"><img src="assets/spur6.png" height="200"/></a>

## Fix the Gear Axes

The gears are not fixed initially, so they will be translated without rotation when dragged.

<a href="assets/spur14.gif"><img src="assets/spur14.gif" height="200"/></a>

The created gear components are nested, which consists of an outer component containing an inner component containing the actual gear. These two nesting components are connected to each other by a rotational joint at the center of the gear.

<a href="assets/spur7.png"><img src="assets/spur7.png" height="200"/></a>

Fixing the outer component to the root component will fix the gear axis, allowing the inner component to rotate freely around it.

To fix the outer component to the root component, selecting the "Ground to Parent" item in the right-click menu of the component seems to work. However, it is a dangerous trap. Using "Ground to Parent" moves the correctly placed component back to the original position. So, do not select it.

Instead, select "Rigid Group" in the right-click menu of the root component.

<a href="assets/spur8.png"><img src="assets/spur8.png" height="200"/></a>

When prompted to capture the position, select "Capture Position".

<a href="assets/spur9.png"><img src="assets/spur9.png" height="150"/></a>

If asked whether to include the rotational joint in the rigid group, select Yes. Actually, if we include the rotational joint in a rigid group, it won't rotate. So, we do not want to do it. However, at this moment, we do not have any other option. So, select yes.

<a href="assets/spur10.png"><img src="assets/spur10.png" height="120"/></a>

Then, we finally reach the rigid group dialog, to select which components should be included by the group.

The reason why the warning which means "Rotation joint(s) is/are included in the rigid group target" appears even when only the root component was selected, was because the "Include Child Components" checkbox in this dialog was checked. In this context, this "Child" means descendants. So, with this option, all the components will be included in the rigid group and can not be moved any more.

In the figure, we can confirm this point. Even though only the root component is selected and it tells us only 1 component is selected, all the components including nested descendant components are highlighted.

<a href="assets/spur11.png"><img src="assets/spur11.png" height="120"/></a>

So, uncheck "Include child components" to deselect the descendant components.

<a href="assets/spur12.png"><img src="assets/spur12.png" height="120"/></a>

Then, re-select only the outer components of the two gears, to fix them to the root component.

<a href="assets/spur13.png"><img src="assets/spur13.png" height="110"/></a>

Now, the gears will rotate around their axes without moving their axes positions.

<a href="assets/spur15.gif"><img src="assets/spur15.gif" height="200"/></a>

## Link the Rotations of the Two Axes

The two gear axes are fixed and can rotate, but their rotations are not linked yet.

Use the "Motion Link" feature to link the motion of the two gears.

Select the two axes in the dialog, specify the rotation amounts by dividing 360 degrees by the number of teeth, and check the "Reverse" box for opposite rotation directions.

<a href="assets/spur16.png"><img src="assets/spur16.png" height="300"/></a>
<a href="assets/spur17.png"><img src="assets/spur17.png" height="250"/></a>

Now, the two gears will rotate together. Drag one gear to see the other rotates correctly.

<a href="assets/spur18.gif"><img src="assets/spur18.gif" height="250"/></a>

## Simulate Backlash

The linked axes do not reflect backlash.

At close look, the gears do not actually touch, maintaining a gap equal to the backlash, i.e. one gear's rotation is transmitted to the other *without contact*.

<a href="assets/spur19.gif"><img src="assets/spur19.gif" height="250"/></a>

To simulate realistic gear movement with backlash, suppress the "Motion Link" and use "Contact Sets".

Right-click the motion link and select "Suppress", then enable "Contact Sets" from the Assembly menu.

<a href="assets/spur20.png"><img src="assets/spur20.png" height="250"/></a>
<a href="assets/spur21.png"><img src="assets/spur21.png" height="250"/></a>

Create a contact set by right-clicking "Contact Sets" and selecting "New Contact Set", then select the two gear bodies.

<a href="assets/spur22.png"><img src="assets/spur22.png" height="200"/></a>
<a href="assets/spur23.png"><img src="assets/spur23.png" height="200"/></a>

Now, the gears will only transmit motion when they touch, simulating realistic gear movement with backlash.

<a href="assets/spur24.gif"><img src="assets/spur24.gif" height="200"/></a>

Contact analysis is more computationally intensive than motion links, so use motion links unless backlash simulation is necessary.

## Continue with contact analysis

To observe the transmission of backlash through multiple gears, we continue using contact analysis in this tutorial.

## Add the Third Gear

Create a 6-tooth gear.

Move it $\mathrm{5\,mm}$ in the $z$ direction, onto the face of the first gear.

<a href="assets/spur25.png"><img src="assets/spur25.png" height="100"/></a>

To add this gear into the existing rigid group, we need reordering the history so the rigid group creation comes after the gear creation to have the gear already created when the rigid group is created.

Watch out! Before reordering, we need to capture the components position first, to prevent reverting the positioning of the component.

<a href="assets/spur26.png"><img src="assets/spur26.png" height="200"/></a>

Reorder the features in the history by dragging.

<a href="assets/spur27.gif"><img src="assets/spur27.gif" height="100"/></a>

Edit the rigid group to include the new gear, to fix the position of its rotation axis.

<a href="assets/spur28.png"><img src="assets/spur28.png" height="200"/></a>

<a href="assets/spur29.png"><img src="assets/spur29.png" height="265"/></a>

Create a motion link between the first and third gear axes to link their rotations.

Disable "Animation" in the contact set to avoid lag due to the contact analysis.

<a href="assets/spur30.png"><img src="assets/spur30.png" height="265"/></a>

Now, the three gears rotate together correctly.

## Add the Fourth Gear

Add an 18-tooth gear and move it to mesh with the third gear.

Before doing it, rotate the first gear slowly back to the original position to make finding the meshing angle easy.

<a href="assets/spur31.png"><img src="assets/spur31.png" height="265"/></a>

Then, capture the position, reorder the history, and add the fourth gear to the rigid group as same as the above procedure.

Create a contact set between the third and fourth gear bodies.

<a href="assets/spur32.png"><img src="assets/spur32.png" height="265"/></a>

Now, everything should be ready!

## This Method Didn't Work...

The gears got stuck and didn't rotate.

Having a motion link between contact sets seems too complex for Fusion 360 to analyze.

## Using Rigid Sets Instead of Motion Links

To solve the issue, suppress the motion link between gears 1 and 3, and create a rigid group between their child components instead.

This allows Fusion 360 to correctly simulate gear movement with backlash.

<a href="assets/spur33.gif"><img src="assets/spur33.gif"/></a>
