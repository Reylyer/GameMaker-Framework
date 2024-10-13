---
Source Filename: sc_reference
Dependencies: 
Inherits: 
tags:
  - TODO
cssclasses:
  - Atom
aliases:
---
# About
Reference merupakan tipe data buatan yang equivalent dengan pointer di C. Reference dibuat dikarenakan GML merupakan bahasa yang [[Garbage Collected]] yang dapat merusak kestabilan eksekusi program. 

Jika merusak, kenapa dibuat dan dibutuhkan? 

Fungsi utama dari reference adalah untuk membuat satu fungsi yang umum namun memerlukan operasi write ke sebuah variabel yang menjadikannya fungsi masing masing ke setiap variabel yang dilakukan operasi write. Terdengar belibet tapi bisa melihat contoh ini:

```js
/// @param {Real} _value
function ubah_global_a_kuadrat(_value) {
	global.a = _value * _value;
}

/// @param {Real} _value
function ubah_global_b_kuadrat(_value) {
	global.b = _value * _value;
}

/// @param {Real} _value
function ubah_global_c_kuadrat(_value) {
	global.c = _value * _value;
}

var a = 10, b = 12, c = 40;

ubah_global_a_kuadrat(a); // global a adalah 100
ubah_global_b_kuadrat(b); // global b adalah 144
ubah_global_c_kuadrat(c); // global c adalah 1600
```

Dimana masing maisng fungsi sebenarnya melakukan hal yang sama namun untuk variabel yang berbeda saja. Dengan reference ini kita dapat merubah fungsi tersebut menjadi

```js
/// @param {function} _ref
/// @param {Real} _value
function ubah_kuadrat(_ref, _value) {
	_ref(_value * _value);
}

glob_a = reference(global, "a");
glob_b = reference(global, "b");
glob_c = reference(global, "c");

var a = 10, b = 12, c = 40;

ubah_kuadrat(glob_a, a); // global a adalah 100
ubah_kuadrat(glob_b, b); // global b adalah 144
ubah_kuadrat(glob_c, c); // global c adalah 1600
```

contoh usecase lain yang umum adalah mengubah sumber read variable saat runtime
// TODO

```js

```



Terlihat lebih simpel (?) tapi kenapa tipe datanya sebuah function bukan Reference? Ini karena keterbatasan dari GML yang tidak menyediakan style `functor` atau `__callable__` yang membuat reference ini hasil antara seelegan mungkin dan seminimal overhead mungkin. Jika dilihat implementasinya, reference merupakan sebuah fungsi wrapper untuk membuat binding reference ke variabel yang diinginkan.

```js
/// @param {Id.Instance|Id.DsMap|Struct} _target
/// @param {String} _symbol
function reference(_target, _symbol) {
	var _ref = new InternalReference(_target, _symbol);

	obj_core_reference_manager.register(_target, _ref);
	
    return _ref.ref;
}
```

Untuk saat ini yang dapat dilakukan reference adalah struktur data map, structs, dan instance object. Namun ada kasus spesial untuk menggunakan reference untuk function. 
## Function Reference
Function reference merupakan reference spesial yang menggunakan function sebagai sumber dari reference.

Untuk reference function use case utamanya adalah ketika use case yang normal (structs) tapi dilakukan dengan evaluasi fungsi. Use case untuk function reference ini cukup sering ditemukan di dalam [[_Core UI|Core UI]] sebagai generalisasi untuk merubah parent tanpa melakukan perubahan secara langsung. Berikut contoh penggunaan dalam [[List Menu]] agar control naik dan turun bisa diubah tanpa mengubah step event

`obj_core_ui_list_menu`:`create`
```js
// default control
listen_event_scroll_up   = reference_function(self.id, keyboard_check, [vk_up]);
listen_event_scroll_down = reference_function(self.id, keyboard_check, [vk_down]);
```
`obj_core_ui_list_menu`:`step`
```js
if (active_index > 0 && listen_event_scroll_up()) {
	...
	event_scroll_up.emit();
}

if (active_index < ds_list_size(item_list) - 1 && listen_event_scroll_down()) {
	...
	event_scroll_down.emit();
}
```

jika dilihat, untuk mengecek apakah list perlu bergerak, kita perlu mengevaluasi `listen_event_scroll_xxx()` yang berada di dalam step parent event (dilihat dari child saat melakukan inherit). Kita tidak dapat merubah ekspresi boolean tersebut secara langsung jika misal menggunakan pengecekan biasa, contoh `keyboard_check(vk_up)`. Penambahan variable key tidak cukup karena jika kita menggunakan fungsi yang lebih kompleks, misal keyboard dan gamepad maka kita memerlukan cara lain untuk menghandle itu. Maka dari itu `reference_function` datang membantu untuk menyelesaikan masalah ini. Kita dapat menginherit parent dan misal mengganti event dengan event lain seperti penggunaan pada `obj_list_menu_training_mod` pada Garuda Emblem
```js
listen_event_scroll_up   = obj_training_controller.event_input_menu_select_up.subscribe_as_reference();
listen_event_scroll_down = obj_training_controller.event_input_menu_select_down.subscribe_as_reference();
```

`obj_list_menu_training_mod` menggunakan konsep lain dari [[Event Broker]] yang menggunakan event sebagai sumber reference function dimana terdapat pengecekan input untuk sistem list dan objek ini menggunakan event tersebut untuk menggerakan list `obj_list_menu_training_mod` 

Mirip dengan reference biasa, `reference_function` merupakan wrapper dari internal struct `FunctionReference`. `reference_function` dipisah sebagai fungsi yang berbeda bernama `reference_function` 

```js
function reference_function(_id, _func, _args=[]) {
	var _ref = new FunctionReference(_func, _args);
	
	obj_core_reference_manager.register_function(_id, _ref);
	
	return _ref.ref;
}
```

# TODO
- [ ] Enforce Clean up atau implementasi Garbage Collection assistant 
# Attributes

# Methods

# Events