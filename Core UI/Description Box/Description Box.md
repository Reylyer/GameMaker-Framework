---
Dependencies: 
Inherit: "[[Frame]]"
---
# About
A frame that contains a generic container that can be sprite or object; or a sprite and a fancy description text below the container.

# Inherits
![[Frame]]

# TODO
- [x] Clear suggestion incosistent naming
- [ ] JSDoc
- [x] converted indent to space

# Attributes
| Name            | Type                                    | Description                                                                                   |
| --------------- | --------------------------------------- | --------------------------------------------------------------------------------------------- |
| `maximum_lines` | `Real`                                  | Not implemented yet                                                                           |
| `media`         | `Asset.GMSprite` or an `Asset.GMObject` | The media show/played on the upperside of the description box;                                |
| `description`   | `String`                                | The text shown below the media. The text will be wrapped around the width of description box. |
|                 |                                         |                                                                                               |
# Methods
| Name | Param | Returns | Description |
| ---- | ---- | ---- | ---- |
| `get_height` |  | `Real` | Get the height of the frame |
| `get_width` |  | `Real` | Get the width of the frame |

