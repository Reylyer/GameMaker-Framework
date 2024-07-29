---
Source Filename: obj_core_ui_list_menu
Dependencies: "[[_Core UI]]"
Inherits: "[[Frame|obj_core_ui_frame]]"
tags:
  - TODO
cssclasses:
  - Atom
aliases:
  - List View
  - List Menu
  - obj_core_ui_list_menu
---
You may also want to see
- [[List Menu 2D]]
- [[Window Tabs]]
# About
List menu merupakan object UI yang menyimpan list satu dimensi. [[List Menu|obj_core_ui_list_menu]] di desain untuk menghandle item yang disusun secara tumpukan/vertikal.

Secara umum List Menu disusun seperti ini
![[List Menu.png]]

# TODO
- [ ] Nulis dokumentasi
- [ ] Contoh modifikasi
- [ ] alternative lain 

# Attributes
| Name                      | Type                                 | Description                                                                                                                                                                                             |
| ------------------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `active_index`            | `Real`                               | Index dalam list yang aktif, nilai akan dalam range 0 - ``                                                                                                                                              |
| `active_anchor`           | `Real`                               | x                                                                                                                                                                                                       |
| `surface_name`            | `string`                             | String yang digunakan sebagai id dari surface yang digunakan                                                                                                                                            |
| `item_list`               | [[List Item\|obj_core_ui_list_item]] | List yang berisikan object object list item, by design elemen dari list ini adalah object [[List Item\|obj_core_ui_list_item]] atau turunannya. **Atribut ini di isi lewat [[#^d48e05\|User Event 0]]** |
| `scrollbar`               | `ScrollBar`                          | ScrollBar dari list ini (jika ada). **Attribut ini memerlukan manual binding**                                                                                                                          |
| `description_box`         |                                      |                                                                                                                                                                                                         |
| `list_item_default_class` | `Asset.GMObject`                     |                                                                                                                                                                                                         |
|                           |                                      |                                                                                                                                                                                                         |
# Methods
## `add_element`
TODO refactor, let the list item construct itself and handle it rather than this class, more generic and no need to create object to inherit the menu and the item list
### Parameters
| Name          | Type             | Description                                                 |
| ------------- | ---------------- | ----------------------------------------------------------- |
| `_data`       | `Id.Struct`      | Data yang perlu untuk membuat sebuah item list              |
| `_item_class` | `Asset.GMObject` | Class object yang digunakan untuk menginstantiate list baru |
### Returns 
>  `Mixin` type of `_item_class`

### Description
> Method ini digunakan untuk menambah element `list_menu` yang dapat menghandle berbagai macam varian `list_item` sesuai dengan `_item_class` yang diberikan

### Example
   
```js
var _c1 = self.add_element(
	"Quick Combo",
	"Basic quick combo. Good for starting a combo or extend any combos that possible.",
	obj_example_farid
)
generic_ui_text(_c1, [_light_attack_sprite,]);
```

---


# Events

## User Event 0
Event ini dilakukan untuk mempopulate list. 
## Clean Up
VERY IMPORTANT EVENT! Di event ini akan melakukan cascading destroy. Secara umum List menu akan memanggil destroy kepada tiap object yang berada di `item_list`. Tiap [[List Item]] akan menghandle ketergantungannya juga. Oleh karena itu, jika melakukan inheritance terhadap [[List Menu|Object ini]] tolong hati hati, karena hanya dengan melakukan spam instantiate destroy intantiate destroy akan membuat memory leak yang parah.

## [[Event Broker|Custom Events]]

