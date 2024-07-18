



# Notes

## Old implementation

![[Camera Analysis.png]]

### Problem & Proposed solution
- [ ] Satu objek yang mengurus semua room yang cukup bermasalaha

old code

### Code
```js
if(!instance_exists(obj_slowmo_parent)){
	//Update destination
	if(instance_exists(v_following) and v_following != self){
		if(global.var_player2_character != 0 and instance_exists(obj_player) and !instance_exists(obj_cutscene_camera) and follow_not_hero = false){
			if(global.one_offthe_player_is_dead = false){
				_list = ds_list_create()
				for (var _i = 0; _i < instance_number(obj_player); ++_i){
						_list[|_i] = instance_find(obj_player,_i);
					}
				for (var _i = 0;_i < ds_list_size(_list); _i++){
					if(_list[|_i].v_state = HUMANSTATE.COMEBACK){
						global.one_offthe_player_is_dead = true
					}
				}
				xTo = (_list[|0].x + _list[|1].x)/2
				yTo = (_list[|0].y + _list[|1].y)/2
				invis_wall_kanan.x = x+view_w_half + 35
				invis_wall_kiri.x = x-view_w_half - 35	
			}
			if(global.one_offthe_player_is_dead = true){
				if(instance_exists(invis_wall_kanan)) instance_destroy(invis_wall_kanan)
				if(instance_exists(invis_wall_kiri)) instance_destroy(invis_wall_kiri)
				var _list = ds_list_create()
				for (var _i = 0; _i < instance_number(obj_player); ++_i){
						_list[|_i] = instance_find(obj_player,_i);
					}
				for (var _i = 0;_i < ds_list_size(_list); _i++){
					if(_list[|_i].v_state != HUMANSTATE.DEAD and _list[|_i].v_state != HUMANSTATE.COMEBACK){
						v_following = _list[|_i]
					}
				}
				if (v_following.x > x+var_tetapan)
			    {
			        xTo = v_following.x - var_tetapan
			    }
			    if (v_following.x < x-var_tetapan)
			    {
			        xTo = v_following.x + var_tetapan
			    }
			    yTo = v_following.y;
			}
		}else{
			if (v_following.x > x+var_tetapan)
		    {
		        xTo = v_following.x - var_tetapan
		    }

		 
		    if (v_following.x < x-var_tetapan)
		    {
		        xTo = v_following.x + var_tetapan
		    }
		    yTo = v_following.y;
		}
	}
	
	//update object position
	x += (xTo - x ) / pembagi_x;
	y += (yTo - y) / pembagi_y;
	
	x = clamp(x,v_batas_kiri_cam+buff,v_batas_kanan_cam-buff);
	y = clamp(y,v_batas_atas_cam,v_batas_bawah_cam);
} else {
	if(obj_slowmo_parent.vs_animasi < 2){
		if(instance_exists(target)){
		    if (target.x > x)
		    {
		        xTo = target.x
		    }
		    if (target.x < x)
		    {
		        xTo = target.x
		    }
			yTo = target.y + target.v_z
		}
		//update object position
		x += (xTo - x ) / pembagi_x;
		y += (yTo - y) / pembagi_y*5;
		
		x = clamp(x,v_batas_kiri_cam+buff-view_w_half,v_batas_kanan_cam-buff+view_w_half);
		y = clamp(y,view_h_half+buff,room_height-view_h_half-buff);
	}
	
	
	if(obj_slowmo_parent.vs_animasi = 2){
		xTo = x_zoom_out
		yTo = y_zoom_out
	
		//update object position
		x += (xTo - x ) / pembagi_x/5;
		y += (yTo - y) / pembagi_y*5;
		
		x = clamp(x,v_batas_kiri_cam+buff,v_batas_kanan_cam-buff);
		y = clamp(y,view_h_half+buff,room_height-view_h_half-buff);
	}
}

//screen shake
x += random_range(-shake_remain,shake_remain);
y += random_range(-shake_remain,shake_remain);
shake_remain = max(0,shake_remain-((1/shake_length)*shake_magnitude));

//Update view
camera_set_view_pos(view_camera[0],x-view_w_half,y-view_h_half)
//camera_set_view_size(view_camera[0],o_display_init.ideal_width,o_display_init.ideal_height)


camera_set_view_size(view_camera[0],width_size,height_size)
//surface_resize(application_surface,width_size,height_size)
//display_set_gui_size(display_get_gui_width(),display_get_gui_height())
//display_set_gui_size(1280,720)
```

### Review

Ini tidak bisa digunakan untuk 3 player
```js
xTo = (_list[|0].x + _list[|1].x)/2
yTo = (_list[|0].y + _list[|1].y)/2
```

weird conditioning
```js
if(global.one_offthe_player_is_dead = false){
	...
}
if(global.one_offthe_player_is_dead = true){
	...
}
```

better use event based to inform there is new state
```js
for (var _i = 0;_i < ds_list_size(_list); _i++){
	if(_list[|_i].v_state = HUMANSTATE.COMEBACK){
		global.one_offthe_player_is_dead = true
	}
}
```

Huh 3 DIFFERENT way of CLAMPING?
```js
...
//update object position
	x += (xTo - x ) / pembagi_x;
	y += (yTo - y) / pembagi_y;
	
	x = clamp(x,v_batas_kiri_cam+buff,v_batas_kanan_cam-buff);
	y = clamp(y,v_batas_atas_cam,v_batas_bawah_cam);
} else {
	if(obj_slowmo_parent.vs_animasi < 2){
		...
		
		//update object position
		x += (xTo - x ) / pembagi_x;
		y += (yTo - y) / pembagi_y*5;
		
		x = clamp(x,v_batas_kiri_cam+buff-view_w_half,v_batas_kanan_cam-buff+view_w_half);
		y = clamp(y,view_h_half+buff,room_height-view_h_half-buff);
	}
	
	
	if(obj_slowmo_parent.vs_animasi = 2){
		...
	
		//update object position
		x += (xTo - x ) / pembagi_x/5;
		y += (yTo - y) / pembagi_y*5;
		
		x = clamp(x,v_batas_kiri_cam+buff,v_batas_kanan_cam-buff);
		y = clamp(y,view_h_half+buff,room_height-view_h_half-buff);
	}
}

```
