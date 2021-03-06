OCOPT = -f -w
AMBV = -av .02 .02 .02
DEV = x11
VIEW = -vf vf/current.vf
RVOPT = $(AMBV) -o $(DEV) $(VIEW) -w
# parts/ovhatch.rad
# vert_rib.rad
# port.rad
# parts/ohhatch.rad
# parts/hatch_door.rad
# parts/hhatch.rad
GEOMETRY = \
parts/hatch_hook.rad
# ship.rad
PATCHED_FILES = \
applicator.rad \
materials.rad \
meters.rad \
port.rad \
parts/brass_nut.rad \
parts/cable_rack.rad \
parts/chainlink.rad \
parts/chain_pole.rad \
parts/connector.rad \
parts/connector_plug.rad \
parts/cvhatch.rad \
parts/exting2.rad \
parts/extinguisher.rad \
parts/handle.rad \
parts/handrail.rad \
parts/hatchway.rad \
parts/hhandrail.rad \
parts/hhatch.rad \
parts/hstairs.rad \
parts/latch_handle.rad \
parts/ohhatch.rad \
parts/ovhatch.rad \
parts/stairs.rad \
parts/vert_hatch.rad \
parts/vh_shinge.rad \
vf/current.vf \
vf/port+bow_cvhatch+valves.vf \
vf/port+bow_stairs.vf \
vf/port+mid_hatch.vf

all:	shipfull.oct shipemer.oct shipbatl.oct

