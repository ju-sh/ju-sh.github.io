# Basic electronics stuff

 - Date created: 24-Mar-2021

Some notes on basic electronics stuff. Derived mostly from Wikipedia articles.

---

## Band gap
 - Gap between top of **valence band** and bottom of **conducting band**.
 - An energy gap.
 - Usually represented in electron volts (eV).
 - Energy required to promote a **valence electron** (electron from valence band) to make it a **conducting electron** (electron in conducting band).
 - Band gap: ([image](https://commons.wikimedia.org/wiki/File:Band_filling_diagram.svg))
   + large: insulator
   + smaller: semiconductor
   + tiny or none: conductor

## Valence electron
 - Electrons in the outer shell of the atom (**valence shell**).
 - Determines the element's chemical properties.
 - Participates in bond formation to form **covalent bonds**.
 - Atom with a **closed shell** means _chemically inert_ (as in inert gases like He, Ne, Ar, etc).

## Conduction electron
 - Free to move in the crystal lattice and serve as charge carrier for electric current.

## Electron holes
 - Lack of electron at a point where an electron could exist.
 - Like a positive charge due to the absence of the electron's negative charge => a net positive charge.
 - Holes in metals and semiconductor crystal lattices can flow the way electrons can.
 - Plays important role in the operation of diodes, transistors, etc.
 - If an electron is excited to a higher state, a hole is created at its former position.

## Diode
 - Conducts power only in one direction.
 - Has two terminals.
 - High resistance (theoretically infinite) in one direction
 - Low resistance (theoretically zero) in another direction.
 - Can be combined with other components to create logic gates like OR and AND => **Diode Resistor Logic (DRL)**

## Extrinsic semiconductor
 - Semiconductor that has been doped.

## Intrinsic semiconductor
 - Undoped semiconductor.
 - Pure semiconductor without significant amount of dopants.
 - Number of excited electrons = Number of electron holes. ie, n=p.

## Charge carrier
 - **Majority charge carrier**: The more abundant charge carrier
 - **Minority charge carrier**: The less abundant charge carrier

## Fermi level (of a solid state body)
Amount of thermodynamic work that needs to be done to add an extra electron to that solid-state body.

## Depletion region
 - An insulating region within a conductive, doped semiconductor.
 - The mobile charge carriers of this region have been diffused away (for holes?) or forced away (for electrons?) by an electric field.
 - The only remaining elements here are the ionized donor (result of extra electron addition) or acceptor impurities (result of hole creation).
 - The region is formed out of a conducting region by removing all free charge carriers => No carrier left to carry current => it becomes an insulating region.
 - Diodes, BJTs, FETs, etc rely on this phenomenon.

## p-type semiconductor
 - Made by doping an intrinsic semiconductor with an _electron acceptor element_ -> holes created.
 - Positive charge due to holes.
 - Majority carrier: Holes
 - Minority carrier: Electrons
 - Dopant for Silicon could be Boron or Gallium

## n-type semiconductor
 - Made by doping an intrinsic semiconductor with an _electron donor element_ -> extra electrons.
 - Negative charge due to extra electrons.
 - Majority carrier: Electrons
 - Minority carrier: Holes
 - Dopant for Silicon could be Phosphorus or Arsenic.

## p-n junction
 - Created by doping.
 - Boundary between two types of semiconductor materials:
   + p-type
   + n-type
 - Electric current passes in only one direction because
   + p side: has excess holes
   + n side: has excess electrons
 - A diode can be made from a single p-n junction
 - A BJT consists of two p-n junctions (either as p-n-p or as n-p-n)

## Transistor
 - Can amplify or switch electronic signals.
 - Usually has three terminals.
 - Voltage applied to one pair of terminals control current through another pair of terminals?
 - **Controlled power** is the output
 - **Controlling power** is the input
 - Controlled power could be greater than the controlling power => amplification

## Digital logic families

### Diode Resistor Logic (DRL)
 - Construction of Boolean logic gates with diodes.
 - Popular in early computers.
 - Not all logic gates can be constructed only with diodes. Only AND and OR.
 - Advantage: Simple.
 - Disadvantage: Lack of an amplifying stage in each gate (so DRL normally limited to single stage?)

### Resistor Transistor Logic (RTL)
 - Input network = resistors
 - Switching done by BJTs
 - Earliest class of 'transistorized' digital logic circuit.
 - First digital logic family to be produced as an IC.

### Diode Transistor Logic (DTL)
 - Uses diodes and invertor logic (ie, NOT).
 - Direct ancestor of TTL.
 - Came after RTL.
 - Logic gates with diodes and amplification via transistors

### Transistor Transistor Logic (TTL)
 - Built from BJTs.
 - Transistors are used to do both the logic function and the amplifying function.
 - TTL ICs were used to buid computer processors before the advent of VLSIs.

## Field Effect Transistor (FET)
 - A unipolar transistor: either electron or hole is used as charge carrier. Not both.
 - Uses an electric field to control flow of current (hence the term FET?)
 - Has three terminals:
   + Source
   + Gate
   + Drain
 - Voltage is applied to gate and the conductivity between source and drain is influenced.
 - MOSFET: Most widely used FET.

## Bipolar Junction Transistor (BJT)
 - Uses both electrons and holes as charge carriers (hence the term bipolar?)

## Impedence (in electronics)
### High impedence
 - Allows lesser amount of current to flow through in relation to the applied voltage.
 - High impedence circuits are low current and (potentially?) high voltage.
 - **Tristate** in digital circuits => neither high state nor low state. Effectively an open circuit. 
   + Basis of bus systems in computers.

### Low impedence
 - Low impedence circuits are high current and low voltage.

## Other electronic stuff of interest
 - pmos
 - nmos
 - Forward bias, reverse bias operation of p-n junction
 - Breakdown voltage of a p-n junction
 - Reverse voltage
 - inversion layer
 - cmos
 - npn
 - pnp
 - p channel
 - saturation in transistors
 - Emitter Coupled Logic (ECL)
 - MOS
 - MOSFET
