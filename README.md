# UnpackShellScripts
总结大佬们的脱壳脚本

[frida_dump_dex](https://github.com/hluwa/FRIDA-DEXDump)
- 基于内存关键字dex035(64 65 78 0a 30 33 35 00)的搜索

[dex_dump](https://github.com/lasting-yang/frida_dump)
- 基于断点libart.so中的[DefineClass](https://cs.android.com/android/platform/superproject/+/master:art/runtime/class_linker.cc;l=3271;bpv=0;bpt=1)函数

[frida-unpack](https://github.com/dstmath/frida-unpack)
- 基于断点libdexfile.so中的[OpenCommon](https://cs.android.com/android/platform/superproject/+/master:art/libdexfile/dex/dex_file_loader.cc;l=316?q=OpenCommon&sq=&ss=android%2Fplatform%2Fsuperproject)函数

---
### 脱壳点：
#### **Android 9.0** (OpenCommon)
##### 32 _ZN3art16ArtDexFileLoader10OpenCommonEPKhjS2_jRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPKNS_10OatDexFileEbbPS9_NS3_10unique_ptrINS_16DexFileContainerENS3_14default_deleteISH_EEEEPNS_13DexFileLoader12VerifyResultE
##### 64 _ZN3art13DexFileLoader10OpenCommonEPKhmS2_mRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPKNS_10OatDexFileEbbPS9_NS3_10unique_ptrINS_16DexFileContainerENS3_14default_deleteISH_EEEEPNS0_12VerifyResultE

#### **Android 8.0** (OpenCommon)
##### 32 _ZN3art7DexFile10OpenCommonEPKhjRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPKNS_10OatDexFileEbbPS9_PNS0_12VerifyResultE
##### 64 _ZN3art7DexFile10OpenCommonEPKhmRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPKNS_10OatDexFileEbbPS9_PNS0_12VerifyResultE

#### **Android 7.0 ~ 6.0** (OpenMemory)
##### 32 _ZN3art7DexFile10OpenMemoryEPKhjRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPNS_6MemMapEPKNS_10OatDexFileEPS9_
##### 64 _ZN3art7DexFile10OpenMemoryEPKhmRKNSt3__112basic_stringIcNS3_11char_traitsIcEENS3_9allocatorIcEEEEjPNS_6MemMapEPKNS_10OatDexFileEPS9_

