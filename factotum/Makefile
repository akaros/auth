# Snoopy from harvey (from Plan 9)
# Rules: keep this simple. Make sure the gcc is in your path and nobody gets hurt.

### Build flags for all targets
#
CFLAGS          = -O2 -std=gnu99 -fno-stack-protector -fgnu89-inline -fPIC -static -fno-omit-frame-pointer -g -Iinclude -Wall -I.
LDFLAGS          =
LDLIBS         = -L$(AKAROS)/install/x86_64-ucb-akaros/sysroot/usr/lib -lpthread -lbenchutil -lm -liplib -lndblib -lvmm -lbenchutil
DEST	= $(AKAROS)/kern/kfs/bin

### Build tools
# 
CC=x86_64-ucb-akaros-gcc
AR=x86_64-ucb-akaros-ar
ALL=factotum
FILES= \
confirm.c \
fs.c \
httpdigest.c \
log.c \
p9any.c \
p9cr.c \
p9sk1.c \
pass.c \
rpc.c \
rsa.c \
secstore.c \
util.c \

NO=\
apop.c \
chap.c \
wep.c\

# compilers are fast. Just rebuild it each time.
all: $(FILES)
	$(CC) $(CFLAGS) $(LDFLAGS) -o snoopy $(FILES) $(LDLIBS)

netinstall: $(ALL)
	scp $(ALL) skynet:

y.tab.c: y.tab.h 

y.tab.h: filter.y
	yacc --defines filter.y

install: all
	echo "Installing $(ALL) in $(DEST)"
	cp $(ALL) $(DEST)

clean:
	rm -f $(ALL) *.o



