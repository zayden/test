##### 
1.下载源码

```shell
cd dl
wget https://github.com/opencv/opencv/archive/3.4.5.tar.gz
mv 3.4.5.tar.gz opencv-3.4.5.tar.gz
```

##### 2.修改编译选项

```shell
cd ../package/libs/opencv/
#修改Makefile文件
#把3.2.0修改为3.4.5
#增加编译选项
CMAKE_OPTIONS += -DENABLE_NEON:BOOL=ON -DENABLE_VFPV3:BOOL=ON
vi Makefie
#删除原来的补丁文件
rm -rf patches/
```

##### 3.编译

```shell
make -j8
#报错：
FATAL: In-source builds are not allowed.
       You should create a separate directory for build files.

#删除out/astar-nbr/compile_dir/target/linux-astar-nbr/opencv-3.4.5/CMakeLists.txt中的
if(" ${CMAKE_SOURCE_DIR}" STREQUAL " ${CMAKE_BINARY_DIR}")
  message(FATAL_ERROR "
FATAL: In-source builds are not allowed.
       You should create a separate directo
```





```shell
#opencv3.4.5打开ENABLE_NEON ENABLE_VFPV3
root@TinaLinux:~# ./main6.test 6
This machine is Little-Endian.
Does this OpenCV version have SIMD128 support? --> yes
Detect test.png for 50 times in 4977ms.
root@TinaLinux:~# ./main6.test 6
This machine is Little-Endian.
Does this OpenCV version have SIMD128 support? --> yes
Detect test.png for 50 times in 4983ms.
root@TinaLinux:~# ./main6.test 6
This machine is Little-Endian.
Does this OpenCV version have SIMD128 support? --> yes
Detect test.png for 50 times in 4994ms.
root@TinaLinux:~#

#opencv3.2.0关闭ENABLE_NEON ENABLE_VFPV3
root@TinaLinux:~# ./main.test 6
This machine is Little-Endian.
Does this OpenCV version have SIMD128 support? --> yes
Detect test.png for 50 times in 5099ms.
root@TinaLinux:~# ./main.test 6
This machine is Little-Endian.
Does this OpenCV version have SIMD128 support? --> yes
Detect test.png for 50 times in 5100ms.
root@TinaLinux:~# ./main.test 6
This machine is Little-Endian.
Does this OpenCV version have SIMD128 support? --> yes
Detect test.png for 50 times in 5100ms.

```

