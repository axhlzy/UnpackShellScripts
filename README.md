# UnpackShellScripts
总结大佬们的脱壳脚本

[frida_dump_dex](https://github.com/hluwa/FRIDA-DEXDump)
- 基于内存关键字dex035(64 65 78 0a 30 33 35 00)的搜索

[dex_dump](https://github.com/lasting-yang/frida_dump)
- 基于断点libart.so中的[DefineClass](https://cs.android.com/android/platform/superproject/+/master:art/runtime/class_linker.cc;l=3271;bpv=0;bpt=1)函数

[frida-unpack](https://github.com/dstmath/frida-unpack)
- 基于断点libdexfile.so中的[OpenCommon](https://cs.android.com/android/platform/superproject/+/master:art/libdexfile/dex/dex_file_loader.cc;l=316?q=OpenCommon&sq=&ss=android%2Fplatform%2Fsuperproject)函数

[dumpDex](https://github.com/WrBug/dumpDex)
- 需要配合xposed使用，xp框架在这里仅仅是起到一个加载so的目的（也可以不用xposed，替代的方法很多），本质是使用的ele7enxxh的[inlinehook](https://github.com/ele7enxxh/Android-Inline-Hook)框架，判断安卓版本后hook指定的脱壳点并dump出dex

[drizzleDumper](https://github.com/DrizzleRisk/drizzleDumper)
- 通过/proc/%s/cmdline遍历去找到指定PackageName的pid,fork出子进程attach到目标pid，然后就是和一套内存搜索组合拳打进去，再dump dex

[FART](https://github.com/hanbinglengyue/FART)
- 基于Android 6.0实现主动调用的脱壳机

[Youpk](https://github.com/Youlor/Youpk)
- 又一款ART的主动调用的脱壳机

---
### 脱壳点：
#### **Android 9.0** (OpenCommon)
##### 32 _ZN3art16ArtDexFileLoader10OpenCommonEPKhjS2_jRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPKNS_10OatDexFileEbbPS9_NS3_10unique_ptrINS_16DexFileContainerENS3_14default_deleteISH_EEEEPNS_13DexFileLoader12VerifyResultE
##### 64 _ZN3art13DexFileLoader10OpenCommonEPKhmS2_mRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPKNS_10OatDexFileEbbPS9_NS3_10unique_ptrINS_16DexFileContainerENS3_14default_deleteISH_EEEEPNS0_12VerifyResultE

#### **Android 8.0** (OpenCommon)
##### 32 _ZN3art7DexFile10OpenCommonEPKhjRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPKNS_10OatDexFileEbbPS9_PNS0_12VerifyResultE
##### 64 _ZN3art7DexFile10OpenCommonEPKhmRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPKNS_10OatDexFileEbbPS9_PNS0_12VerifyResultE

#### **Android 7.0 ~ 5.0** (OpenMemory)
##### 32 _ZN3art7DexFile10OpenMemoryEPKhjRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPNS_6MemMapEPKNS_10OatDexFileEPS9_
##### 64 _ZN3art7DexFile10OpenMemoryEPKhmRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPNS_6MemMapEPKNS_10OatDexFileEPS9_

#### **Android < 5.0** (dvmDexFileOpenPartial 和 dexFileParse)
##### dvmDexFileOpenPartial(addr, len, &pDvmDex)
##### dexFileParse(const u1* data, size_t length, int flags)

