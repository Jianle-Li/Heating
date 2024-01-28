##### 2022/4/18

在添加oled.c，oled.h，oledfont.h三个文件后，编译报错：<br>

arm-none-eabi-gcc.exe: error: Core/Src/oled.c: No such file or directory<br>
arm-none-eabi-gcc.exe: error: Core/Inc/oled.h: No such file or directory<br>
arm-none-eabi-gcc.exe: error: Core/Inc/oledfont.h: No such file or directory<br>
mingw32-make.exe[3]: * [Heating.elf] Error 1<br>
mingw32-make.exe[2]: * [CMakeFiles/Heating.elf.dir/all] Error 2<br>
mingw32-make.exe[1]: *[CMakeFiles/Heating.elf.dir/rule] Error 2<br>
mingw32-make.exe: * [Heating.elf] Error 2<br>
CMakeFiles\Heating.elf.dir\build.make:424: recipe for target 'Heating.elf' failed<br>
CMakeFiles\Makefile2:94: recipe for target 'CMakeFiles/Heating.elf.dir/all' failed<br>
CMakeFiles\Makefile2:101: recipe for target 'CMakeFiles/Heating.elf.dir/rule' failed<br>
Makefile:137: recipe for target 'Heating.elf' failed<br>

经过于其他工程对比发现，本工程**CMakeLists.txt**中的**第55行中多了oled.c，oled.h，oledfont.h三个文件**，改为<br>

```c
set(LINKER_SCRIPT ${CMAKE_SOURCE_DIR}/STM32F103C8Tx_FLASH.ld)
```

后编译通过。

