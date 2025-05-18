## Data Types

Each setting accepts a specific data type:

-   `bool`: `true` (YES) or `false` (NO).
-   `int`: Whole numbers (e.g., `1`, `2`).
-   `float`: Decimal numbers (e.g., `1.2`, `1.22`).
-   `double`: Decimal numbers (e.g., `0.20`, `0.99`).
-   `str`: Text.

## Capture

These settings control the object detection window, a small, centered window designed to minimize system load.

-   `capture_method` (`str`): Screen capture method. Choose from:
    -   `duplication_api`
    -   `winrt`
    -   `virtual_camera`
-   `detection_resolution` (`int`): Resolution of the capture window in pixels (e.g., `200` for a 200x200 window).
-   `capture_fps` (`float`): Capture frame rate limit. Set to `0.0` to disable limiting. Higher values increase CPU usage.
-   `capture_use_cuda` (`bool`): Enable CUDA acceleration for screen capturing (requires NVIDIA GPU).
-   `monitor_idx` (`int`): ID of the monitor to capture (`0` for the primary monitor).
-   `circle_mask` (`bool`): Enable a circular overlay mask.
-   `capture_borders` (`bool`): Display frames around the capture window
-   `capture_cursor` (`bool`): Display the mouse cursor during capture
-   `virtual_camera_name` (`str`): Name of the virtual camera.

## Target

-   `body_y_offset` (`float`): Vertical offset from the target's center. `0.00` is the center; negative values shift the aim upwards. Applied when head targeting is disabled or fails.
-   `head_y_offset` (`float`): Vertical offset specifically for head targeting.
-   `ignore_third_person` (`bool`): Ignore third-person players (`true` to ignore).
-   `shooting_range_targets` (`bool`): Enable targeting of objects at shooting ranges.
-   `auto_aim` (`bool`): Automatically target enemies without needing to press a button.

## Mouse Move

-   `dpi` (`int`): Software mouse DPI (dots per inch). Higher values result in faster movement.
-   `sensitivity` (`float`): Multiplier that reduces mouse movement speed (higher value = slower movement).
-   `fovX` (`int`): Horizontal field of view from the game, used to improve aiming accuracy.
-   `fovY` (`int`): Vertical field of view from the game, used to improve aiming accuracy.
-   `minSpeedMultiplier` (`float`): Minimum multiplier for mouse movement speed.
-   `maxSpeedMultiplier` (`float`): Maximum multiplier for mouse movement speed.
-   `predictionInterval` (`float`): Interval for target prediction processing (higher value = faster processing).
-   `snapRadius` (`float`): Inner radius (in pixels) around the target where an extra speed boost is applied for precise aiming.
-   `nearRadius` (`float`): Radius (in pixels) defining a smooth slowdown zone near the target.
-   `speedCurveExponent` (`float`): Exponent ($\alpha$) that shapes the S-curve deceleration ($curve = 1 - (1 - t)^\alpha$). Higher $\alpha$ means gentler braking.
-   `snapBoostFactor` (`float`): Multiplier applied to `minSpeedMultiplier` within the `snapRadius`.
-   `easynorecoil` (`bool`): Enable easy no-recoil functionality.
-   `easynorecoilstrength` (`float`): Amount the crosshair is pulled down when easy no-recoil is enabled.
-   `input_method` (`str`): Method used for mouse input:
    -   `WIN32`
    -   `GHUB`
    -   `ARDUINO`
    -   `KMBOX_B`

## Wind Mouse

-   `wind_mouse_enabled` (`bool`): Enable WindMouse movement for more human-like mouse paths.
-   `wind_G` (`float`): Gravity force pulling the mouse towards the target (higher = stronger lock).
-   `wind_W` (`float`): Wind force adding randomness to movement (higher = more wobble).
-   `wind_M` (`float`): Maximum step size or movement speed.
-   `wind_D` (`float`): Distance threshold where wind and gravity behavior changes for more precise movement.

