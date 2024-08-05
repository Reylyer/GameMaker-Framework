---
Source Filename: 
Dependencies: 
Inherits: 
tags:
  - TODO
cssclasses:
  - Atom
aliases:
  - Custom Events
  - obj_core_system_event_broker
---
\* sedikit glossarium
1. Event: Sebuah peristiwa, contoh: `if (keyboard_check(ord("A")) { // peristiwa }
2. Emit: Sebuah aksi untuk mengumumkan suatu event sedang/telah terjadi
3. Callback: Fungsi yang akan dipanggil ketika suatu event terjadi
4. Event Publisher / Provider / Emitter: Sesuatu yang akan meng-emit event | \*ada alasan kenapa menggunakan *sesuatu* bukan *objek*
5. Event Poller / Subscriber: Sesuatu yang mendaftarkan fungsi yang akan dipanggil
6. Event Broker: Objek yang menghandle pembuatan event, pendaftaran callback, pemanggilan callback, hingga cleanup event
# About
Event broker merupakan core system dari modul Support/Shariyl. Event broker menyediakan cara untuk para developer agar dapat menggunakan event-based style code. System ini mirip dengan pola [pub/sub](https://en.wikipedia.org/wiki/Publish%E2%80%93subscribe_pattern) pada umumnya yang di implementasikan pada redis, gcp, dan beberapa framework umum yang menggunakan pattern asyncronous event based.

Secara umum, event broker memiliki interaksi antar komponennya sebagai berikut

![[Poll and Emit.png]]
Alur pada umumnya dapat dilihat sebagai berikut

![[Event Broker.png]]


\
Example real usecase:
`obj_will_emit_event`:`create`
```js
event_example = event_broker.register_event_emittable("EVENT_EMIT_EXAMPLE");
listen_keypress = reference_function(self.id, keyboard_check, [vk_enter]);
```
`obj_will_emit_event`:`step`
```js
if (listen_keypress()) {
	event_example.emit();
}
```
read [[Reference#Function Reference|Function Reference]] for learn about `reference_function`

`obj_subscribe_emit_event`:`create`
```js
function on_event_example_emitted() {
	show_debug_message("Terpanggil");
}

// -----------------------------------------------------------------

event_broker.subscribe_event_emittable(self.id, "EVENT_EMIT_EXAMPLE", on_event_example_emitted);

// or

obj_will_emit_event.event_example.subscribe(self.id, on_event_example_emitted);

// either will do and the function will called
```

---
*Pada umumnya*, event emitter akan mendaftarakan eventnya terlebih dahulu. Ada kalanya event subscriber akan meregister callback terlebih dahulu sebelum emitter mendaftarkan eventnya. Pada kejadian tersebut, event akan dibuat sekaligus mendaftarkan callbacknya. Ketika emitter akan mendaftarkan eventnya, broker akan memberikan eventnya tanpa membuat yang baru.
# Attributes

# Methods

# Events



# Bug Logs
## White Screen Freeze saat self subscribe event
![[Pasted image 20240805182138.png]]
Bug ini muncul ketika ada sebuah objek yang menyediakan event, kemudian melakukan subscribe ke event tersebut. Hasilnya adalah saat di debug/run game akan stuck di layar putih not responding.

Jika dilihat dari output log, pesan terakhir yang disampaikan adalah

```
Done ObjectLists
Done Extension_Initialize
About to startroom
```

Setelah diidentifikasi, masalahnya terlalu sederhana sampai sangat menjengkelkan. Bug ini disebabkan oleh Struct yang ditaruh di dalam objek [[Event Broker|obj_core_system_event_broker]] seperti ini

![[Pasted image 20240805182550.png]]

Hipotesis dari bug ini adalah Order of Execution dari gamemaker yang dimana beberapa objek tidak dapat melakukan reference ke struct ini untuk objek yang dibuat (di dalam IDE) setelah [[Event Broker|obj_core_system_event_broker]] ini dibuat. Tapi sepertinya hipotesis ini tidak cukup sempurna. Dengan hipotesis ini solusi yang terpikir utama adalah mengeluarkan struct ini dari objek ke dalam sebuah script dan entah kenapa dengan memindahkannya ke script menyelesaikan masalah tersebut...
