# vscode c++ 配置

## 配置方法

1. 安装[vscode](https://code.visualstudio.com/Download)
    ![安装vscode](doc/image.png)
2. 安装简体中文语言包
   ![安装简体中文语言包](doc/image3.png)
3. 安装C/C++插件
   ![alt text](doc/zoomit.png)
4. 安装[mingw](https://github.com/writer-liu/vscode-cpp-config/releases/download/vscode_1/x86_64-14.2.0-release-win32-seh-ucrt-rt_v12-rev2.7z)
5. 配置系统环境

   - 右键此电脑 -> 属性 -> 高级系统设置 -> 环境变量
   - 在系统变量中找到Path，双击，点击新建，添加`mingw`的`bin`目录，如：`D:\myDate\mingw64\bin`
   - 或运行[add_mingw_to_path.bat](https://github.com/writer-liu/vscode-cpp-config/releases/download/vscode_1/add_mingw_to_path.bat)![462418206-ab9d7e50-b36e-4df0-a586-4a6c522a1c21.png (1734×927)](https://private-user-images.githubusercontent.com/187073916/462418206-ab9d7e50-b36e-4df0-a586-4a6c522a1c21.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NTU5NTQ5MTMsIm5iZiI6MTc1NTk1NDYxMywicGF0aCI6Ii8xODcwNzM5MTYvNDYyNDE4MjA2LWFiOWQ3ZTUwLWIzNmUtNGRmMC1hNTg2LTRhNmM1MjJhMWMyMS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwODIzJTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDgyM1QxMzEwMTNaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT01NzBkOGI4MjY5YmQ4ZGIwNTU0NzAzYjFjMzI4Yjc2YmVmYjRhNDA3NTFhM2ZmMmUyOTdkNWQxNTFkMDAwOGE4JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.JSyDnDXiWtw2zNGb4cpDmslkgOvCUVyTQcAjh1LgDj4)
6. 配置.vscode 文件夹  **下载了`code runner`插件，可直接运行`.cpp`，无需配置**

   - 下载`.vscode`文件夹
   - 对`c_cpp_properties.json`、`launch.json`、`tasks.json`进行配置

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
               "compilerPath": "D:/myDate/mingw64/bin/g++.exe" // 更改为你的`编译器路径`
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
               "name": "C/C++: g++.exe 构建和调试活动文件",
               "type": "cppdbg",
               "request": "launch",
               "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",
               "args": [],
               "stopAtEntry": false,
               "cwd": "${fileDirname}",
               "environment": [],
               "externalConsole": false,
               "MIMode": "gdb",
               "miDebuggerPath": "D:\\myDate\\mingw64\\bin\\gdb.exe", // // 更改为你的`编译器路径`
               "setupCommands": [
                   {
                       "description": "为 gdb 启用整齐打印",
                       "text": "-enable-pretty-printing",
                       "ignoreFailures": true
                   }
               ],
               "preLaunchTask": "C/C++: g++.exe 生成活动文件"
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
               "label": "C/C++: g++.exe 生成活动文件",
               "command": "D:\\myDate\\mingw64\\bin\\g++.exe", // 更改为你的`编译器路径`
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
               "detail": "调试器生成的任务。"
           }
       ],
       "version": "2.0.0"
   }
   ```
7. 重启`vscode`，打开一个`.cpp`文件，按`F5`，选择`C/C++: g++.exe 构建和调试活动文件`，即可运行调试
    ![alt text](doc/image4.png)