# Pic Usb Servo
# USB connected device which controls a servo
# Makefile, creates PicUsbServo.hex file from sources
#
# Copyright (C) 2013 Holger Oehm
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

OBJECTS=descriptor.o wait.o servo.o main.o

%.o : %.asm
	gpasm -c -p p18f13k50 -r dec -w 2 -I ../firmware/18f13k50 $<

all: PicUsbServo.hex

PicUsbServo.hex: $(OBJECTS)
	gplink -o PicUsbServo.hex -a inhx32 -m -I ../firmware/18f13k50 usb.o $(OBJECTS) -s 18f13k50_bootloader.lkr
	@test -f PicUsbServo.hex || ( echo gplink failed; exit 1 )

clean:
	rm -f *.o *.map *.lst *.cod *.hex

.PHONY: all clean
