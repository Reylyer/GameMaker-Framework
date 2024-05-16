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
# TODO
- [ ] Nulis dokumentasi
# About

# Attributes
| Name              | Type                                 | Description                                                                                                                                                                                             |
| ----------------- | ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `active_index`    | `Real`                               | Index dalam list yang aktif, nilai akan dalam range 0 - ``                                                                                                                                              |
| `active_anchor`   | `Real`                               | x                                                                                                                                                                                                       |
| `surface_name`    | `string`                             | String yang digunakan sebagai id dari surface yang digunakan                                                                                                                                            |
| `item_list`       | [[List Item\|obj_core_ui_list_item]] | List yang berisikan object object list item, by design elemen dari list ini adalah object [[List Item\|obj_core_ui_list_item]] atau turunannya. **Atribut ini di isi lewat [[#^d48e05\|User Event 0]]** |
| `scrollbar`       | `ScrollBar`                          | ScrollBar dari list ini (jika ada). **Attribut ini memerlukan manual binding**                                                                                                                          |
| `description_box` |                                      |                                                                                                                                                                                                         |
|                   |                                      |                                                                                                                                                                                                         |
|                   |                                      |                                                                                                                                                                                                         |
# Methods

# Events

## User Event 0
Event ini dilakukan untuk mempopulate list. 
## Clean Up
VERY IMPORTANT EVENT! Di event ini akan melakukan cascading destroy. Secara umum List menu akan memanggil destroy kepada tiap object yang berada di `item_list`. Tiap [[List Item]] akan menghandle ketergantungannya juga. Oleh karena itu, jika melakukan inheritance terhadap [[List Menu|Object ini]] tolong hati hati, karena hanya dengan melakukan spam instantiate destroy intantiate destroy akan membuat memory leak yang parah.