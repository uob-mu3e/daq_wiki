# Switching boards #

Which switching boards are enabled and their names (which are generically Central, Upstream, Downstream, Fibres, where Central is used for test setups and integration runs) are defined in

```
/Equipment/Clock Reset/Settings/SwitchingBoardMask
/Equipment/Clock Reset/Settings/SwitchingBoardNames

```
both arrays with 4 entries.

The switching board part of the ODB is created by the switch FE, which can be configured via an include to be any of the four switching boards (TODO: automating this/automatically compiling several executables)

# Switching board equipment #

The central switching board creates the following equipment and associated ODB paths

```
SwitchingCentral
LinksCentral
PixelsCentral (Can be disabled for non-pixel test setups)
TilesCentral (Integration/Test only)
SciFiCentral (Integration/Test only)

```

The upstream and downstream switching boards generate the following equipment and associated ODB paths

```
SwitchingUpstream
LinksUpstream
PixelsUpstream
TilesUpstream

```


```
SwitchingDownstream
LinksDownstream
PixelsDownstream
TilesDownstream

```
and the fibre switching board generates the following equipment and associated ODB paths


```
SwitchingFibres
LinksFibres
SciFiFibres  (to be discussed...)

```

## ODB organization ##

We use the banks in ODB idiom for slow control, so `/Equipment/XXX/Settings` will contain bank variable names and `/Equipment/XXX/Variables` will contain the bank content. With this, it makes sense to move UI commands from settings to a `/Equipment/XXX/Commands` branch on which a watch can be set.

# FEBs and Crate mapping #

`/Equipment/FEBCrates/Settings/` contains the physical position of FEBs (note that in the final system with the large backplane, each FEB will have an unique 8-Bit address, of which the MSB will be 0). In particular, `FEBCrate` denotes the crate (0-7) and `FEBSlot` denotes the slot (0-15) in the crate. With the large backplanes, we will get `unique address = 16*FEBCrate + FEBSlot`. `FEBPower` here is used to switch FEBs on and off via the crate controller (handled in febcratefe).

The FEBs then have optical fibres to the switching boards, this mapping is handled in `/Equipment/LinksCentral/Settings` (replace `Central` with `Upstream`, `Downstream`, `Fibres` for the respective switching boards). Note that the indexes in the arrays here refer to the link numbering on the switching board. `LinkMask` defines whether the RX (data) and TX (slow control) link is used. `LinkFEB` gives the unique global address of the connected FEB, `FEBType` indicates the subdetector and `FEBName` allows naming of FEBs.