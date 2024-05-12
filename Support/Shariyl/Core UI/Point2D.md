---
Source Filename: _core_ui_Point2D
Dependencies: 
Inherit: 
tags:
  - TODO
cssclasses:
  - Atom
aliases:
  - _core_ui_Point2D
---
# TODO
- [x] Clear suggestion incosistent naming
- [ ] JSDoc
- [x] converted indent to space
- [ ] documenting methods
# About
A simple 2D point

# Attributes
|Name|Type|Description|
|---|---|---|
|`x` |`Real` |The x component of the point. The x-coordinate of the point in GameMaker is centered at 0, where positive values extend to the right side of the origin.  |
|`y` |`Real` |The y component of the point. The y-coordinate of the point in GameMaker is based on an origin at 0. Unlike a typical Cartesian plane, positive values extend below the x-axis origin.  |
# Methods
## `is_inside`

### Parameters

| Name | Type | Description |
| ---- | ---- | ---- |
| `_p1` | `Point2D` | [[Point2D]] in the upper left |
| `_p2` | `Point2D` | [[Point2D]] in the bottom right |
### Returns 
> `Boolean`

### Description
> This method will return `true` if `self` is within the rectangle defined by `_p1` and `_p2`; otherwise, it returns `false`.

#### Example
   
```js
// copy code here
```

---

## `minus`

### Parameters
| Name | Type | Description |
| ---- | ---- | ---- |
| `_p` | `Point2D` | [Point2D](app://obsidian.md/Point2D) used as translation  |

### Returns 
> `None` 

### Description
> What

#### Example
   
```js
// copy code here
```

---


## `plus`

### Parameters
| Name | Type | Description |
| ---- | ---- | ---- |
| `_p` | `Point2D` | [Point2D](app://obsidian.md/Point2D) used as translation  |

### Returns 
> `None` 

### Description
> What

### Example
   
```js
// copy code here
```

---

## `rminus`

### Parameters
| Name | Type | Description |
| ---- | ---- | ---- |
| `_p` | `Point2D` | [Point2D](app://obsidian.md/Point2D) used as translation  |
### Returns 
> `Point2D` 

### Description
> Unlike [[Point2D#`minus`|minus]], it will create a new [[Point2D]] instead of modifying `self`

### Example
   
```js
// copy code here
```

---

## `rplus`

### Parameters
| Name | Type | Description |
| ---- | ---- | ---- |
| `_p` | `Point2D` | [Point2D](app://obsidian.md/Point2D) used as translation  |
### Returns 
> `Point2D` 

### Description
> Unlike [[Point2D#`plus`|plus]], it will create a new [[Point2D]] instead of modifying `self`

### Example
   
```js
// copy code here
```

---
