---
Source Filename: obj_core_room_loader, sc_virtual_room_data
Dependencies: 
Inherits: 
tags:
  - TODO
cssclasses:
  - Atom
aliases:
---
# About
Virtual room merupakan sebuah game manager yang menyediakan cara agar room dapat disusun berdasarkan layer. Untuk per 10/03/2024, virtual room hanya digunakan untuk kebutuhan UI yang menyediakan virtual space untuk sistem koordinat yang terisolasi dari [[application_surface]]. 

Cara kerja [[Virtual Room]]:
1. Buat virtual room dengan method `obj_core_room_loader.instantiate_virtual_room` dengan param `room_id` dari virtual room yang ingin di instantiate
2. Setiap layer yang ada di room akan di ubah menjadi [[Layer Handler]] yang dimana setiap sprite yang ada di dalam layer akan diubah menjadi [[Sprite Handler]]. Sementara untuk layer dalam room yang menginherit dari obj_core_object akan mendapatkan atribut virtual_room yang dapat digunakan untuk menggambar disana. !warning untuk sekarang pastikan jika mengguakan layer instance semua object yang memiliki visual menginherit `obj_core_object` agar tampil dengan benar (cth yang tidak memiliki visual: managers)
# TODO
- [ ] TODO
# Attributes

# Methods

# Events