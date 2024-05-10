---
Source Filename: o_human
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

## Attributes
| Name                 | Data Type   | Default Value     | Description                                                                       |
| -------------------- | ----------- | ----------------- | --------------------------------------------------------------------------------- |
| vs_set_player_number | Boolean     | `false`           | Untuk ngeset character setelah diset playernumbernya di creation code             |
| v_z                  | Float       | 0                 | Koor logic untuk ketinggian                                                       |
| v_height             |             |                   | Tinggi sprite, untuk menentukan kapan bisa dihit diudara                          |
|                      |             |                   |                                                                                   |
| v_state              | HUMANSTATE  | HUMANSTATE.MOVE   | State dari human                                                                  |
| v_attack_state       | ATTACKSTATE | ATTACKSTATE.NONE  | Attack state dari human                                                           |
| vs_is_passive        | Boolean     | false             | Kondisi sedang mode passive atau mode active                                      |
|                      |             |                   |                                                                                   |
| v_run_speed_init     |             | 8.8 * 1.5         |                                                                                   |
| v_walk_speed_init    |             | 4.5 * 1.5         |                                                                                   |
| v_run_speed          |             | v_run_speed_init  |                                                                                   |
| v_walk_speed         |             | v_walk_speed_init |                                                                                   |
| v_dir                |             | 0                 | Nilai dalam derajat, utk nilai algoritma point direction di sc_player_move (arah) |
| v_spd                |             | 0                 |                                                                                   |
| v_moveX              |             |                   |                                                                                   |
| v_moveY              |             |                   |                                                                                   |
| v_moveZ              |             |                   |                                                                                   |
| v_moveZ_init         |             |                   |                                                                                   |
| v_axis_value_hor     |             |                   |                                                                                   |
| v_axis_value_ver     |             |                   |                                                                                   |
| v_axis_value_hor_2p  |             |                   |                                                                                   |
| v_axis_value_ver_2p  |             |                   |                                                                                   |
| v_alpha_teleport     |             |                   |                                                                                   |
| vs_animasi_teleport  |             |                   |                                                                                   |
| v_dir_balik          |             |                   |                                                                                   |
|                      |             |                   |                                                                                   |
| v_is_not_nabrak      |             |                   |                                                                                   |


//-=-=-	movement variables -=-=-
 = 
 = 
 = 
 = 
 = 					//
 = v_walk_speed		//utk nilai algoritma point direction di sc_player_move (kecepatan)
 = 0					//nilai penggerak utama X kombinasi dari v_spd dan v_dir
 = 0					//nilai penggerak utama Y kombinasi dari v_spd dan v_dir
 = 0					//nilai penggerak utama Z kombinasi dari v_spd dan v_dir
 = -14\*1.5			//Setter v_moveZ ketika human mantul ke destroyed object
 = false	//False berarti analog dilepas / diam
 = false	//False berarti analog dilepas / diam
 = false	//False berarti analog dilepas / diam
 = false	//False berarti analog dilepas / diam
 = 1		// alpha ketika animasi teleport (2 player only)
 = 0		// untuk switch membuat icon character yg sedang teleport
 = 1				// dir hero ketika dia balik lagi dari pintu teleport

//NANTI MAU DIBENERIN !!!!!!!!!!!!!!!!!!!!!
 = false
//!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