clean:
	-rm -f *~ *.oct *.rej parts/*~ parts/*.rej *.sh *.amb *.tiff *.hdr

clobber: clean
	-rm -f parts/blender.rad
	git checkout $(PATCHED_FILES)

blender: apply_patches parts/blender.rad

parts/blender.rad: \
materials.rad \
$(GEOMETRY)
	cat materials.rad $(GEOMETRY) > parts/blender.rad

apply_patches: materials.patch
	-echo "apply patches ..."
	patch applicator.rad -i applicator.patch
	patch materials.rad -i materials.patch
	patch meters.rad -i meters.patch
	patch port.rad -i port.patch
	patch parts/brass_nut.rad -i parts/brass_nut.patch
	patch parts/cable_rack.rad -i parts/cable_rack.patch
	patch parts/chainlink.rad -i parts/chainlink.patch
	patch parts/chain_pole.rad -i parts/chain_pole.patch
	patch parts/connector.rad -i parts/connector.patch
	patch parts/connector_plug.rad -i parts/connector_plug.patch
	patch parts/cvhatch.rad -i parts/cvhatch.patch
	patch parts/exting2.rad -i parts/exting2.patch
	patch parts/extinguisher.rad -i parts/extinguisher.patch
	patch parts/handle.rad -i parts/handle.patch
	patch parts/handrail.rad -i parts/handrail.patch
	patch parts/hatchway.rad -i parts/hatchway.patch
	patch parts/hhandrail.rad -i parts/hhandrail.patch
	patch parts/hhatch.rad -i parts/hhatch.patch
	patch parts/hstairs.rad -i parts/hstairs.patch
	patch parts/latch_handle.rad -i parts/latch_handle.patch
	patch parts/ohhatch.rad -i parts/ohhatch.patch
	patch parts/ovhatch.rad -i parts/ovhatch.patch
	patch parts/stairs.rad -i parts/stairs.patch
	patch parts/vert_hatch.rad -i parts/vert_hatch.patch
	patch parts/vh_shinge.rad -i parts/vh_shinge.patch
	patch vf/current.vf -i vf/current.patch
	patch vf/port+bow_cvhatch+valves.vf -i vf/port+bow_cvhatch+valves.patch
	patch vf/port+bow_stairs.vf -i vf/port+bow_stairs.patch
	patch vf/port+mid_hatch.vf -i vf/port+mid_hatch.patch

port.oct:	port.rad cvhatch.oct ohhatch.oct ovhatch.oct \
stairs.oct ventbox.oct valve.oct connbox.oct extinguisher.oct cable_rack.oct \
cdoor.rad horiz_rib.rad vert_rib.rad fire_valve.rad breather.oct helmet.oct \
jbox1.rad jbox2.rad meters.rad portfullfixt.rad lantern.rad fixt1.rad fixt2.rad\
parts/red_box.rad parts/hydrant.rad exting2.oct support_bracket.rad \
applicator.rad applicat_head.rad 
	oconv $(OCOPT) materials.rad port.rad portfullfixt.rad > port.oct

view:	shipfull.oct
	rvu $(RVOPT) shipfull.oct

view_all: shipfull.oct
	find vf/ -name "*.vf" -print -exec rvu $(AMBV) -o $(DEV) -vf {} -w shipfull.oct \;

shipfull.oct:	ship.oct shipfullfixt.rad lantern.rad fixt1.rad fixt2.rad \
portfullfixt.rad
	oconv $(OCOPT) -i ship.oct shipfullfixt.rad > shipfull.oct

shipred.oct:	ship.oct shipredfixt.rad lantern.rad fixt1o.rad \
fixt2o.rad fixt1r.rad fixt2r.rad portredfixt.rad
	oconv $(OCOPT) -i ship.oct shipredfixt.rad > shipred.oct

shipemer.oct:	ship.oct shipemerfixt.rad lantern.rad fixt1e.rad fixt2e.rad \
fixt1o.rad fixt2o.rad portemerfixt.rad
	oconv $(OCOPT) -i ship.oct shipemerfixt.rad > shipemer.oct

shipbatl.oct:	ship.oct shipbatlfixt.rad lanternon.rad fixt1o.rad fixt2o.rad \
portbatlfixt.rad
	oconv $(OCOPT) -i ship.oct shipbatlfixt.rad > shipbatl.oct

ship.oct:	ship.rad port.rad cvhatch.oct ohhatch.oct ovhatch.oct \
stairs.oct ventbox.oct valve.oct connbox.oct extinguisher.oct cable_rack.oct \
cdoor.rad horiz_rib.rad vert_rib.rad fire_valve.rad breather.oct helmet.oct \
jbox1.rad jbox2.rad meters.rad exting2.oct \
parts/red_box.rad parts/hydrant.rad exting2.oct support_bracket.rad \
applicator.rad applicat_head.rad 
	oconv $(OCOPT) materials.rad ship.rad > ship.oct

cvhatch.oct:	parts/cvhatch.rad parts/latch_handle.rad parts/brass_nut.rad \
parts/latch+nut.rad parts/hinge.pts parts/vert_hatch.rad parts/hatch_rib.rad \
parts/latch_plate.rad parts/hatch.pts parts/shinge.pts parts/vh_shinge.rad
	oconv $(OCOPT) materials.rad \
'!cd parts;xform -n cvhatch -e -s .083333 -rz 90 cvhatch.rad' > cvhatch.oct

ohhatch.oct:	parts/ohhatch.rad parts/links.rad parts/chainlink.rad \
parts/hhatch.rad parts/chain_pole.rad parts/hatch_hook.rad \
parts/hatch_door.rad parts/hatch_valvebase.rad parts/hatch_valve.rad \
parts/handle.rad parts/hatchway.rad parts/hstairs.rad parts/hhandrail.rad
	oconv $(OCOPT) materials.rad \
'!cd parts; xform -n ohhatch -e -t 4 .75 0 -rz 180 -t 67 7 0 ohhatch.rad' \
> ohhatch.oct

ovhatch.oct:	parts/ovhatch.rad parts/brass_nut.rad parts/latch_handle.rad \
parts/latch+nut.rad parts/vert_hatch.rad parts/latch_plate.rad parts/hatch_rib.rad \
parts/hinge.pts parts/shinge.pts parts/hatch.pts parts/vh_shinge.rad
	oconv $(OCOPT) materials.rad \
'!cd parts;xform -n ovhatch -e -s .083333 -rz 90 ovhatch.rad' > ovhatch.oct

stairs.oct:	parts/handrail.rad parts/stairs.rad
	oconv $(OCOPT) materials.rad \
'!cd parts;xform -e -n up_stairs stairs.rad' > stairs.oct

ventbox.oct:	parts/ventbox.rad parts/circ2rect.cal parts/ceiling_vent.rad
	oconv $(OCOPT) materials.rad \
'!cd parts; xform -n ventbox -e ventbox.rad' > ventbox.oct

valve.oct:	parts/valve_indicator.rad parts/valve_unit.rad \
parts/screw.rad parts/control_valve.rad parts/valve.rad parts/valve_box.rad
	oconv $(OCOPT) \
'!cd parts; xform -e valve_unit.rad' > valve.oct

connbox.oct:	parts/connector.rad
	oconv $(OCOPT) \
'!cd parts; xform -n connbox -e -t 0 -.319 0 connector.rad' > connbox.oct

extinguisher.oct:	parts/extinguisher.rad parts/hose.cal
	oconv $(OCOPT) \
'!cd parts; xform -n extinguisher -e -t 0 4 0 -s .08333 extinguisher.rad' \
> extinguisher.oct

cable_rack.oct:	parts/cable_rack.rad parts/cable.cal parts/connector_plug.rad
	oconv $(OCOPT) materials.rad \
'!cd parts; xform -n cable_rack -e -s .08333 cable_rack.rad' > cable_rack.oct

breather.oct:	parts/breather.rad
	oconv $(OCOPT) materials.rad parts/breather.rad > breather.oct

helmet.oct:	parts/helmet.rad
	oconv $(OCOPT) materials.rad parts/helmet.rad > helmet.oct

exting2.oct: parts/exting2.rad 
	oconv $(OCOPT) materials.rad parts/exting2.rad > exting2.oct 
  
