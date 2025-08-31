# vscode c++ ����

## ���÷���

1. ��װ`vscode`[����](https://code.visualstudio.com/Download)��[github����](https://github.com/writer-liu/vscode-cpp-config/releases/download/config-v1/VSCodeUserSetup-x64-1.103.2.exe)

    ![��װvscode](doc/image.png)

2. ��װ�����������԰�

   ![��װ�����������԰�](doc/image3.png)

3. ��װC/C++���

   ![alt text](doc/zoomit.png)

4. ��װ[mingw](https://github.com/writer-liu/vscode-cpp-config/releases/download/config/x86_64-14.2.0-release-win32-seh-ucrt-rt_v12-rev2.7z)

5. ����ϵͳ����

   - �Ҽ��˵��� -> ���� -> �߼�ϵͳ���� -> ��������
   - ��ϵͳ�������ҵ�Path��˫��������½������`mingw`��`bin`Ŀ¼���磺`D:\myDate\mingw64\bin`
   - ������[add_mingw_to_path.bat](https://github.com/writer-liu/vscode-cpp-config/releases/download/conifg/add_mingw_to_path.bat)

   ![add_mingw_to_path](doc/image5.png)

6. ����.vscode �ļ���  **������`code runner`�������ֱ������`.cpp`����������**

   - ����`.vscode`�ļ���
   - ��`c_cpp_properties.json`��`launch.json`��`tasks.json`��������

   `c_cpp_properties.json`

   ```javascript
   {
       "configurations": [
           {
               "name": "Win32",
               "includePath": [
                   "${workspaceFolder}/**"
               ],
               "defines": [
                   "_DEBUG",
                   "UNICODE",
                   "_UNICODE"
               ],
               "cStandard": "c23",
               "cppStandard": "c++23",
               "intelliSenseMode": "windows-gcc-x64",
               "compilerPath": "D:/myDate/mingw64/bin/g++.exe" // ����Ϊ���`������·��`
           }
       ],
       "version": 4
   }
   ```
   `launch.json`

   ```javascript
   {
       "configurations": [
           {
               "name": "C/C++: g++.exe �����͵��Ի�ļ�",
               "type": "cppdbg",
               "request": "launch",
               "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",
               "args": [],
               "stopAtEntry": false,
               "cwd": "${fileDirname}",
               "environment": [],
               "externalConsole": false,
               "MIMode": "gdb",
               "miDebuggerPath": "D:\\myDate\\mingw64\\bin\\gdb.exe", // // ����Ϊ���`������·��`
               "setupCommands": [
                   {
                       "description": "Ϊ gdb ���������ӡ",
                       "text": "-enable-pretty-printing",
                       "ignoreFailures": true
                   }
               ],
               "preLaunchTask": "C/C++: g++.exe ���ɻ�ļ�"
           }
       ],
       "version": "2.0.0"
   }
   ```
   `tasks.json`

   ```javascript
   {
       "tasks": [
           {
               "type": "cppbuild",
               "label": "C/C++: g++.exe ���ɻ�ļ�",
               "command": "D:\\myDate\\mingw64\\bin\\g++.exe", // ����Ϊ���`������·��`
               "args": [
                   "-fdiagnostics-color=always",
                   "-g",
                   "${file}",
                   "-o",
                   "${fileDirname}\\${fileBasenameNoExtension}.exe"
               ],
               "options": {
                   "cwd": "${fileDirname}"
               },
               "problemMatcher": [
                   "$gcc"
               ],
               "group": "build",
               "detail": "���������ɵ�����"
           }
       ],
       "version": "2.0.0"
   }
   ```
7. ����`vscode`����һ��`.cpp`�ļ�����`F5`��ѡ��`C/C++: g++.exe �����͵��Ի�ļ�`���������е���

    ![alt text](doc/image4.png)