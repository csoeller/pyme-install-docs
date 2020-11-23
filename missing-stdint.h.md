# Issue with missing stdint.h

Came across an issue during install of PYME:

C:\Users\cs463\AppData\Local\Programs\Common\Microsoft\Visual C++ for Python\9.0\VC\Bin\amd64\cl.exe /c /nologo /Ox /MD /W3 /GS- /DNDEBUG -IPYME\experimental -IC:\ProgramData\Anaconda2\envs\pyme-default-plain\lib\site-packages\numpy\core\include -Iwin_incl -IC:\ProgramData\Anaconda2\envs\pyme-default-plain\lib\site-packages\numpy\core\include -IC:\ProgramData\Anaconda2\envs\pyme-default-plain\include -IC:\ProgramData\Anaconda2\envs\pyme-default-plain\PC -IC:\ProgramData\Anaconda2\envs\pyme-default-plain\include -IC:\ProgramData\Anaconda2\envs\pyme-default-plain\PC /TcPYME\experimental\_triangle_mesh.c /Fobuild\temp.win-amd64-2.7\Release\PYME\experimental\_triangle_mesh.obj -O3 -fno-exceptions -ffast-math -march=native -mtune=native
cl : Command line warning D9002 : ignoring unknown option '-O3'
cl : Command line warning D9002 : ignoring unknown option '-fno-exceptions'
cl : Command line warning D9002 : ignoring unknown option '-ffast-math'
cl : Command line warning D9002 : ignoring unknown option '-march=native'
cl : Command line warning D9002 : ignoring unknown option '-mtune=native'
_triangle_mesh.c
c:\programdata\anaconda2\envs\pyme-default-plain\lib\site-packages\numpy\core\include\numpy\npy_1_7_deprecated_api.h(14) : Warning Msg: Using deprecated NumPy API, disable it with #define NPY_NO_DEPRECATED_API NPY_1_7_API_VERSION
c:\python-support\python-microscopy-git\pyme\experimental\triangle_mesh_utils.h(4) : fatal error C1083: Cannot open include file: 'stdint.h': No such file or directory

The following site has details: https://stackoverflow.com/questions/44865576/python-scikit-image-install-failing-using-pip
