# Intro
This repo contains all the Eagle libraries I use in all of my designs. Doing so helps to commonize on part numbers and create more consistent schematics across projects.

# Guidelines
Here are a few guidlines I follow when creating library "components", "symbols", and "footprints".

## Components
All components have the following items added and filled out completely. This helps for organization purposes, but also assists in creating complete and useful BOMs for a schematic.
- **Name:** When creating the component within a library, the name is the "base PN", and any variant PN (usually separated from the base PN by a hyphen) will be placed in the "Variant" option which will be discussed below.
- **Description:** All componenets created have the "Description" field filled out. This is typically the short-hand description given by the parts distributor. It summarizes the components characteristics in as few characters as possible.
  - Ex. **P-Channel 30V 3.8A (Ta) 1.08W (Ta) Surface Mount SOT-23**
- **Attributes:** The following attributes are included on all part numbers. Attributes are unique to the variant of the component you are editing.
  - **MF:** Manufacturer
  - **MP:** Manufacturer Part Number (This would be the FULL PN, meaning the base PN + any variant PN)
  - **VALUE:** In the case of a passive, this is just the components value. When dealing with any other modules like micros, transceivers, etc. the VALUE is just filled with the Manufacturer Part Number. I don't know if this is correct, but for the sake of my OCD, it ensures every line item in a BOM has something filled in for the VALUE.
- **Variant:** Variants are created and used in several situations. The first being if you have different footprint sizes, to be paired with a single schematic symbol. You could also create variants when you have the same schematic symbol and PCB footprint, but different values for the component (Example being a resistor or capacitor that have the same base PN, but a variant PN is given to indicate the resistor value)
  - Ex. The RR0816P resistor family by Susumu is a family of 0603 resistors, and the value of the resistor can be found in the variant portion of the PN
    - 0603 Resistor with 1k resistance part number is RR0816P-102. This means the component name would be **RR0816P**, and it would have a variant named **-102**. When looking at the library in the schematic editor, you would then see a component with the full name **RR0816P-102**. Keep in mind, that you would also need to modify the "Value" and "MP" attributes for EACH variant.
- **Prefix:** Located in the bottom right of the screen when viewing a component will be a prefix text box. This is a one character prefix to be used in the component name when placing it on a schematic and PCB. (D, C, R, U, J. etc..)
- **Component value radio button:** Located right next to the prefix text box is a radio button for turning the componenet value on or off. I set all of these to ON, as this will allow the components VALUE attribute to be displayed on a Symbol or Footprint when the >VALUE keyword is used. This will be explained further below.

## Symbols
I have very few guidlines I am currently following when creating schematic symbol shapes and pin layout. I intend to eventually go back through and attempt to clean up symbols and follow a hybrid of the IEEE-315 standard and my own preferences. I do have a few things I ensure are done on a symbol though.
- **Name:** I ensure the name is added to the top of the symbol using a text import on the "Names" layer, and place the text >NAME. Doing so will add the component prefix, and auto increment a number which is essentially a count of components with that same prefix.
- **Value:** I also place the value at the bottom of the symbol using a text import on the "Values" layer, and place the text >VALUE. Using the keyword >VALUE will ensure that the value given within the components VALUE attribute, will be shown on the schematic.

## Footprints
Again, I have few guidlines I follow when creating footprints, but intend to eventually go backthrough and more closely follow the IPC-7351B guidelines for creating component footprints. Here are the few guidelines I follow currently.
- **Name:** I ensure the name is added to the top of the symbol using a text import on the "tNames" layer, and place the text >NAME. Doing so will add the component prefix, and auto increment a number which is essentially a count of components with that same prefix.
- **Value:** I also place the value at the bottom of the symbol using a text import on the "tValues" layer, and place the text >VALUE. Using the keyword >VALUE will ensure that the value given within the components VALUE attribute, will be shown on the schematic.
- **SM Pad Roundness:** All SMD pads I create are rounded to 25%

This is not a complete list, and I will update further as I remember items to be added.
