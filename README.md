＃卒業論文
### 20170917読んだもの： 
1.<山崎 誠> 言語単位と文の長さが品詞比率に与える影響 (2014年3月，国立国語研究所)
2.

### 遭った問題：

#### problem：
Win10 64x python27 按照 http://qiita.com/h_kabocha/items/5bee9e9b852aed11411b 的提示安装mecab时，编译模块时出现了以下问题：
#### description：
C:\Python27\Lib\site-packages\MeCab\mecab-python-0.996>py -2 setup.py build
running build
running build_py
running build_ext
building '_MeCab' extension
error: Unable to find vcvarsall.bat
#### solution：
stackoverflow上关于这个问题的解决方式也是让人眼花缭乱的！
后来参考：http://wangye.org/blog/archives/738/
决定就按这种看起来最简便的方式解决：

##### 1.打开64位Visual Studio 201x命令行编译模式
从开始菜单 – Microsoft Visual Studio 201x – Visual Studio Tools – Visual Studio x64 Win64 命令提示(201x)
#### 2.使用下面的命令设置环境：
set DISTUTILS_USE_SDK=1
set MSSdk=1
之后再运行之前的命令，成功了：

····
C:\Python27\Lib\site-packages\MeCab\mecab-python-0.996>py -2 setup.py build
running build
running build_py
running build_ext
building '_MeCab' extension
creating build\temp.win-amd64-2.7
creating build\temp.win-amd64-2.7\Release
C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Tools\MSVC\14.11.25503\bin\HostX64\x64\cl.exe /c /nologo /Ox /MD /W3 /GS- /DNDEBUG -IC:\Python27\Lib\site-packages\MeCab\sdk -IC:\Python27\include -IC:\Python27\PC /TpMeCab_wrap.cxx /Fobuild\temp.win-amd64-2.7\Release\MeCab_wrap.obj
MeCab_wrap.cxx
MeCab_wrap.cxx(3747): warning C4530: 使用了 C++ 异常处理程序，但未启用展开语义。请 指定 /EHsc
C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Tools\MSVC\14.11.25503\include\type_traits(2342): warning C4577: 在未指定异常处理模式的情况下使用了 "noexcept"；不一定会在异常时终止。指定 /EHsc
C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Tools\MSVC\14.11.25503\bin\HostX64\x64\link.exe /DLL /nologo /INCREMENTAL:NO /LIBPATH:C:\Python27\Lib\site-packages\MeCab\sdk /LIBPATH:C:\Python27\libs /LIBPATH:C:\Python27\PCbuild\amd64 libmecab.lib /EXPORT:init_MeCab build\temp.win-amd64-2.7\Release\MeCab_wrap.obj /OUT:build\lib.win-amd64-2.7\_MeCab.pyd /IMPLIB:build\temp.win-amd64-2.7\Release\_MeCab.lib /MANIFESTFILE:build\temp.win-amd64-2.7\Release\_MeCab.pyd.manifest
  正在创建库 build\temp.win-amd64-2.7\Release\_MeCab.lib 和对象 build\temp.win-amd64-2.7\Release\_MeCab.exp
····
C:\Python27\Lib\site-packages\MeCab\mecab-python-0.996>py -2 setup.py install
running install
running build
running build_py
running build_ext
running install_lib
copying build\lib.win-amd64-2.7\MeCab.py -> C:\Python27\Lib\site-packages
copying build\lib.win-amd64-2.7\_MeCab.pyd -> C:\Python27\Lib\site-packages
byte-compiling C:\Python27\Lib\site-packages\MeCab.py to MeCab.pyc
running install_egg_info
Writing C:\Python27\Lib\site-packages\mecab_python-0.996-py2.7.egg-info



