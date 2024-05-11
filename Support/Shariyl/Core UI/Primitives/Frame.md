---
Source Filename: obj_core_ui_frame
Dependencies: 
Inherit: "[[Debuggable Hover]]"
tags:
  - TODO
cssclasses:
  - Atom
aliases:
  - obj_core_ui_frame
---
# About
A simple frame that can contains an object, sprite, or another frame.
# TODO

# Attributes
| Name | Type | Description |
| ---- | ---- | ---- |
| `x` | `Real` | The x origin, left side. |
| `y` | `Real` | The y origin, upper side. |
| `w` | `Real` | The width of the frame |
| `h` | `Real` | The height of the frame |
| `p1` | `Point2D` | [[Point2D]] of (`x`, `y`) |
| `p2` | `Point2D` | [[Point2D]] of (`x + w`, `y + h`) |
# Methods
| Name | Param | Returns | Description |
| ---- | ---- | ---- | ---- |
| `get_height` |  | `Real` | Get the height of the frame |
| `get_width` |  | `Real` | Get the width of the frame |
| `get_anchor_x` |  | `Real` | Get the x of p1 |
| `get_anchor_y` |  | `Real` | Get the y of p1 |
| `get_center_horizontal` |  | `Real` | Get the center of x axis |
| `get_center_vertical` |  | `Real` | Get the center of y axis |

# Events Summary
## Draw
Draw outline dari frame `(x, y) (x + w, y + h)`

**Inherit** di awal atau di akhir untuk melihat frame

## Draw GUI
Menambah informasi debug saat di hover

**Inherit** secara kondisional jika [[option]] `debug` diset `True` dan menambahkan informasi untuk dilog dengan `ds_list_add(messages, "log here");`
## Step
Update posisi frame jika didrag atau diresize

**Inherit** di awal jika frame dapat digeser atau diresize.

