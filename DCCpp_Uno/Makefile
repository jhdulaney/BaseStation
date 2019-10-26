OBJ := DCCpp_Uno.ino

serial-port := /dev/ttyUSB0

wd != pwd
build-path = $(wd)/build

# Paths for arduino-builder
hardware = /usr/share/arduino/hardware/
tools = /usr/bin/

# Default to human readable logging output
logger := human

uno: builddir
	@echo Building for target $@
	@arduino-builder -hardware $(hardware) -tools $(tools) -fqbn arduino:avr:uno -logger $(logger) -build-path $(build-path) $(wd)/$(OBJ)
	@echo $(build-path)/$(OBJ).hex


uno_upload: uno
	@echo Uploading to Arduino Uno on $(serial-port)
	/usr/bin/avrdude -C/etc/avrdude/avrdude.conf -v -patmega328p -carduino -P$(serial-port) -b115200 -D -Uflash:w:$(build-path)/$(OBJ).hex:i



builddir:
	@echo $@ is $(build-path)
	@mkdir -p $(build-path)


clean:
	@echo $@
	@rm -rf $(build-path)
