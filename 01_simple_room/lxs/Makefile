all: \
simple_room_cam1.lxs \
simple_room_cam2.lxs \
simple_room_cam3.lxs \
simple_room_cam4.lxs

clean:
	-rm -f *~ simple_room_cam?.lxs 

clobber: clean
	-rm -f *.png

simple_room_cam1.lxs: simple_room.lxs
	-cp simple_room.lxs simple_room_cam1.lxs

simple_room_cam2.lxs: simple_room.lxs simple_room_cam2.patch
	patch simple_room.lxs -i simple_room_cam2.patch -o simple_room_cam2.lxs

simple_room_cam3.lxs: simple_room.lxs simple_room_cam3.patch
	patch simple_room.lxs -i simple_room_cam3.patch -o simple_room_cam3.lxs

simple_room_cam4.lxs: simple_room.lxs simple_room_cam4.patch
	patch simple_room.lxs -i simple_room_cam4.patch -o simple_room_cam4.lxs
