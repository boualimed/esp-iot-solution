# Component: led

* This component defines an led as a well encapsulated object.

* An led device is defined by:
	* `GPIO number` on which the led is attached
	* `dark_level` which decided by peripheral hardware

* An led device can provide:
	* `LED_OFF`, `LED_ON`, `LED_QUICK_BLINK` and `LED_SLOW_BLINK` four states which can be set by calling led_state_write()
	* `LED_NORMAL_MODE` and `LED_NIGHT_MODE` two modes which can be set by calling led_mode_write()
	* led_state_read() or led_mode_read() can be called to get the current state or mode of the led
    * led_update_blink_freq() can be called to change the blink frequency of all the leds
    * led_night_duty_write() can be called to set the duty of led in night mode

* To use the led device, you need to:
	* call led_setup to initialize ledc timers and set the frequency of quick_blink and slow_blink
	* create a led device object by led_create()
	* to free the led object, you can call led_delete() to delete the object and free the memory

### NOTE:
> `LEDC_TIMER_0`, `LEDC_TIMER_1` and `LEDC_TIMER_2` has been `used` by this module.

> `LEDC_CHANNEL_0`, `LEDC_CHANNEL_1`, `LEDC_CHANNEL_2`, `LEDC_CHANNEL_3` has been `used` by this module.

> Don't call led_delete() `more than once` for the same led_handle and you'd better to set the led_hanle to `NULL` after `led_delete`. 
