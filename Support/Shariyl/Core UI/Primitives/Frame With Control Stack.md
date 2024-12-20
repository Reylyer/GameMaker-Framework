---
Source Filename: obj_core_ui_frame_with_control_stack
Dependencies: 
Inherits: "[[Frame|obj_core_ui_frame]]"
tags:
  - POSSIBLE_TO_EXPAND
cssclasses:
  - Atom
aliases:
  - obj_core_ui_frame_with_control_stack
---
# About
Sebuah [[Frame]] spesial yang memiliki sistem control passing, biasa digunakan ketika diperlukan manajemen control yang hanya ada satu bagian saja yang memiliki control. Contohnya adalah nested menu yang memerlukan control passing dari satu menu ke menu lain dan mengembalikan control jika ingin kembali ke menu sebelumnya.

Contoh use case:

Menu A dibuat, lalu dipilih item ke-n dari menu A yang mengespawn menu B.

Menu A sekarang tidak memiliki control dan menu B yang memiliki control.

Menu B ditutup, sekarang menu A yang memiliki control kembali.

Contoh dengan canvas:
![[Frame With Control Stack Explanation.png]]

# Attributes
| Name            | Type     | Description                        |
| --------------- | -------- | ---------------------------------- |
| `control_stack` | [[Support/Shariyl/Data Structures/List]] | List yang menyimpan stack control. |
|                 |          |                                    |
More on [[Frame#Attributes]]

# Methods
| Name                 | Param                                                              | Returns   | Description                                                                  |
| -------------------- | ------------------------------------------------------------------ | --------- | ---------------------------------------------------------------------------- |
| `init_control_stack` |                                                                    |           | Initialize and reset the control stack                                       |
| `push_control`       | [[Frame With Control Stack\|obj_core_ui_frame_with_control_stack]] |           | Get the width of the frame                                                   |
| `pop_control`        |                                                                    |           | Mengembalikan control ke pemilik sebelumnya                                  |
| `is_in_control`      |                                                                    | `Boolean` | Mengecek apakah object ini memiliki control                                  |
| `when_in_control`    |                                                                    |           | Event loop yang dieksekusi ketika `is_in_control` True. **Perlu dioverride** |
More on [[Frame#Methods]]

# Events