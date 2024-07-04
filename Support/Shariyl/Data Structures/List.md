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
- [ ] isi methods
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
> Element akhir

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

var size = generic_list.size();
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
> Fungsi pengganti aksesor dari 

### Example
   
```js
// TODO: Unimplemented
```

---
## `last`

### Parameters
| Name | Type | Description |
| ---- | ---- | ---- |
|  |  |  |
|  |  |  |
### Returns 
> `Any` 

### Description
> What

### Example
   
```js
// TODO: Unimplemented
```

---

## `first`

### Parameters
| Name | Type | Description |
| ---- | ---- | ---- |
|  |  |  |
|  |  |  |
### Returns 
> `Any` 

### Description
> What

### Example
   
```js
// TODO: Unimplemented
```

---

## `is_not_empty`

### Parameters
| Name | Type | Description |
| ---- | ---- | ---- |
|  |  |  |
|  |  |  |
### Returns 
> `Any` 

### Description
> What

### Example
   
```js
// TODO: Unimplemented
```

---

## `is_empty`

### Parameters
| Name | Type | Description |
| ---- | ---- | ---- |
|  |  |  |
|  |  |  |
### Returns 
> `Any` 

### Description
> What

### Example
   
```js
// TODO: Unimplemented
```

---

## `foreach`

### Parameters
| Name | Type | Description |
| ---- | ---- | ---- |
|  |  |  |
|  |  |  |
### Returns 
> `Any` 

### Description
> What

### Example
   
```js
// TODO: Unimplemented
```

---

## `cleanup`

### Parameters
| Name | Type | Description |
| ---- | ---- | ----------- |
|      |      |             |
|      |      |             |
### Returns 
> `Any` 

### Description
> What

### Example
   
```js
// TODO: Unimplemented
```

---



# Events