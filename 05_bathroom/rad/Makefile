# usage:
# make clobber
# make -j 5 all

PATCHED_FILES = \
bathroom.rad \
skylight_night.rad \
lib/shdoor_frame.rad \
lib/shdoor_outer.rad \
lib/bathfauc.rad \
lib/door.rad \
lib/sinkfauc.rad \
lib/sinkspig.rad \
lib/vanity.rad \
lib/medcab.rad \
lib/lamp_holder.rad \
lib/vanfixt.rad \
lib/towel_rack_bracket.rad \
lib/towel_rack.rad \
lib/flushand.rad \
lib/toilet.rad

OBJECTS = bathroom.rad lib/sinkfauc.rad lib/sinkspig.rad lib/bathfauc.rad \
lib/toilet.rad lib/flushand.rad lib/medcab.rad lib/vanity.rad lib/basin.cal \
lib/sinkspig.rad lib/vanfixt.rad lib/lamp_holder.rad lib/door.rad \
lib/towel_rack.rad lib/towel_rack_bracket.rad

all: \
pics/bathroom_radiance_mir.png \
pics/bathroom_radiance_shwin.png \
pics/bathroom_radiance_sink.png \
pics/bathroom_radiance_stall.png \
pics/bathroom_radiance_van.png

clean:
	-rm -f *~ lib/*~ *.amb *.oct *.sh pics/*.tiff pics/*.hdr

clobber: clean
	-rm -f pics/*.png
	git checkout $(PATCHED_FILES)

blender: apply_patches

apply_patches: \
bathroom.patch \
skylight_night.patch \
lib/shdoor_frame.patch \
lib/shdoor_outer.patch \
lib/bathfauc.patch \
lib/door.patch \
lib/sinkfauc.patch \
lib/sinkspig.patch \
lib/vanity.patch \
lib/medcab.patch \
lib/lamp_holder.patch \
lib/vanfixt.patch \
lib/towel_rack_bracket.patch \
lib/towel_rack.patch \
lib/flushand.patch \
lib/toilet.patch
	patch bathroom.rad -i bathroom.patch
	patch skylight_night.rad -i skylight_night.patch
	patch lib/shdoor_frame.rad -i lib/shdoor_frame.patch
	patch lib/shdoor_outer.rad -i lib/shdoor_outer.patch
	patch lib/bathfauc.rad -i lib/bathfauc.patch
	patch lib/door.rad -i lib/door.patch
	patch lib/sinkfauc.rad -i lib/sinkfauc.patch
	patch lib/sinkspig.rad -i lib/sinkspig.patch
	patch lib/vanity.rad -i lib/vanity.patch
	patch lib/medcab.rad -i lib/medcab.patch
	patch lib/lamp_holder.rad -i lib/lamp_holder.patch
	patch lib/vanfixt.rad -i lib/vanfixt.patch
	patch lib/towel_rack_bracket.rad -i lib/towel_rack_bracket.patch
	patch lib/towel_rack.rad -i lib/towel_rack.patch
	patch lib/flushand.rad -i lib/flushand.patch
	patch lib/toilet.rad -i lib/toilet.patch

pics/bathroom_radiance_mir.png: clobber
	rad mir.rif
	ra_tiff pics/mir_cam.hdr pics/bathroom_radiance_mir.tiff
	imf_copy pics/bathroom_radiance_mir.tiff pics/bathroom_radiance_mir.png

pics/bathroom_radiance_shwin.png: clobber
	rad shwin.rif
	ra_tiff pics/shwin_cam.hdr pics/bathroom_radiance_shwin.tiff
	imf_copy pics/bathroom_radiance_shwin.tiff pics/bathroom_radiance_shwin.png

pics/bathroom_radiance_sink.png: clobber
	rad sink.rif
	ra_tiff pics/sink_cam.hdr pics/bathroom_radiance_sink.tiff
	imf_copy pics/bathroom_radiance_sink.tiff pics/bathroom_radiance_sink.png

pics/bathroom_radiance_stall.png: clobber
	rad stall.rif
	ra_tiff pics/stall_cam.hdr pics/bathroom_radiance_stall.tiff
	imf_copy pics/bathroom_radiance_stall.tiff pics/bathroom_radiance_stall.png

pics/bathroom_radiance_van.png: clobber
	rad van.rif
	ra_tiff pics/van_cam.hdr pics/bathroom_radiance_van.tiff
	imf_copy pics/bathroom_radiance_van.tiff pics/bathroom_radiance_van.png
