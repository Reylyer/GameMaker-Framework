---
Source Filename: sc_datra_structure_list
Dependencies: 
Inherits: 
tags:
  - TODO
cssclasses:
  - Atom
aliases:
---
# About


# TODO
- [ ] Bikin abourt
- [x] isi methods
# Attributes

| Name   | Type      | Description                   |
| ------ | --------- | ----------------------------- |
| `data` | `Id.List` | Container wrapper untuk list. |
# Methods
## `add`

### Parameters
| Name     | Type | Description                                 |
| -------- | ---- | ------------------------------------------- |
| _element | Any  | Element yang akan ditambahkan ke akhir list |
### Returns 
> `None` 

### Description
> Menambahkan sebuah element ke akhir list

### Example
   
```js
var generic_list = new List();

generic_list.add("a");
generic_list.add(1);
generic_list.add(3.5);

// hasil akhir generic_list
// [ "a", 1, 3.5]
```

---

## `push`

### Description
> Alias dari [[List#`add`|add]]

---

## `append`

### Description
> Alias dari [[List#`add`|add]]

---

## `pop`

### Parameters
No param
### Returns 
> `Any`

### Description
> Melakukan penghapusan element di akhir list sekaligus mengembalikannya sebagai return value

### Example
   
```js
var generic_list = new List();

generic_list.add("a");
generic_list.add(1);
generic_list.add(3.5);

var last = generic_list.pop();

// hasil akhir generic_list
// [ "a", 1]
// last == 3.5
```

---

## `size`

### Parameters
No param
### Returns 
> `Real` 

### Description
> Mendapatkan size dari list

### Example
   
```js
var generic_list = new List();

generic_list.add("a");
generic_list.add(1);
generic_list.add(3.5);

var size = generic_list.size(); // size is 3
```

---

## `at`

### Parameters
| Name     | Type   | Description                    |
| -------- | ------ | ------------------------------ |
| `_index` | `Real` | Index list yang ingin di akses |
### Returns 
> `Any` 

### Description
> Fungsi pengganti aksesor `[| _index]` untuk tipe data buatan ini

### Example
   
```js
var generic_list = new List();

generic_list.add("a");
generic_list.add(1);
generic_list.add(3.5);

var second_element = generic_list.at(1); // second_element is 1
```

---
## `last`

### Parameters
No param

### Returns 
> `Any` 

### Description
> Menggambil data element terakhir dari list, berbeda dengan [[List#`pop`|pop]], fungsi ini tidak menghapus element terakhir
### Example
   
```js
var generic_list = new List();

generic_list.add("a");
generic_list.add(1);
generic_list.add(3.5);

var last_element = generic_list.last(); // last_element is 3.5
```

---

## `first`

### Parameters
No param

### Returns 
> `Any` 

### Description
> Menggambil data element pertama list

### Example
   
```js
var generic_list = new List();

generic_list.add("a");
generic_list.add(1);
generic_list.add(3.5);

var first_element = generic_list.first(); // first_element is "a"
```

---

## `is_not_empty`

### Parameters
No param
### Returns 
> `Bool` 

### Description
> Mengecek apakah list tidak kosong, negasi dari [[List#`is_empty`|is_empty]]

### Example
   
```js
var generic_list = new List();

generic_list.is_not_empty(); // false

generic_list.add("a");

generic_list.is_not_empty(); // true
```

---

## `is_empty`

### Parameters
No param

### Returns 
> `Bool` 

### Description
> Mengecek apakah list kosong, negasi dari [[List#`is_not_empty`|is_not_empty]]

### Example
   
```js
var generic_list = new List();

generic_list.is_not_empty(); // true

generic_list.add("a");

generic_list.is_not_empty(); // false
```

---

## `foreach`

### Parameters
| Name         | Type       | Description                                |
| ------------ | ---------- | ------------------------------------------ |
| `_func`      | `function` | Fungsi yang akan diapply ke setiap element |
| `_parameter` |            | Not implemented yet TODO                   |
### Returns 
> [[List]] 

### Description
> Fungsi yang akan meng-apply fungsi `_func` ke setiap element yang ada di list. Fungsi ini tidak melakukan modifikasi terhadap list aslinya dan akan mereturn [[List]] baru hasil dari kembalian fungsi ke setiap element

### Example
   
```js
var num_list = new List();

num_list.add(10);
num_list.add(1);
num_list.add(3.5);

var squared_list = num_list.foreach(function(_element) {return _element * _element})
```

---

## `cleanup`

### Parameters
No param

### Returns 
> `None` 

### Description
> Handler internal untuk melakukan cleanup dari list yang dibuat

### Example
   
```js
// TODO: Unimplemented
```

---



# Events