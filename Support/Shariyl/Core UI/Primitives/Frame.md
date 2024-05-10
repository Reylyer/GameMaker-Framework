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
# Inherits
![[Debuggable Hover]]

# TODO
- [x] Clear suggestion incosistent naming
- [ ] JSDoc
- [x] converted indent to space

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