//-=-=-	get hit -=-=-
v_get_dmg = 0				// Nilai dari damage setelah dihitung
vt_draw_x = 0				// coordinate untuk draw damage
vt_draw_y = 0				// coordinate untuk draw damage
vt_alarm_dmg_draw = 0		// Utk waktu berapa lama damage keliahatan sampai hilang
vt_dmg_increment = 30		//untuk animasi tulisan damage yg naik ke atas sc_draw_damage
vs_draw_crit = 0			// Trigger draw damage pas critical
vs_hit = false				// Trigger kalau sudah ke hit, ada di tiap2 hitbox
vs_is_dead = false
vt_alarm_hit = 0			// Untuk waktu berapa lama memainkan animasi ke_hit 
vs_air_combo = true			// Untuk switch apakah masih bisa dilanjut hit sebelum kelar udah ditanah
//v_angkat_hit = false		// Untuk trigger bisa lompat setelah ngangkat
//diilangi dan diganti dengan vs_make_hitbox ketika di sc_player_attack
vs_mantul = 0				// Switch kondisi terpantulkan 
vt_alarm_mantul = 0			// Untuk waktu berapa lama nempel tanah ketika terpantul
vt_alarm_recovery = 0		// Untuk waktu bisa recovery, diset ketika ke blow
vs_animasi_fx = 0			// Untuk switch fx2 tertentu
v_unflinch = false			// Switch jika bisa unflinch atau tidak
vs_unflinch_fx = false		// Switch efek unflinch TRUE maka nyala FALSE maka mati
v_block_chance = 0			// Jika di enemy chance untuk ngetrigger action block ketika sc_gethit
vs_block_animasi = 0		// Untuk keperluan animasi block enemy (ada di alarm 2 & animation end)
vs_unflinch_fx_animasi = 0	// Switch efek unflinch value nya sebagai pengganti timeline
vt_move_x_slide = 0			//move nglondor di sc_hitme
vs_mantul_tembok = 0		//ada di object collision tembok pinggir
shake_on = 0				// Dipakai untuk switch di fx getar
x_init = 0					// Dipakai pas fx getar
getarx = 0					// Nilai getar jika shake_on -> dipakai di draw
v_quick_recovery_chance = 0	// Chance untuk enemy bisa quick recovery di udara ketika ke get_blow
v_quick_recovery_chance_init = 0
							// v_quick_recovery_chance di set v_quick_recovery_chance_init

//-=-=-	dead -=-=-
vs_draw_ko = 0				// Trigger untuk draw damage KO saat overkill
vs_give_exp = 0				// Switch jika enemy mati maka give exp 1x


//-=-=- jump -=-=-
v_jump_speed = 19			// Kecepatan ketika jump
v_grav_speed = 0.9			// Nilai yang mengurangi v_jump_speed
v_z_floor = 0				// Nilai v_z dari tanah yang diinjak, jika lantai dasar maka = 0

//-=-=- run -=-=-
v_left_counter = 0			// Ngecek tombol terpejet utk trigger RUN
v_right_counter = 0			// Ngecek tombol terpejet utk trigger RUN
v_up_counter = 0			// Ngecek tombol terpejet utk trigger DASH
v_down_counter = 0			// Ngecek tombol terpejet utk trigger DASH
vt_alarm_run = 0			// Untuk penghitung jeda waktu reset run counter

//-=-=- combo -=-=-
v_combo = 0					// Nilainya menunjukkan state combo atk yang sedang dilakukan
vs_trigger_for_combo = false// Jika TRUE maka tombol yg sama akan memicu combo
vs_can_attack = true		// Switch di sc_attack untuk kondisi bisa attack lagi setelah ng-attack
vs_can_cancel = true		// Switch udah bisa gerak tetapi belum bisa attack lagi setelah ng-attack, contoh akhir combo
vs_make_hitbox = 0
vs_make_sound = 0
v_combo_max = 4				// Nilai maksimum combo
vs_grab_atk = 0				// State attack untuk animasi grab
vs_voice_fx = false;		// Untuk kunci agar suara voice tdk diplay 2x
vs_voice_fx_played = false	// Untuk simpan id dari voice played
vs_run_atk_combo = false	// Trigger utk combo lanjutan dari light runatk

// =-=- skill -=-=
v_skill_roll_chance = 0		// variable yang digunakan utk ng-roll chance dari suatu skill

//-=-=- weapon_condition -=-=-
v_have_weapon = false	//check membawa weapon atau tidak
weapon_atribute = {		
	weapon_id : 0,
	base_dmg : 0,
	durability : 0
}
vs_weapon_hit = 0			// Sama dengan vs_hit tetapi untuk weapon
vt_weapon_charge_atk = 0	// Waktu charge heavy attack weapon


//--PROCEDURE

//AI get touch
v_get_enemy_touch = ds_list_create();
v_num_enemy_touch = 0

## Methods
