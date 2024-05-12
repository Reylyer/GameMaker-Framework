---
Source Filename: sc_access_helper
Dependencies: 
Inherit: 
tags:
  - POSSIBLE_TO_EXPAND
cssclasses:
  - Atom
---
# About
 Helper function for accessing some native data structures with safe check. If the key is exist, return the value, else return `pointer_null`. It will be treated same as `false` if used in Boolean expression. Thus, you can safe access in one line like this:

```js
var val = st_safe_access(st, "x") ?? "KEY IS NOT EXIST";
```

# Provides
## Functions
### `st_safe_access`

#### Parameters
- `_struct`: `Struct`
   > Struct that want to be accessed
- `_key`: `String`
   > The key to be used to access the struct

#### Returns 
> `Any` or `pointer_null` if key doesn't exist (can be treated as `false`)

#### Description
> Giving a way to safely access structs without crashing the game

#### Example
   
```js
var arbitrary_struct = {
    member : 123
};

// val will be pointer_null instead of throwing error
var val = st_safe_access(arbitrary_struct, "x") ?? "KEY IS NOT EXIST";

// simple if struct has member
val = st_safe_access(arbitrary_struct, "member");
if (val) {
    // do something
}
```

---
### `mp_safe_access`

#### Parameters
- `_map`: `ds_map` 
   > Map that want to be accessed
- `_key`: `String` 
   > The key to be used to access the struct

#### Returns 
> `Any` or `pointer_null` if key doesn't exist (can be treated as `false`)

#### Description
> Giving a way to safely access maps without crashing the game

#### Example
   
```js
var arbitrary_map = ds_map_create();
arbitrary_map[? "member"] = 123;
  
// val will be pointer_null instead of throwing error
var val = mp_safe_access(arbitrary_map, "x") ?? "KEY IS NOT EXIST";

// simple if map has member
val = mp_safe_access(arbitrary_map, "member");
if (val) {
    // do something
}
```

---

