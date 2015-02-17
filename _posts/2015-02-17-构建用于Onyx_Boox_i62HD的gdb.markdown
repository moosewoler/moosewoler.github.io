---
  layout: post
  author: Moose W. Oler
  abstract: 本文介绍了如何构建用于Onyx Boox i62HD的gdb和gdbserver，告别printf。
  categories: 玩意儿
  tags:
    - onyx-boox
    - i62hd
    - 交叉编译
    - gdb
---

### 0 引言

为了调试程序，告别printf。

### 1 构建gdb

自带的zlib不知道什么问题，需要先构建zlib[1]。

    $ apt-get source zlib
    $ cd zlib-1.2.7.dfsg/
    $ ./configure --prefix=/opt/onyx/mwo
    $ make
    $ make install

构建gdb。由于我们得在i62hd上运行gdb，所以这里和参考资料有些不同[2]\[3]。

    $ apt-get source gdb
    $ cd gdb-7.4.1+dfsg/
    $ ./configure --prefix=/opt/onyx/mwo --host=arm-linux
    $ make -j4
    $ make install

由于根本没用Qt，所以跟Onyx Boox的固件版本无关，据推测也可以用于其他型号。


### 2 配置eclipse

由于我的设备网络连接不灵，这部分暂时搁置。

### 3 系统要求

uname

    $ uname -a
    Linux debian 3.2.0-4-686-pae #1 SMP Debian 3.2.65-1+deb7u1 i686 GNU/Linux

gcc

    $ arm-linux-gcc -v
    Using built-in specs.
    Target: arm-fsl-linux-gnueabi
    Configured with: /work/arm-toolchains/tmp/src/gcc-4.4.4/configure --build=i686-build_pc-linux-gnu --host=i686-build_pc-linux-gnu --target=arm-fsl-linux-gnueabi --prefix=/work/arm_fsl_gcc_4.4.4_multilib --with-sysroot=/work/arm_fsl_gcc_4.4.4_multilib/arm-fsl-linux-gnueabi/multi-libs --enable-languages=c,c++ --with-pkgversion=4.4.4_09.06.2010 --enable-__cxa_atexit --disable-libmudflap --with-host-libstdcxx='-static-libgcc -Wl,-Bstatic,-lstdc++,-Bdynamic -lm' --with-gmp=/work/arm-toolchains/tmp/arm-fsl-linux-gnueabi/build/static --with-mpfr=/work/arm-toolchains/tmp/arm-fsl-linux-gnueabi/build/static --with-ppl=/work/arm-toolchains/tmp/arm-fsl-linux-gnueabi/build/static --with-cloog=/work/arm-toolchains/tmp/arm-fsl-linux-gnueabi/build/static --enable-threads=posix --enable-target-optspace --with-local-prefix=/work/arm_fsl_gcc_4.4.4_multilib/arm-fsl-linux-gnueabi/multi-libs --disable-nls --enable-symvers=gnu --enable-c99 --enable-long-long --enable-multilib --with-system-zlib --enable-lto
    Thread model: posix
    gcc version 4.4.4 (4.4.4_09.06.2010) 

cpuinfo(部分)

    $ cat /proc/cpuinfo 
    processor   : 0
    vendor_id   : GenuineIntel
    cpu family  : 6
    model       : 37
    model name  : Intel(R) Core(TM) i7 CPU       L 620  @ 2.00GHz
    stepping    : 5
    microcode   : 0x4
    cpu MHz     : 1199.000
    cache size  : 4096 KB
    physical id : 0
    siblings    : 4
    core id     : 0
    cpu cores   : 2
    apicid      : 0
    initial apicid  : 0
    fdiv_bug    : no
    hlt_bug     : no
    f00f_bug    : no
    coma_bug    : no
    fpu     : yes
    fpu_exception   : yes
    cpuid level : 11
    wp      : yes
    flags       : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid sse4_1 sse4_2 popcnt aes lahf_lm ida arat dtherm tpr_shadow vnmi flexpriority ept vpid
    bogomips    : 3990.29
    clflush size    : 64
    cache_alignment : 64
    address sizes   : 36 bits physical, 48 bits virtual
    power management:

### 参考资料

1. [Cross-Compiled Linux From Scratch version 3.0.0-SYSTEMD-PowerPC](http://www.clfs.org/view/CLFS-3.0.0-SYSTEMD/ppc/index.html)
2. [贝壳博客：Eclipse-cdt 配合 gdbserver 进行 arm 程序远程调试 上](http://bashell.sinaapp.com/archives/eclipse-cdt-gdbserver-arm-remote-debugging-1.html)
3. [贝壳博客：Eclipse-cdt 配合 gdbserver 进行 arm 程序远程调试 下](http://bashell.sinaapp.com/archives/eclipse-cdt-gdbserver-arm-remote-debugging-2.html)
4. [构建Onyx Boox i62HD开发环境]()

