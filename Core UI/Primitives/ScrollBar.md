---
Source Filename: _o_core_ui_scroll_bar
Dependencies: 
Inherit: 
tags:
  - TODO
cssclasses:
  - Atom
---
# TODO
- [ ] Clear suggestion incosistent naming
- [ ] JSDoc
- [ ] converted indent to space
# About
A simple scrollbar with three segment. Note: [[ScrollBar]] is independent and not depends to [[ListItem]]s. You can use [[List View]] to manage both the scroll bar and the list or use the helper method `bind` to change the data used to a custom list.

```
 ^   < top head
 |
|||  < the scroll bar
|||
 |
 |   < the "skeleton"
 | 
 |
 V   < tail
```
# Attributes
| Name           | Type                   | Description                                                                                                                                  |
| -------------- | ---------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| `n`            | `Real`                 | How many item is the on the list.                                                                                                            |
| `per_page`     | `Real`                 | How may item is shown at once                                                                                                                |
| `index`        | `Real`                 | The index of selected item.                                                                                                                  |
| `anchor_index` | `Real`                 | The index of anchor. It is different from `index` it is only moved when the scrollbar is moved. You can say it is the index of the scrollbar |
| `behaviour`    | `Enum.ScrollBehaviour` | How the scroll should behave? `clamp` or `mod`?                                                                                              |

# Methods
| Name          | Parameters | Description                          |
| ------------- | ---------- | ------------------------------------ |
| `bind`              | `Instance`           |                                      |
| `scroll_up`   |            | Decrease index by 1, scrolling up.   |
| `scroll_down` |            | Increase index by 1, scrolling down. |

