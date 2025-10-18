# How to use: 
1. Establish a SSH connection to your printer

2. Move to your folder directory, that's typically in ~/pinter_data/config

    ```bash
    cd ~/printer_data/config
    ```

3. Download the `shutdown_delay.sh` file using the command below:

    ```bash
    wget https://github.com/thomasfjen/Klipper_MISC/blob/main/safe_power_off_tasmota/shutdown_delay.sh

4. Change the permission so the script can be executed
    ``` bash
    chmod +x shutdown_delay.sh
5. Change the IP of your Tasmota plug to the file and if disered change the delay time
    ````bash
    sudo nano shutdown_delay.sh
6. Add macros to your configs or download tasmota_shutdown.cfg and include it in your config
    ````bash
    [gcode_shell_command delay_shutdown_tasmota]
    command: ~/printer_data/config/shutdown_delay.sh
    timeout: 30
    verbose: True

    [gcode_macro _TASMOTA_SHUTDOWN]
    description: calls shutdown shell script
    gcode:
        RUN_SHELL_COMMAND CMD=delay_shutdown_tasmota

    [gcode_macro SHUTDOWN]
    gcode:
        _TASMOTA_SHUTDOWN
        {action_call_remote_method("shutdown_machine")}

7. DONE! If you call the `Shutdown` a shutdown with delay request will be send to the Tasmota plug, after that the pi shuts down
