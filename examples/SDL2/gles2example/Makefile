#
# SDL application Makefile
# type without args to build
# type run to execute
# type clean to clean sources
# type log to check application log
#



TARGET = gles2example

all: $(TARGET)

TERMUX_PREFIX = /data/data/com.termux/files/usr

CFLAGS = -Os -fPIC -Wall -DANDROID -I${TERMUX_PREFIX}/include

CXXFLAGS = $(CFLAGS)

LDFLAGS = -shared -L${TERMUX_PREFIX}/lib -lSDL2 -lGLESv2 -llog -lm

SDLRUN = am start $(shell am 2>&1| grep -q '\-\-user' && echo '--user 0') -n com.termux.sdl/.TermuxSDLActivity -e sdlmain

OBJS = $(TARGET).o

$(TARGET): $(OBJS)
	$(CC) -o lib$@.so $^ $(LDFLAGS)

clean:
		rm -f $(OBJS) lib$(TARGET).so

run: $(TARGET)
		$(SDLRUN) $(PWD)/lib$(TARGET).so

log:
	logcat -d | grep SDL
