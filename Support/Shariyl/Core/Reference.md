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

Terlihat lebih simpel (?) tapi kenapa tipe datanya sebuah function bukan Reference? Ini karena keterbatasan dari GML yang tidak menyediakan style functor atau \_\_callable\_\_ yang membuat reference ini hasil antara se elegan mungkin dan seminimal overhead mungkin. Jika dilihat implementasinya, reference merupakan sebuah fungsi wrapper untuk membuat binding reference ke variabel yang diinginkan.

```js
/// @param {Id.Instance|Id.DsMap|Struct} _target
/// @param {String} _symbol
function reference(_target, _symbol) {

	/// @type {Asset.GMObject.obj_core_reference_manager} 
	static _reference_manager = instance_create_depth(0, 0, 0, obj_core_reference_manager);
	
	var _ref = new InternalReference(_target, _symbol);

	_reference_manager.register(_target, _ref);
	
    return _ref.ref;
}
```

dan InternalReference adalah:
```js
function InternalReference (_target, _symbol) constructor {
	
	target = _target;
	symbol  = _symbol;
			
	if (instance_exists(target) or is_struct(target)) {
		/// @param {Any} _set_value
		ref = function (_set_value = pointer_null) {
			if (_set_value == pointer_null) {
				return target[$ symbol];
			}  else {
				target[$ symbol] = _set_value;
			}
		}
	} else if (ds_exists(target, ds_type_map)) {
		/// @param {Any} _set_value
		ref = function (_set_value = pointer_null) {
			if (_set_value == pointer_null) {
				return target[? symbol];
			} else {
				target[? symbol] = _set_value;
			}
		}
	}
}
```

Untuk saat ini yang dapat dilakukan reference adalah struktur data map, structs, dan instance object.

# ToDo
- [ ] Enforce Clean up atau implementasi Garbage Collection assistant 
# Attributes

# Methods

# Events