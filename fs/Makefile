AR	=gar
AS	=gas
CC	=gcc
LD	=gld
CFLAGS	=-Wall -O -fstrength-reduce -fcombine-regs -fomit-frame-pointer \
	-mstring-insns -nostdinc -I../include
CPP	=gcc -E -nostdinc -I../include

.c.s:
	$(CC) $(CFLAGS) \
	-S -o $*.s $<
.c.o:
	$(CC) $(CFLAGS) \
	-c -o $*.o $<
.s.o:
	$(AS) -o $*.o $<

OBJS=	open.o read_write.o inode.o file_table.o buffer.o super.o \
	block_dev.o char_dev.o file_dev.o stat.o exec.o pipe.o namei.o \
	bitmap.o fcntl.o ioctl.o tty_ioctl.o truncate.o

fs.o: $(OBJS)
	$(LD) -r -o fs.o $(OBJS)

clean:
	rm -f core *.o *.a tmp_make
	for i in *.c;do rm -f `basename $$i .c`.s;done

dep:
	sed '/\#\#\# Dependencies/q' < Makefile > tmp_make
	(for i in *.c;do $(CPP) -M $$i;done) >> tmp_make
	cp tmp_make Makefile

### Dependencies:
bitmap.o : bitmap.c ../include/string.h ../include/apex/sched.h \
  ../include/apex/head.h ../include/apex/fs.h ../include/sys/types.h \
  ../include/apex/mm.h ../include/apex/kernel.h 
block_dev.o : block_dev.c ../include/errno.h ../include/apex/fs.h \
  ../include/sys/types.h ../include/apex/kernel.h ../include/asm/segment.h 
buffer.o : buffer.c ../include/apex/config.h ../include/apex/sched.h \
  ../include/apex/head.h ../include/apex/fs.h ../include/sys/types.h \
  ../include/apex/mm.h ../include/apex/kernel.h ../include/asm/system.h 
char_dev.o : char_dev.c ../include/errno.h ../include/apex/sched.h \
  ../include/apex/head.h ../include/apex/fs.h ../include/sys/types.h \
  ../include/apex/mm.h ../include/apex/kernel.h 
exec.o : exec.c ../include/errno.h ../include/sys/stat.h \
  ../include/sys/types.h ../include/a.out.h ../include/apex/fs.h \
  ../include/apex/sched.h ../include/apex/head.h ../include/apex/mm.h \
  ../include/apex/kernel.h ../include/asm/segment.h 
fcntl.o : fcntl.c ../include/string.h ../include/errno.h \
  ../include/apex/sched.h ../include/apex/head.h ../include/apex/fs.h \
  ../include/sys/types.h ../include/apex/mm.h ../include/apex/kernel.h \
  ../include/asm/segment.h ../include/fcntl.h ../include/sys/stat.h 
file_dev.o : file_dev.c ../include/errno.h ../include/fcntl.h \
  ../include/sys/types.h ../include/apex/sched.h ../include/apex/head.h \
  ../include/apex/fs.h ../include/apex/mm.h ../include/apex/kernel.h \
  ../include/asm/segment.h 
file_table.o : file_table.c ../include/apex/fs.h ../include/sys/types.h 
inode.o : inode.c ../include/string.h ../include/apex/sched.h \
  ../include/apex/head.h ../include/apex/fs.h ../include/sys/types.h \
  ../include/apex/mm.h ../include/apex/kernel.h ../include/asm/system.h 
ioctl.o : ioctl.c ../include/string.h ../include/errno.h \
  ../include/sys/stat.h ../include/sys/types.h ../include/apex/sched.h \
  ../include/apex/head.h ../include/apex/fs.h ../include/apex/mm.h 
namei.o : namei.c ../include/apex/sched.h ../include/apex/head.h \
  ../include/apex/fs.h ../include/sys/types.h ../include/apex/mm.h \
  ../include/apex/kernel.h ../include/asm/segment.h ../include/string.h \
  ../include/fcntl.h ../include/errno.h ../include/const.h \
  ../include/sys/stat.h 
open.o : open.c ../include/string.h ../include/errno.h ../include/fcntl.h \
  ../include/sys/types.h ../include/utime.h ../include/sys/stat.h \
  ../include/apex/sched.h ../include/apex/head.h ../include/apex/fs.h \
  ../include/apex/mm.h ../include/apex/tty.h ../include/termios.h \
  ../include/apex/kernel.h ../include/asm/segment.h 
pipe.o : pipe.c ../include/signal.h ../include/sys/types.h \
  ../include/apex/sched.h ../include/apex/head.h ../include/apex/fs.h \
  ../include/apex/mm.h ../include/asm/segment.h 
read_write.o : read_write.c ../include/sys/stat.h ../include/sys/types.h \
  ../include/errno.h ../include/apex/kernel.h ../include/apex/sched.h \
  ../include/apex/head.h ../include/apex/fs.h ../include/apex/mm.h \
  ../include/asm/segment.h 
stat.o : stat.c ../include/errno.h ../include/sys/stat.h \
  ../include/sys/types.h ../include/apex/fs.h ../include/apex/sched.h \
  ../include/apex/head.h ../include/apex/mm.h ../include/apex/kernel.h \
  ../include/asm/segment.h 
super.o : super.c ../include/apex/config.h ../include/apex/sched.h \
  ../include/apex/head.h ../include/apex/fs.h ../include/sys/types.h \
  ../include/apex/mm.h ../include/apex/kernel.h 
truncate.o : truncate.c ../include/apex/sched.h ../include/apex/head.h \
  ../include/apex/fs.h ../include/sys/types.h ../include/apex/mm.h \
  ../include/sys/stat.h 
tty_ioctl.o : tty_ioctl.c ../include/errno.h ../include/termios.h \
  ../include/apex/sched.h ../include/apex/head.h ../include/apex/fs.h \
  ../include/sys/types.h ../include/apex/mm.h ../include/apex/kernel.h \
  ../include/apex/tty.h ../include/asm/segment.h ../include/asm/system.h 
