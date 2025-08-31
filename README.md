# vscode c++ ����

## ���÷���

1. ��װ[vscode](https://code.visualstudio.com/Download)
    ![��װvscode](doc/image.png)
2. ��װ�����������԰�
   ![��װ�����������԰�](doc/image3.png)
3. ��װC/C++���
   ![alt text](doc/zoomit.png)
4. ��װ[mingw](https://github.com/writer-liu/vscode-cpp-config/releases/download/vscode_1/x86_64-14.2.0-release-win32-seh-ucrt-rt_v12-rev2.7z)
5. ����ϵͳ����

   - �Ҽ��˵��� -> ���� -> �߼�ϵͳ���� -> ��������
   - ��ϵͳ�������ҵ�Path��˫��������½������`mingw`��`bin`Ŀ¼���磺`D:\myDate\mingw64\bin`
   - ������[add_mingw_to_path.bat](https://github.com/writer-liu/vscode-cpp-config/releases/download/vscode_1/add_mingw_to_path.bat)![462418206-ab9d7e50-b36e-4df0-a586-4a6c522a1c21.png (1734��927)](https://private-user-images.githubusercontent.com/187073916/462418206-ab9d7e50-b36e-4df0-a586-4a6c522a1c21.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTU5NTQ5MTMsIm5iZiI6MTc1NTk1NDYxMywicGF0aCI6Ii8xODcwNzM5MTYvNDYyNDE4MjA2LWFiOWQ3ZTUwLWIzNmUtNGRmMC1hNTg2LTRhNmM1MjJhMWMyMS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwODIzJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDgyM1QxMzEwMTNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01NzBkOGI4MjY5YmQ4ZGIwNTU0NzAzYjFjMzI4Yjc2YmVmYjRhNDA3NTFhM2ZmMmUyOTdkNWQxNTFkMDAwOGE4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.JSyDnDXiWtw2zNGb4cpDmslkgOvCUVyTQcAjh1LgDj4)
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