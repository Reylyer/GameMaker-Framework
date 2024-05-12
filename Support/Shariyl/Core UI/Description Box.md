---
Source Filename: obj_core_ui_description_box
Dependencies: 
Inherits: "[[Frame]]"
tags:
  - TODO
cssclasses:
  - Atom
aliases:
  - obj_core_ui_description_box
---
# About
A frame that contains a generic container that can be sprite or object; or a sprite and a fancy description text below the container.
# TODO
- [ ] TODO

# Attributes
| Name            | Type                                    | Description                                                                                   |
| --------------- | --------------------------------------- | --------------------------------------------------------------------------------------------- |
| `maximum_lines` | `Real`                                  | Not implemented yet                                                                           |
| `media`         | `Asset.GMSprite` or an `Asset.GMObject` | The media show/played on the upperside of the description box;                                |
| `description`   | `String`                                | The text shown below the media. The text will be wrapped around the width of description box. |
|                 |                                         |                                                                                               |
# Methods

## `set_media`

#### Parameters

| Name     | Type                                 | Description                                  |
| -------- | ------------------------------------ | -------------------------------------------- |
| `_media` | `Asset.GMObject` \| `Asset.GMSprite` | Media yang ditampilkan dalam description box |
### Returns 
> `None`

### Description
> Set media ke description box yang sekaligus handle posisi dan 




