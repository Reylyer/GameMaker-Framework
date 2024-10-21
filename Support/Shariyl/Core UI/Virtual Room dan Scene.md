---
Source Filename: obj_core_room_loader, sc_virtual_room_data
Dependencies: 
Inherits: 
tags:
  - TODO
cssclasses:
  - Atom
aliases:
  - Room Loader
  - Virtual Room Data
---
# About
Virtual room merupakan sebuah [[manager]] yang menyediakan cara agar room dapat disusun berdasarkan layer. Untuk per 10/2024, virtual room hanya digunakan untuk kebutuhan UI yang menyediakan virtual space untuk sistem koordinat yang terisolasi dari [[application_surface]]. 

Cara kerja [[Virtual Room dan Scene]]:
1. Buat sebuah virtual room dengan method `obj_core_room_loader.instantiate_virtual_room` dengan param `room_id` dari room yang ingin di instantiate sebagai virtual room
2. Setiap layer yang ada di room akan di ubah menjadi [[Layer Handler]] yang dimana setiap sprite yang ada di dalam layer akan diubah menjadi [[Sprite Handler]]. Sementara untuk layer dalam room yang menginherit dari obj_core_object akan mendapatkan atribut virtual_room yang dapat digunakan untuk menggambar disana. ***warning untuk sekarang pastikan jika mengguakan layer instance semua object yang memiliki visual menginherit `obj_core_object` agar tampil dengan benar (cth yang tidak memiliki visual: managers)***
3. Untuk layer objects/instances tidak di handle oleh [[Layer Handler]] melainkan oleh gamemaker langsung yang disimpan di `VirtualRoomData.instances_datas`

Untuk memperjelas, room yang ada di step 1 adalah room yang digunakan untuk layer overlay yang disusun lewat room editor. Misal ada room dengan id `rm_overlay_ui_menu` maka panggil `virtual_room = obj_core_room_loader.instantiate_virtual_room(rm_overlay_ui_menu)` untuk melaksanakan step 1.
# TODO
- [ ] TODO
# Attributes

# Methods

# Events