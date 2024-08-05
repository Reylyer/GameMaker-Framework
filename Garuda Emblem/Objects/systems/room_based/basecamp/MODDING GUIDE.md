Ada 3 major step yang perlu ditambahkan untuk menambahkan mod. Untuk sekarang hanya bisa boolean toggle, untuk jenis lain seperti mod config dan nilai kontinu dijadwalkan untuk dikembangkan

## Registering Event
![[Pasted image 20240805212702.png]]
lokasi: `obj_mod_controller`:`create`
Untuk menambah mod, pertama kita akan membuat [[Event Broker|event]] di objek `obj_mod_controller` dan sebuah variable toggle untuk flag mod aktif atau tidak.

## Registering UI

![[Pasted image 20240805212543.png]]
lokasi: `obj_list_menu_training_mod`:`User Event 0`
Untuk register UI (menambahkan di item list), seperti list di bagian lain, kita cukup mengedit User Event 0 menggunakan method add_element. Untuk item mod, kita perlu menyediakan:

- `name` : untuk nama yang ditampilkan di item
- `on_toggle_emit_event`: event yang kita buat di [[]] tadi

## Handling mod

![[Pasted image 20240805212713.png]]
lokasi: `obj_mod_controller`:`step`