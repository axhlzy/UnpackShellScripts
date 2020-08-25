# UnpackShellScripts
总结大佬们的脱壳脚本

[frida_dump_dex](https://github.com/hluwa/FRIDA-DEXDump)
- 基于内存关键字dex035(64 65 78 0a 30 33 35 00)的搜索

[dex_dump](https://github.com/lasting-yang/frida_dump)
- 基于断点libart.so中的[DefineClass](https://cs.android.com/android/platform/superproject/+/master:art/runtime/class_linker.cc;l=3271;bpv=0;bpt=1)函数

[frida-unpack](https://github.com/dstmath/frida-unpack)
- 基于断点libdexfile.so中的[OpenCommon](https://cs.android.com/android/platform/superproject/+/master:art/libdexfile/dex/dex_file_loader.cc;l=316?q=OpenCommon&sq=&ss=android%2Fplatform%2Fsuperproject)函数
