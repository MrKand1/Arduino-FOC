# SimpleFOC v2.3.4 as ESP-IDF component

set(SIMPLEFOC_SRCS
    "src/BLDCMotor.cpp"
    "src/StepperMotor.cpp"
    "src/common/time_utils.cpp"
    "src/common/pid.cpp"
    "src/common/lowpass_filter.cpp"
    "src/common/foc_utils.cpp"
    "src/common/base_classes/CurrentSense.cpp"
    "src/common/base_classes/Sensor.cpp"
    "src/common/base_classes/FOCMotor.cpp"
    "src/communication/Commander.cpp"
    "src/communication/SimpleFOCDebug.cpp"
    "src/communication/StepDirListener.cpp"
    "src/sensors/MagneticSensorAnalog.cpp"
    "src/sensors/HallSensor.cpp"
    "src/sensors/GenericSensor.cpp"
    "src/sensors/MagneticSensorPWM.cpp"
    "src/sensors/MagneticSensorSPI.cpp"
    "src/sensors/MagneticSensorI2C.cpp"
    "src/sensors/Encoder.cpp"
    "src/drivers/BLDCDriver3PWM.cpp"
    "src/drivers/BLDCDriver6PWM.cpp"
    "src/drivers/StepperDriver2PWM.cpp"
    "src/drivers/StepperDriver4PWM.cpp"
    "src/drivers/hardware_specific/esp32/esp32_ledc_mcu.cpp"
    "src/drivers/hardware_specific/esp32/esp32_driver_mcpwm.cpp"
    "src/drivers/hardware_specific/esp32/esp32_mcpwm_mcu.cpp"
    "src/current_sense/GenericCurrentSense.cpp"
    "src/current_sense/InlineCurrentSense.cpp"
    "src/current_sense/LowsideCurrentSense.cpp"
    "src/current_sense/hardware_specific/esp32/esp32_adc_driver.cpp"
    "src/current_sense/hardware_specific/esp32/esp32_mcu.cpp"
    "src/current_sense/hardware_specific/esp32/esp32_mcpwm_mcu.cpp"
)

idf_component_register(
    SRCS ${SIMPLEFOC_SRCS}
    INCLUDE_DIRS "src"
    REQUIRES espressif__arduino-esp32
)

# Suppress strict warnings for third-party SimpleFOC library
target_compile_options(${COMPONENT_LIB} PRIVATE
    -Wno-uninitialized
    -Wno-maybe-uninitialized
    -Wno-unused-variable
)
