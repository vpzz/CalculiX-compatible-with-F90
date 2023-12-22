# Build Guidance
1. Download the `Calculix.tar.gz` file, and after extracting it, the CCX directory will appear, which contains three folders: `SPOOLES2.2, ARAPCK, and Calculix`.
2. First build SPOOLES2.2 and ARAPCK, and finally build Calculix. Three folders are placed in the same level directory, but it is not required to all be placed in the user's home directory, as most of the makefiles are relative paths.
3. Enter `SPOOLES.2.2` and execute `make CC=gcc lib`. If `CC=gcc` is not added, an error will be reported`:/usr/lang-4.0/bin/cc: No such file or directory`.
4. Enter the `ARPACK` folder and first modify the `ARMake.inc` file according to README.
   1. Modify `home` to the ARPACK folder path
   2. Modify `PLAT=INTEL`
   3. Modify `FFLAGS = -O -fallow-argument-mismatch`. The option of `-cg89` has been removed here and `-fallow-argument-mismatch` has been added
   4. Modify `UTIL/second.f` and add a * comment at the beginning of the `Extended ETIME`
   5. Finally, run `make lib`
5. Execute `make` in `Calculix/ccx_2.20/src`. If you encounter an `Interface mismatch in dummy procedure 'f' at (1): 'fun' is not a function` error. Compile the file separately and add the option `-std=legacy`.
6. Execute `./ccx_2.20 ../test/beamp`, check for any occurrence of beam.dat file, which can be proofread to verify whether the software has successfully compiled.

# 构建指南
1. 下载Calculix.tar.gz文件，解压后会出现CCX目录，内部含有SPOOLES2.2，ARAPCK和Calculix三个文件夹。
2. 先构建SPOOLES2.2和ARAPCK，最后构建Calculix。三个文件夹放在同一级目录中，但不要求都放在用户家目录中，因为makefile中大多数为相对路径。
3. 进入SPOOLES.2.2中执行 make CC=gcc lib。如果不加CC=gcc会报错:/usr/lang-4.0/bin/cc: No such file or directory。
4. 进入ARPACK文件夹，先根据README修改ARmake.inc文件。
   1. 修改home为ARPACK文件夹路径
   2. 修改PLAT = INTEL
   3. 修改FFLAGS = -O -fallow-argument-mismatch。这里去除了-cg89的选项，增加了-fallow-argument-mismatch
   4. 修改UTIL/second.f，在EXTERNAL ETIME的最开头添加*注释
   5. 最后运行make lib即可
6. 在Calculix/ccx_2.20/src中执行make。如果遇到 Interface mismatch in dummy procedure ‘f’ at (1): ‘fun’ is not a function的错误。单独编译该文件，应该加上 --std=legacy的选项。
7. 执行 ./ccx_2.20 ../test/beamp，检查是否出现beamp.dat文件，可以beamp.dat.ref校对检验软件是否成功编译。
