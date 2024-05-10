Ada beberapa naming convention yang digunakan dalam kode ini

# Naming

## File
Ada beberapa jenis file di GameMaker dan GameMaker memiliki static name checker bernama [[Feather]]. Permasalahan disini adalah [[Feather]] suka ngambek kalau penamaan file tidak mengikuti naming conventionnya. [[Feather]] ini relatif baru dengan Garuda Emblem yang menyebabkan ada 2 macam naming convention yang ada di folder Garuda Emblem ini. Berikut merupakan naming convention yang ada di folder Garuda Emblem

| Type of file | Prefix | Prefix alt        |
| ------------ | ------ | ----------------- |
| Object       | `obj_` | `o_`              |
| Sprite       | `spr_` | `s_`              |
| Room         | `rm_`  | `r_`              |
| Script       | `sc_`  | `script_`, `scr_` |

## Variable / Member / Attribute
Untuk variable ditulis dengan snake case dengan beberapa prefix yang ditambahkan untuk mengetahui cara digunakannya variable tersebut. Berikut beberapa prefix yang digunakan

| Prefix | Description                                                            | Example |
| ------ | ---------------------------------------------------------------------- | ------- |
| `vs_`  | Variabel yang digunakan dalam `switch` statement                       |         |
| `vt_`  | Variabel yang digunakan dalam sebuah animasi (bergantung dengan waktu) |         |
| `v_`   | Variabel yang ketat digunakan                                          |         |
