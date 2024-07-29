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

*Pada umumnya*, event emitter akan 

# TODO
- [ ] 
# Attributes

# Methods

# Events
