# Makefile for txtrevise
# ======================
# Requirements to build:
# * Make
# * Python
# * Py2exe (Win) or Freeze (Unix)
# * MSYS (Win)
# * UPX

TARGET = txtrevise
INSTALL_DIR_U = /usr/bin 
INSTALL_DIR_W = /c/dev/bin
FREEZE = /usr/bin/freeze.sh # Shell script for Freeze

make: 
	@echo Build ${TARGET} program
	@echo make py2exe - build py2exe executable
	@echo make freeze - build Freeze Unix exectuable
	@echo make instnix - install Freeze executable
	@echo make instwin - install py2exe executable

py2exe: create_exe.py ${TARGET}.py
	@echo Building executable for Win...
	python create_exe.py py2exe
	rm -r build
	rm dist/w9xpopen.exe
	mv dist/${TARGET}.exe dist/t.exe
	upx -9 -o dist/${TARGET}.exe dist/t.exe
	rm dist/t.exe
	
freeze: ${TARGET}.py
	cp Makefile Makefile.1
	@echo Building executable for Unix-like...
	${FREEZE} ${TARGET}.py
	make
	rm Makefile
	rm -f *.c
	rm -f  *.o
	mv Makefile.1 Makefile
	mv ${TARGET} t
	upx -9 -o ${TARGET} t
	rm -f t

instnix: freeze
	@echo Installing executable...
	mv ${TARGET} ${INSTALL_DIR_U}

instwin: py2exe
	@Echo Installing executable...
	mv ${TARGET} ${INSTALL_DIR_W}
