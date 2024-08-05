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
- `on_toggle_emit_event`: event yang kita buat di [[MODDING GUIDE#Registering Event|Registering Event]] tadi
- `bind_value` : Value yang dibind, dalam hal ini flag yang kita buat di [[MODDING GUIDE#Registering Event|Registering Event]] tadi. Untuk mendapatkan value perlu menggunakan [[Reference]] sebagai perantara agar bisa membaca runtime value.

## Handling mod

![[Pasted image 20240805212713.png]]
lokasi: `obj_mod_controller`:`step`

Setelah setup binding agar mod aktif atau tidak, kita akan menggunakan bind_value tadi untuk mengeksekusi script mod. Salah satu caranya cukup menggunakan if block menggunakan bind value. Jika ada variable yang persistent selama mod berjalan, bisa mendeclare variable tersebut di `obj_mod_controller` untuk sekarang