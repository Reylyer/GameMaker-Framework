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

## Attributes
| Name                   | Type                                 | Description                                                  |
| ---------------------- | ------------------------------------ | ------------------------------------------------------------ |
| `active_index`         | `Real`                               | Index dalam list yang aktif, nilai akan dalam range 0 - ``   |
| `active_anchor`        | `Real`                               | x                                                            |
| `surface_name`         | `string`                             | String yang digunakan sebagai id dari surface yang digunakan |
| `item_list` ^item-list | [[List Item\|obj_core_ui_list_item]] |                                                              |
| `scrollbar`            | `ScrollBar`                          | x                                                            |
| `description_box`      |                                      |                                                              |
|                        |                                      |                                                              |
## Methods

## Events

## Clean Up
VERY IMPORTANT EVENT! Di event ini akan melakukan cascading destroy. Secara umum List menu akan memanggil destroy kepada tiap object yang berada di [[List Menu#^item-list|item_list]] `