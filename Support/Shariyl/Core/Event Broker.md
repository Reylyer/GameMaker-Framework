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

`obj_subscribe_emit_event`:`create`
```js
function on_event_example_emitted() {
	show_debug_message("Terpanggil");
}


event_broker.subscribe_event_emittable("EVENT_EMIT_EXAMPLE");

// or

obj_will_emit_event.event_example.subscribe
```

---
*Pada umumnya*, event emitter akan mendaftarakan eventnya terlebih dahulu. Ada kalanya event subscriber akan meregister callback terlebih dahulu sebelum emitter mendaftarkan eventnya. Pada kejadian tersebut, event akan dibuat sekaligus mendaftarkan callbacknya. Ketika emitter akan mendaftarkan eventnya, broker akan memberikan eventnya tanpa membuat yang baru.
# Attributes

# Methods

# Events
