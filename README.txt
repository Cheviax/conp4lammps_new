-------------1-------------
[0] apt-get update
[0] apt-get upgrade
[1] apt-get install gcc
[2] apt-get install g++
[3] apt-get install gfortran
[4] apt-get install make
[5] apt-get install libfftw*
[6] apt-get install mpi-default*
[7] apt-get install libpng*
[8] apt-get install libjpeg*

[7], [8] 装不上无所谓

-------------2-------------
[1] wget http://www.netlib.org/lapack/lapack-3.7.0.tgz
[2] tar -zxvf lapack-3.7.0.tgz
[3] cd lapack*
[4] cp make.inc.example make.inc
[5] 修改 Makefile：	lib: lapacklib tmglib
		#lib: blaslib variants lapacklib tmglib
		↓
		#lib: lapacklib tmglib
		lib: blaslib variants lapacklib tmglib
[6] ulimit -s unlimited
[7] sudo make -jN
[8] 修改 Makefile.mpi：LINKFLAGS, LIB: 替换lapack目录

lapack-3.7.0.tgz 可以(?)换成其他版本
[7] N是核心数

-------------3-------------
[1] cp fix* /home/xx.../lmp/src
[2] cp Makefile.mpi /home/xx.../lmp/src/MAKE
[3] cd /home/xx.../lmp/src
[4] make yes-all
[5] make no-lib
[6] sudo make mpi -jN
[7] cp lmp_mpi /usr/bin

-------------4-------------
[1] lmp_mpi -in in.exam

done