## Arduino

-   `arduino_baudrate` (`int`): Baud rate for Arduino communication (higher = faster processing).
-   `arduino_port` (`str`): COM port for Arduino (e.g., `COM1`, `COM2`, or `auto` for automatic detection).
-   `arduino_16_bit_mouse` (`bool`): Send 16-bit mouse coordinates (`true` if supported by the mouse). `false` uses 8-bit coordinates.
-   `arduino_enable_keys` (`bool`): Forward button press data from Arduino to trigger auto-targeting.

## Kmbox B

-   `kmbox_b_baudrate` (`int`): Baud rate for KMBOX B communication.
-   `kmbox_b_port` (`str`): COM port for KMBOX B (e.g., `COM1`, `COM2`).

## Mouse shooting

-   `auto_shoot` (`bool`): Enable automatic shooting (may require Arduino, GHUB exploit, or Razer for some games).
-   `bScope_multiplier` (`float`): Adjust the target zone size for automatic shooting (e.g., `2.20` for a larger zone, `0.50` for a smaller zone).

## AI

-   `backend` (`str`): AI inference engine to use:
    -   `TRT`: NVIDIA TensorRT (fastest, requires CUDA).
    -   `DML`: DirectML (works on most GPUs, no CUDA needed).
-   `ai_model` (`str`): Filename of the AI model in the `./models` folder (e.g., `Nova.pt`).
-   `confidence_threshold` (`float`): Minimum confidence level (0.0-1.0) for the AI to target an object (higher = fewer targets).
-   `nms_threshold` (`float`): Non-Maximum Suppression threshold for merging overlapping detections.
-   `max_detections` (`int`): Maximum number of objects to detect per frame.
-   `postprocess` (`str`): Method for parsing the AI model output (`yolo8`, `yolo5`, `yolo9`, `yolo10`, `yolo11`, `yolo12`).
-   `export_enable_fp8` (`bool`): Export the model with FP8 quantization (faster, \~4% accuracy loss, limited GPU support). Disabled by default.
-   `export_enable_fp16` (`bool`): Export the model with FP16 quantization (faster).

## CUDA

-   `use_cuda_graph` (`bool`): 
-   `use_pinned_memory` (`bool`): Enable faster data transfer between CPU and GPU (not supported on all GPUs).

## Optical Flow

Currently under development.

-   `enable_optical_flow` (`bool`): Enable or disable optical flow.
-   `draw_optical_flow` (`bool`): Draw the optical flow in the debug window.
-   `draw_optical_flow_steps` (`int`): Size of the rendering grid for optical flow visualization.
-   `optical_flow_alpha_cpu` (`float`): Alpha channel size during optical flow conversion.
-   `optical_flow_magnitudeThreshold` (`double`): Threshold for optical flow correction.
-   `staticFrameThreshold` (`float`): Threshold to avoid processing identical frames.

## Buttons

Use `None` to deactivate a function. Multiple keys can be assigned (e.g., `RightMouseButton, MiddleMouseButton`). Key presses are registered even when the program is minimized.

-   `button_targeting` (`str`): Key(s) for targeting.
-   `button_shoot` (`str`): Key(s) for the easy anti-recoil shoot function.
-   `button_zoom` (`str`): Key(s) for the easy anti-recoil zoom function.
-   `button_exit` (`str`): Key(s) to exit the program.
-   `button_pause` (`str`): Key(s) to pause the program.
-   `button_reload_config` (`str`): Key(s) to reload the configuration.
-   `button_open_overlay` (`str`): Key(s) to open the overlay (does not work in fullscreen applications).

## Overlay

-   `overlay_opacity` (`int`): Transparency of the overlay (values from `1` to `255`).
-   `overlay_snow_theme` (`bool`): Enable or disable the winter theme for the overlay.
-   `overlay_ui_scale` (`float`): Adjust the global UI scale of the overlay.
