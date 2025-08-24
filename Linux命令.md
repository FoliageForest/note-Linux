# 文件操作

## ls

来源: `ls --help`, `man ls`  

Usage: ls [OPTION]... [FILE]...  
List information about the FILEs (the current directory by default).  
Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.  

-a, --all                  do not ignore entries starting with .  
-l                         use a long listing format  
-d, --directory            list directories themselves, not their contents  
-h, --human-readable       with -l and -s, print sizes like 1K 234M 2G etc.  
-r, --reverse                 逆序排列  
-r, --reverse  
              reverse order while sorting  
-t                         sort by modification time, newest first  
-i, --inode                print the index number of each file  
-R, --recursive            list subdirectories recursively  
-F, --classify             append indicator (one of */=>@|) to entries  
-F, --classify[=何时]      指定 <何时> 在项目后追加指示符号（*/=@| 中的一个）  

来源: <https://gnu-linux.readthedocs.io/>

`ls -i [FILE]...` : 查看文件名对应的 inode 号码  

## rm

`rm --help`  
-d, --dir             remove empty directories  
-r, -R, --recursive   remove directories and their contents recursively  

## rmdir

## mkdir

参考: SCCC教学, <https://www.geeksforgeeks.org/mkdir-command-in-linux-with-examples/>  

`mkidr --help`  
-p, --parents     no error if existing, make parent directories as needed  
-p : A flag which enables the command to create parent directories as necessary. If the directories exist, no error is specified.  

`mkdir -p {a,b}/No{08..12}`  

mkdir  

## cp

`cp --help`  
-R, -r, --recursive           递归复制目录及其子目录内的所有内容  
-R, -r, --recursive  
              copy directories recursively  

`how cp`  
-R/r：递归处理，将指定目录下的所有文件与子目录一并处理；  

`cp /etc/rsyslog.conf{,.bak}` : 快速创建备份文件  

## type

显示命令类型的信息。

## cat

来源: `man cat`  

-n  
  打印时显示行号  

-n, --number  
       number all output lines  


## less

可以用于训练的文件, 参考 vim  
参考: <https://cn.linux-console.net/?p=19754>

来源: `less --help`, `how less`  

命令选项:  
`-N`  
  进入 less 界面后使用键入 -N 后回车, 可以暂时(本次退出 less 后失效)切换显示行号的开关状态  
  也可以在运行 less 命令时使用 -N 选项, 可以在进入 less 时显示行号, 同样为本次使用 less 有效  
`-R` : 显示颜色信息  
-r  -R  ....  --raw-control-chars  --RAW-CONTROL-CHARS  
                Output "raw" control characters.  
-s：将连续多个空行压缩成一行显示；  
-s  ........  --squeeze-blank-lines  
                  Squeeze multiple blank lines.  
-S：在单行显示较长的内容，而不换行显示；  
-S  ........  --chop-long-lines  
                Chop (truncate) long lines rather than wrapping.  
-i  ........  --ignore-case  
                Ignore case in searches that do not contain uppercase.  
-I  ........  --IGNORE-CASE  
                Ignore case in all searches.  
-p [pattern]  --pattern=[pattern]  
                Start at pattern (from command line).  
-P [prompt]   --prompt=[prompt]  
                Define new prompt.  
-N  ........  --LINE-NUMBERS  
                Use line numbers.  



运行界面:  
`/str` 键入 str 后回车 : 与 `n` 和 `N` 配合使用, 在文本中搜索字符串 str, 向下为正方向 (`n` 的查找方向)  
        `/^str` 回车 : 查找位于行首的 str 字符串  
`?str` 键入 str 后回车 : 与 `n` 和 `N` 配合使用, 在文本中搜索字符串 str, 向上为正方向 (`n` 的查找方向)  
`n` : 正向查找字符串, 配合 `/` 或 `?` 使用  
`N` : 负向查找字符串, 配合 `/` 或 `?` 使用  
`g` : 跳转至首行  
`G` : 跳转至尾行  
`800g` : 跳转到第 800 行  
`800G` : 同 `800g`  
`e` :  	向下滚动一行  
`y` :  	向上滚动一行  
`d` : 向下滚动半页  
`u` : 向上滚动半页  
`f` : 向下滚动一整页  
`b` : 向上滚动一整页  

[pagedown]： 向下翻动一页  
[pageup]： 向上翻动一页  
空格键: 滚动一页  
回车键: 滚动一行  

## grep

来源: 学校教学, `man grep`, `how grep`  

`grep "/sbin/nologin" /etc/passwd` -> 在 /etc/passwd 文件中查找包含 `/sbin/nologin` 字符串的行，并打印到屏幕上  
`grep "^#" /etc/fstab` 或 `grep ^"#" /etc/fstab` -> 查找 /etc/fstab 文件中以 # 号开始的行  
`grep "^$" /etc/fstab` 或 `grep ^$ /etc/fstab` -> 查找 /etc/fstab 文件中的空行  
`env | grep ^"PATH"`  

-n  
  `grep -n "/bin/bash" /etc/passwd` -> 在 /etc/passwd 文件中查找包含 `/sbin/nologin` 字符串的行，打印到屏幕上，同时打印编号  
-v  
  `grep -v "/sbin/nologin" /etc/passwd` -> 在 /etc/passwd 文件中查找不包含 `/sbin/nologin` 字符串的行，并打印到屏幕上。带上 -n 选项 (即 `grep -nv "/sbin/nologin" /etc/passwd`) 则额外打印编号  

`env | grep -i home`  

-i --ignore-case      # 忽略字符大小写的差别。  
-i, --ignore-case  
       Ignore case distinctions, so that characters that differ only  in  case  match each other.  
-v, --invert-match  
       Invert the sense of matching, to select non-matching lines.  


## wc

`how wc`  
wc 命令 统计指定文件中的字节数、字数、行数，并将统计结果显示输出。利用 wc 指令我们可以计算文件的 Byte 数、字数或是列数，若不指定文件名称，或是所给予的文件名为“-”，则 wc 指令会从标准输入设备读取数据。wc 同时也给出所指定文件的总统计数。  

`wc -l FILE`  

## stat

Usage: stat [OPTION]... FILE...
Display file or file system status.

`小飞侠Geek`  
`stat -c %a FILE` : 以数值显示文件的权限  
`stat -c %F FILE`  

## vim

可以用于训练的文件 /etc/sysconfig/network-scripts/ , /etc/ssh/sshd_config , /var/log/auth.log  

参考: https://cloud.tencent.com/developer/article/1671410 , <https://github.com/chloneda/vim-cheatsheet> , SCCC 教学  

Command Mode (可视模式)  
  `i` : 在当前位置（光标所在的位置）前插入  
  `a` : 在当前位置（光标所在的位置）后插入  
  `I` : 在光标移动到当前行行首, 进入插入模式  
  `A` : 在光标移动到当前行行尾, 进入插入模式  
  `dd` : 删除光标所在的行  
  数字 + 命令 : 运行指定次数命令  
  HOME 键 : 光标移动至当前行行首  
  `0` : 同 HOME 键  
  `^` : 同 HOME 键  
  END 键 : 光标移动至当前行行尾  
  `$` : 同 END 键  
  `1G` : 同 gg  
  `gg` : 光标移动到第一行行首  
  `G` : 光标移动到最后一行行首  
  `N<ENTER>` : 光标向下移动 N 行  
  `x` : 删除光标所在处的字符，光标不会移动，可以理解为光标位于光标字符与光标前字符中间  
  `X` : 删除光标位置的前一个字符，光标跟随删除位置移动，可以理解为光标位于光标字符与光标前字符中间  
  `C` : 删除从光标处到行尾(包括光标处)的全部字符，然后进入插入模式  
  `o` : 在当前行下方插入一空行，光标移至新建的空行，同时进入插入模式  
  `O` : 在当前行上方插入一空行，光标移至新建的空行，同时进入插入模式  
  `f` 后接一个字符, 无需回车 : 在当前行内, 向后(向行尾)查找某一字符  
  `F` 后接一个字符, 无需回车 : 在当前行内, 向前(向行首)查找某一字符  
  `/` 后接字符(串), 然后回车 : 向下查找内容. 按 `n` 沿着当前查找方向跳转到下一个匹配字符, 按 `N` 沿着当前查找方向的反方向跳转到下一个匹配字符  
  `?` 后接字符(串), 然后回车 : 向上查找内容. 按 `n` 沿着当前查找方向跳转到下一个匹配字符, 按 `N` 沿着当前查找方向的反方向跳转到下一个匹配字符  
  `y$` : 复制从光标处(包括光标处的字符)到当前行行尾的内容  
  `yy` : 复制光标所在行到缓冲区  
  `p` : 缓冲区内的字符粘贴到光标所在位置  
  `u` : undo  
  `U` : 用于取消对当前行所做的所有编辑  
  `CTRL-R` : redo  
  `CTRL-F` : 上翻(接近一整页)  
  `CTRL-B` : 下翻(接近一整页)  
  `ZZ` : 保存退出  
  `ZQ` : 不保存退出  

Command Line Mode (底线模式)  
  `:0` 回车 : 光标移动到首行行首  
  `:1` 回车 : 光标移动到首行行首  
  `:$` 回车 : 光标移动到尾行行首  
  `:N<ENTER>` : 跳转到指定行, 例如 `:121<ENTER>` 跳转到第 121 行  
      也可以像这样 `vim +121 /etc/ssh/sshd_config` 这里使用 +121 迅速跳转到第 121 行进行编辑  
  `:n1,n2 w /path/to/file` : 将 n1~n2 行(包括行 n1 和行 n2)的内容存储成 /path/to/file 文件  
  `:set nu` 回车 : 显示行号  
  `:set nonu` 回车 : 取消显示行号  
  `:set wrap` 回车 : 折行显示(超出屏幕宽度的行分成多行显示)  
  `:set nowrap` 回车 : 取消折行显示  
  `:set no*` 回车 : 取消设置. 比如 `:set nonu` 不显示行号、`:set nowrap` 不折行等等  
  `:set ignorecase` 回车 : 不区分大小写查找字符串  

## tail

`tail /etc/passwd` : 在屏幕上打印 /etc/passwd 文件的最后 10 行  

-n, --lines=[+]NUM       output the last NUM lines, instead of the last 10;  
                           or use -n +NUM to output starting with line NUM  

-n  
  `tail -n 2 /etc/passwd` 或 `tail -n2 /etc/passwd` 或 `tail -2 /etc/passwd` : 在屏幕上打印 /etc/passwd 文件的最后 2 行.  
-f  
  `tail -f /var/log/messages` : 实时查看日志  

## head

`head /etc/passwd` : 在屏幕上打印 /etc/passwd 文件的头部共 10 行  

-n, --lines=[-]NUM       print the first NUM lines instead of the first 10;  
                           with the leading '-', print all but the last  
                           NUM lines of each file  


-n  
  `head -n 2 /etc/passwd` 或 `head -n2 /etc/passwd` 或 `head -2 /etc/passwd` : 在屏幕上打印 /etc/passwd 文件的头部共 2 行  

## awk


-F value         sets the field separator, FS, to value.  

`man awk`  
`awk --help`  
参考(一字不漏地): https://www.ruanyifeng.com/blog/2018/11/awk.html  

## sed

`sed -n "3p"` 或者 `sed -n '3p'` 或者 `sed -n 3p` : 打印第 3 行的文本。后接文件名或者使用 `|`。  
`sed -n "3,5p"` 或者 `sed -n '3,5p'` 或者 `sed -n 3,5p` : 打印第 3 到第 5 行的文本。  

## tree

`tree --help`  
-L level      Descend only level directories deep.  
              FoliageForest: 不能为零  

## find

查找文件或目录. 如果没有指定搜索路径, 默认从当前目录查找, 即默认路径为当前目录  

`man find`  
-name  
  `find /etc -name "passwd"` : 在 /etc 目录下准确查找(不匹配 mypasswd)名为 passwd 的文件或目录  
-iname  
  说明: 不匹配大小写查找  
  `*` : 匹配所有字符(包括零个或以上数量的字符)  
  `?` : 匹配单个字符  
    `find /etc -name "init???"` : 查找目录 /etc 下以 init 开头, 且后面有三位的文件  
-size  
  按文件大小查找, 以 block 为单位, 一个 block 是 512B, 1K=2block     +大于  -小于  不写是等于  
  `find /etc -size +10000` : 目录 /etc 下大于 10000 block 的文件  
-type  
  按文件类型查找   b (块设备文件), c (字符设备文件), p(管道文件), f 二进制文件, l 软链接文件, d 目录, c 字符文件  
-user uname  
       File is owned by user uname (numeric user ID allowed).  
-o  
-a  


`find -name FILE -exec ls -l {} \;`  

## ln

`ln --help`  
-s, --symbolic              make symbolic links instead of hard links  

SCCC 上课示例  

`ln file.txt hard.ln` : 创建文件 file.txt 的硬链接  
`ln -s file.txt soft.ln` : 创建文件 file.txt 的软链接  

## 压缩打包

### tar

`tar zxvf x-ui-linux-amd64.tar.gz`  

`tar --help`  
-x, --extract, --get       从归档中解出文件  
-f, --file=ARCHIVE         使用归档文件或 ARCHIVE 设备  
-t, --list                 列出归档内容  
-r, --append               追加文件至归档结尾  
-v, --verbose              详细地列出处理的文件  
-c, --create               创建一个新归档  
-d, --diff, --compare      找出归档和文件系统的差异  
-z, --gzip, --gunzip, --ungzip   通过 gzip 过滤归档  
-z, --gzip, --gunzip, --ungzip   filter the archive through gzip  

例子: 
来源: <https://gnu-linux.readthedocs.io/zh/latest/> <https://cloud.tencent.com/developer/article/1626115> `how tar`  
`tar -xf archive.tar.xz` : 解压文件 archive.tar.xz  
`tar -xf archive.tar.xz -C /home/linuxize/files` : 解压文件 archive.tar.xz 到 /home/linuxize/files  
`tar -cvf myarchive.tar /etc/ /root/anaconda-ks.cfg` : 将 /etc/ 和 /root/anaconda-ks.cfg 归档到当前目录  
`tar -tvf myarchive.tar` : 查看归档中的内容，并不提取文件  
`tar -rvf myarchive.tar /media/fstab` : 追加文件到归档中  
`tar --exclude scf/service -zcvf scf.tar.gz scf/*` : 将 scf/ 归档，但不包括 service 文件  



### zip

压缩目录: `zip -r ./压缩后的文件名.zip ./需要压缩的目录/`  

`zip --help`  
-r   recurse into directories  

## 文件权限

### chmod

`chmod --help`  
Usage: chmod [OPTION]... MODE[,MODE]... FILE...  
  or:  chmod [OPTION]... OCTAL-MODE FILE...  
  or:  chmod [OPTION]... --reference=RFILE FILE...  
-R, --recursive        递归修改文件和目录  
-R, --recursive        change files and directories recursively  

权限 范围的表示法如下：

    u User 文件或目录的拥有者  
    g Group 文件或目录的所属群组  
    o Other 除了文件或目录的拥有者和所属组之外的其他用户  
    a All 全部的用户  
    r 读取权限，数字代号“4”  
    w 写入权限，数字代号“2”；  
    x 执行或切换权限，数字代号“1”  
    - 不具任何权限，数字代号为“0”  
    s 强制位权限，使其他用户临时拥有文件拥有者的权限  
    t 粘滞位权限，用户只能删除自己为属主的文件  

来源: <https://gnu-linux.readthedocs.io/>, `how chmod`, `chmod --help`  

--reference=RFILE  use RFILE's mode instead of MODE values  


`chmod o-x a.sh` : 删除 other 的执行权限  
`chmod ug-x a.sh` : 针对属主和属组删除执行权限  

`chmod u=rwx,g=rw,o=r ./test.log` : 当前用户具有所有权限，组用户有读写权限，其他用户只有读权限。逗号两边不能有空格存在  
`chmod 764 ./test.log` : 上一条命令的等价的八进制数表示  

### chown

`chown --help`  
Usage: chown [OPTION]... [OWNER][:[GROUP]] FILE...  
  or:  chown [OPTION]... --reference=RFILE FILE...  

-R, --recursive        operate on files and directories recursively  

`chown username FILE` : 修改文件 FILE 的属主为 username  
`chown USER:GROUP FILE` : 修改文件 FILE 的属主为 USER, 属组为 GROUP. 冒号前可以不写属主  

### chgrp

`chgrp --help`  
Usage: chgrp [OPTION]... GROUP FILE...  
  or:  chgrp [OPTION]... --reference=RFILE FILE...  

-R, --recursive        operate on files and directories recursively  

`how chgrp`  

`chgrp -R mengxin /usr/meng` : 将 /usr/meng 及其子目录下的所有文件的用户组改为 mengxin  
`chgrp group FILE` : 更改文件 FILE 的属组为 group  

### umask

`小飞侠Geek`  
| New files | New directories | |
|---|---|---|
| `666` | `777` | Linux base permissions |
| `-022` | `-022` | umask |
| `644` | `755` | Resulting permissions |

`umask --help`  
-S        以符号形式输出，否则以八进制数格式输出  
-S        makes the output symbolic; otherwise an octal number is output  

`umask` : 查看 umask 值  
`umask 000` : 修改 umask 值  

### 特殊权限

`chmod u+s FILE`  
`chmod u-s FILE`  
`chmod 4755 FILE`  
`chmod g+s /DIR`  
`chmod 2755 /DIR`  
`chmod o-t /DIR`  

`小飞侠Geek`  
当执行设置了 SUID 位的程序时, 是以该程序的属主身份执行, 而不是当前用户  
`find / -perm -4000 -type f 2> /dev/null` : 在系统中查找哪些文件设置了 SUID 位. 这里 `-4000` 中的 `-` 表示包含的意思, 不包含 `-` (即 `-perm 4000`)则精确匹配 `4000` 权限  
`find / -perm -u=s -type f 2> /dev/null` : 在系统中查找哪些文件设置了 SUID 位  
`find / -perm -2000 -type d 2> /dev/null`  
`find / -perm -2000 -type f 2> /dev/null`  
`find / -perm -2000 -o -perm -4000 -type f 2>/dev/null` 或 `find / -type f \( -perm -2000 -o -perm -4000 \) 2> /dev/null` : 在系统中查找设置了 SUID 位或 SGID 位的文件  
`find / -user root -perm -4000 2> /dev/null` : 查找包含 SUID 位且属主是 root 用户的文件  
特殊权限的危险示例:  
给 find 添加 SUID 后, 用户 user1 执行 `find -name FILE -exec /bin/sh -p \;` 可借助 find 提权, `find -name user1 -exec whoami \;` 查看提权是否成功.  
  高版本的 Linux 中, 如果启动 bash 的 Effective (有效的) UID 与 Real (真实的) UID 不相同, 而且没有使用 -p 参数, 则 bash 会将 Effective UID 还原成 Real UID.  

# 系统管理

## init

`init 0` : 关机  
`init 3` : 暂时关闭 GUI  
`init 5` : 暂时开启 GUI  
`init 6` : 重启计算机  

关闭 GUI 后可用 `CTRL + ALT + F1~F6` 切换终端  

## systemctl

start : 启动  
stop : 停止  
restart : 重启  
enable : 把服务设置为开机启动  
disable : 把服务设置为开机不启动  
is-enabled : 查看是否为 enable  
list-unit-files  

`systemctl stop sshd.service`  
`systemctl start sshd.service`  
`systemctl restart sshd.service`  
`systemctl status sshd` 或 `systemctl status sshd.service`  
`systemctl is-enabled sshd` 或 `systemctl is-enabled sshd.service`  

## service

`service nginx status`  


## ssh

ssh -i /root/.ssh/id_rsa root@192.168.8.1

-T      Disable pseudo-terminal allocation.  


     -i identity_file
             Selects a file from which the identity (private key) for public key authentication is read.
             The default is ~/.ssh/id_dsa, ~/.ssh/id_ecdsa, ~/.ssh/id_ed25519 and ~/.ssh/id_rsa.  Iden‐
             tity files may also be specified on a per-host basis in the configuration file.  It is pos‐
             sible to have multiple -i options (and multiple identities specified in configuration
             files).  If no certificates have been explicitly specified by the CertificateFile directive,
             ssh will also try to load certificate information from the filename obtained by appending
             -cert.pub to identity filenames.

## ssh-keygen



## scp

来源: `man scp`  

-i identity_file  
               Selects the file from which the identity (private key) for public key authentication is read.  This option is directly passed to ssh(1).  

`scp /home/ff/.ssh/id_rsa.pub root@192.168.1.2:/root/myKey/` : 将本地文件 `/home/ff/.ssh/id_rsa.pub` 上传到服务器的 `/root/myKey/` 目录下  
`scp -i /home/ff/.ssh/id_ed25519 root@my.blog.ff.com:/var/log/auth.log /home/ff/tempFF/` : 使用私钥文件连接服务器 my.blog.ff.com，将服务器的 `/var/log/auth.log` 文件下载到本地的 `/home/ff/tempFF/` 目录下。  

## chkconfig

chkconfig firewalld  

## wget

命令格式: wget [参数] [URL地址]  

`wget URL` : 使用 wget 下载单个文件  

## curl

-x, --proxy [protocol://]host[:port] Use this proxy
-L, --location      Follow redirects

## alias

来源: SCCC教材  

无参数时列出系统已定义的别名  

`alias mand="less /etc/man_db.conf"` 可以用单引号 : 创建命令 mand 的别名  

在 ~/.bashrc 中添加一行 `alias name="value"` 即可默认加载所需 alias  

## unalias

来源: SCCC教材  

取消别名的定义  

`unalias mand` : 取消 mand 的别名  

## hostname

## hostnamectl

`hostnamectl set-hostname CentOS` : 修改主机名  

## tty

来源: `how tty`  

显示连接到当前标准输入的终端设备文件名  

- 显示连接到当前标准输入的终端设备文件名，当标准输入不是终端时打印 "not
a tty"。  

## chsh

Usage:
 chsh [options] [<username>]

Change your login shell.

Options:
 -s, --shell <shell>  specify login shell  
 -l, --list-shells    print list of shells and exit  
 -u, --help           display this help  
 -v, --version        display version  

示例:  
`chsh -s $(which zsh)` : 将默认的 shell 设置为 zsh  

## locale

手动编辑 /etc/locale.conf  

`locale --help`  
-a, --all-locales          写出可用区域的名称  

## localectl

`man localectl` , `localectl --help`  
localectl [OPTIONS...] COMMAND ...  
localectl [OPTIONS...] {COMMAND}  


`localectl --help`  
list-locales             Show known locales  


`localectl status`  
`localectl list-locales | grep zh_CN`  

## iostat

来源: https://www.cnblogs.com/ftl1012/p/iostat.html

cpu属性值说明:  
%user：CPU处在用户模式下的时间百分比。  
%nice：CPU处在带NICE值的用户模式下的时间百分比。  
%system：CPU处在系统模式下的时间百分比。  
%iowait：CPU等待输入输出完成时间的百分比。  
%steal：管理程序维护另一个虚拟处理器时，虚拟CPU的无意识等待时间百分比。  
%idle：CPU空闲时间百分比。  

## lsof

`ls -i`: 查看当前

## 系统信息

### uname

`uname -a`  

## 网络设备与网络连接

### netstat

-a, --all                display all sockets (default: connected)  
-n, --numeric            don't resolve names  
-o, --timers             display timers  
-p, --programs           display PID/Program name for sockets  

`netstat -ano` : 查看端口情况. 同样适用于 Windows  

常用举例 `netstat -ano | grep 80`。  

来源: `how netstat`

netstat 命令 用来打印 Linux 中网络系统的状态信息，可让你得知整个 Linux 系统的网络情况。  


### netcat

参考资料:  
[扫盲 netcat&#65288;网猫&#65289;的 N 种用法&#8212;&#8212;从&#8220;网络诊断&#8221;到&#8220;系统入侵&#8221; @ 编程随想的博客](https://program-think.blogspot.com/2019/09/Netcat-Tricks.html)  

`-v` : 如果你是 netcat 的新手，俺建议总是带上这个选项——通过更详细的输出，能帮你搞明白状况。  
`-n` : 由于测试的是 IP 地址，用该选项告诉 netcat，无须进行域名（DNS）解析；反之，如果你要测试的主机是基于域名，就不能用“选项 `-n`”。  
`-u` : 通常情况下，要测试的端口都是 TCP 协议的端口；如果你碰到特殊情况，需要测试某个 UDP 的端口是否可达。netcat 同样能胜任。只需要追加 `-u` 选项。  
`-w` : 在测试链接的时候，如果你没使用 `-w` 这个超时选项，默认情况下 netcat 会等待很久，然后才告诉你连接失败。如果你所处的网络环境稳定且高速（比如：局域网内），那么，你可以追加“`-w` 选项”，设置一个比较小的超时值。在下面的例子中，超时值设为 3 秒。`nc -nv -w 3 127.0.0.1 443`  

`nc -nv x.x.x.x xx` : 用这个命令可以测试某个 IP 地址（x.x.x.x）上的某个监听端口（xx）是否开启。

使用 netcat 进行文件传输: 先在接收端主机（IP 为 `192.168.8.1`）运行 `nc -l -p 12345 > file2`（使用 `12345` 端口号），然后在发送端主机（IP 为 `192.168.8.2`）运行 `nc 192.168.8.1 12345 < file1`（端口号为接收端主机的 netcat 对应端口号）。  

### ifconfig

来源: <https://cloud.tencent.com/developer/article/2155987>

`ifconfig ens160`  
`ifconfig ens160 down` : 卸载网卡 ens160  
`ifconfig ens160 up` : 重新加载网卡 ens160  
`ifconfig ens224 192.168.142.3/24` : 临时配置 IP 地址, 重启后失效  
`ifconfig ens224 192.168.142.3 netmask 255.255.255.0` : 临时配置 IP 地址, 重启后失效  

### ifup

`ifup ens160`  

### ifdown

`ifdown ens160`  


### ping

`man ping`  

-b           Allow pinging a broadcast address.  

### traceroute



### route

`man route`  

-n     show  numerical  addresses instead of trying to determine symbolic host names. This is useful if you are trying to determine why the route to your nameserver has vanished.  

`route`  
`route -n`  
`route add default gw 192.168.142.3` : 添加默认网关  

### nmcli

来源: SCCC教学, `how nmcli`  

`nmcli device status` : 显示状态  
`nmcli connection show` : 查看当前连接状态  
`nmcli connection show ens160`  
`nmcli connection up ens160`  
`nmcli connection down ens160`  
`nmcli connection delete ens160`  
`nmcli connection reload` : 查看当前连接状态  
`nmcli device status` : 显示设备状态  
`nmcli device show` : 显示全部接口属性  
`nmcli device wifi list`  
`nmcli device wifi connect`  

### brctl

来源: `man brctl`, <https://ipcmen.com/brctl>  

brctl - ethernet bridge administration  

brctl命令用于设置、维护和检查linux内核中的以太网网桥配置。  
以太网网桥是一种设备，通常用于将以太网的不同网络连接在一起，以便这些以太网对参与者显示为一个以太网。所连接的每个以太网对应于网桥中的一个物理接口。这些单独的以太网被聚集成一个更大的（“逻辑”）以太网，这个更大的以太网对应于网桥网络接口。  

语法格式：brctl [参数] <bridge>  

### 防火墙配置

##### firewall-cmd

`firewall-cmd --help`  
--state              Return and print firewalld state  
--reload             Reload firewall and keep state information  
--zone=<zone>        Use this zone to set or query options, else default zone  
                     Usable for options marked with [Z]  
--list-ports         List ports added [P] [Z] [O]  
--add-port=<portid>[-<portid>]/<protocol>  
                     Add the port [P] [Z] [O] [T]  
--remove-port=<portid>[-<portid>]/<protocol>  
                     Remove the port [P] [Z] [O]  

##### ufw

`ufw status`: 查看 ufw 的状态. 也能查看已经放行的端口  
`ufw allow 'Nginx Full'` : 允许 Nginx Full  
`ufw allow 22`: 新建规则以开放 22 端口  
`ufw delete allow 22`: 删除 `allow 22` 规则  
`ufw app list` : app list  

## 用户和组

相关文件:  
/etc/passwd  
/etc/group  
/etc/shadow  

### who

来源: SCCC-职教云, `how who`  

查看当前登录主机用户终端信息  
显示当前所有登陆用户的信息。  

- 当没有给出非选项参数时，按以下字段顺序为每个当前用户打印信息：登录用户名称，终端信息，登录时间，远程主机或 X display。  
- 当用户执行 `who am i` 时，只显示运行该命令的用户的信息。  

### id

`id --help`  
Usage: id [OPTION]... [USER]  

`how id`  
打印真实以及有效的用户和所在组的信息  
没有选项时，打印指定用户 id 信息。  

`id`  

### w

`man w`  
w - Show who is logged on and what they are doing.  

### last

来源: SCCC-职教云

查看当前和过去登陆系统用户的相关信息。

可以借助该命令查看 VPS 的 SSH 登录日志对应 IP。

### useradd

来源: `useradd --help`  
-d, --home-dir HOME_DIR       新账户的主目录  
-d, --home-dir HOME_DIR       home directory of the new account  
-D, --defaults                显示或更改默认的 useradd 配置  
-D, --defaults                print or change default useradd configuration  
-u, --uid UID                 新账户的用户 ID  
-u, --uid UID                 user ID of the new account  
-g, --gid GROUP               新账户主组的名称或 ID  
-g, --gid GROUP               force use GROUP as new primary group  
-m, --create-home     创建用户的主目录  
-m, --create-home             create the user's home directory  
-M, --no-create-home          不创建用户的主目录  
-M, --no-create-home          do not create the user's home directory  

来源: SCCC 教学  
-g 组名: 手工指定用户的初始组. 一般以和用户名相同的组作为用户的初始组, 在创建用户时会默认建立初始组. 一旦手动指定, 则系统将不会在创建此默认的初始组目录.  


来源: `how useradd`  

创建的新的系统用户  

useradd 命令 用于 Linux 中创建的新的系统用户。useradd 可用来建立用户帐号。帐号建好之后，再用 passwd 设定帐号的密码．而可用 userdel 删除帐号。使用 useradd 指令所建立的帐号，实际上是保存在/etc/passwd 文本文件中。  
在 Slackware 中，adduser 指令是个 script 程序，利用交谈的方式取得输入的用户帐号资料，然后再交由真正建立帐号的 useradd 命令建立新用户，如此可方便管理员建立用户帐号。在 Red Hat Linux 中， adduser 命令 则是 useradd 命令的符号连接，两者实际上是同一个指令。  

`useradd lutixia` : 新建一个普通用户  

-d : `useradd -d /company/yf/yf01 yf01` 此处使用 -d 选项需要注意, /company/yf/ 目录需存在, /company/yf/yf01 目录可以不存在. 如果 /company/yf/yf01 目录不存在, 则会自动创建并初始化, 初始化文件 .bashrc, .bash_profile 等.  

### userdel

来源: `userdel --help`  
-r, --remove                  删除主目录和邮件池  
-r, --remove                  remove home directory and mail spool  

来源: SCCC教学  
`userdel –r lamp` : 删除用户 lamp 用户同时，删除家目录  

### usermod

`usermod --help`  
-G, --groups GROUPS           新的附加组列表 GROUPS  
-G, --groups GROUPS           new list of supplementary GROUPS  


来源: SCCC 教学  
`usermod -G testgroup lamp` : 用户 lamp 加入组 testgroup  

### groupadd

`groupadd --help`  
-g, --gid GID                 为新组使用 GID  

`groupadd sales` : 创建 sales 组  

### groupdel

`groupdel sales` : 删除 sales 组  

### groupmod

`groupmod --help`  
-n, --new-name NEW_GROUP      改名为 NEW_GROUP  
-n, --new-name NEW_GROUP      change the name to NEW_GROUP  
-g, --gid GID                 将组 ID 改为 GID  
-g, --gid GID                 change the group ID to GID  


SCCC 教学  
`groupmod -n newsales sales` : 给组重命名, 将 sales 重命名为 newsales  

### groupmems

`groupmems --help`  
Usage: groupmems [options] [action]  
Options:  
  -g, --group groupname         更改组 groupname，而不是用户的组(只 root)  
  -g, --group groupname         change groupname instead of the user's group  
                                (root only)  

Actions:  
  -a, --add username            将用户 username 添加到组成员中  
  -a, --add username            add username to the members of the group  
  -l, --list                    列出组中的所有成员  
  -l, --list                    list the members of the group  

参考: SCCC 教学  
`groupmems -g testgroup –l` : 显示 testgroup 组中的成员  
`groupmems -g testgroup -a rose` : 向 testgroup 中添加成员  
`groupmems -g testgroup -d rose` : 删除 testgroup 组中的成员  

### gpasswd

参考: `gpasswd --help`  
-a, --add USER                向组 GROUP 中添加用户 USER  
-a, --add USER                add USER to GROUP  
-d, --delete USER             从组 GROUP 中添加或删除用户  
                              FoliageForest: 可能有误  
-d, --delete USER             remove USER from GROUP  
-A, --administrators ADMIN,...        设置组的管理员列表  
-A, --administrators ADMIN,...  
                                set the list of administrators for GROUP  


参考: `less gpasswd`  
`-A` : 指定管理员  

参考: SCCC 教学  
`gpasswd testgroup` : 给组设置密码  
`gpasswd -A lamp testgroup` : 加入群组管理员 lamp. 将群组的控制权交给 lamp 用户管理, lamp 为群组的管理员, 仅 root 用户可用  
`gpasswd -a lamp testgroup` : 用户 lamp 加入组 testgroup  

### groups

### su

`su - ff` : 切换工作目录到 ff 的家目录  
`su ff` : 不切换工作目录  

### whoami

来源: `whoami --help`  

Print the user name associated with the current effective user ID.  

### passwd

来源: SCCC教学  
`passwd ff` : 为用户 ff 设置密码  
`echo "google" | passwd --stdin google` : 快速设置用户密码  

`passwd --help`  
Usage: passwd [OPTION...] <accountName>  
-d, --delete            删除命名帐户的密码（仅限 root
                          用户）；也删除密码锁（如果有）  
-d, --delete            delete the password for the named account (root
                          only); also removes password lock if any  
-S, --status            报告已命名帐号的密码状态(只有 root 用户才能进行此操作)  
-l, --lock              锁定指名帐户的密码(仅限 root 用户)  
-l, --lock              lock the password for the named account (root only)  
-u, --unlock            解锁指名帐户的密码(仅限 root 用户)  
-u, --unlock            unlock the password for the named account (root only)  
-e, --expire            终止指名帐户的密码(仅限 root 用户)  
-e, --expire            expire the password for the named account (root only)  

`man passwd`  
-d, --delete  
       This is a quick way to delete a password for an account. It will set the named account passwordless. Available to root only.  
       Note that if the password was locked, this implicitly removes the password lock as well.  


## 电源

### shutdown

来源: SCCC教材, `shutdown --help`, `how shutdown`  

-P --poweroff  Power-off the machine  
-r --reboot    Reboot the machine  
-h             Equivalent to --poweroff, overridden by --halt  

shutdown [选项] 时间 [警告信息]  

`-r` : 系统关闭后重新启动  
`-h` : 关闭系统  

`shutdown -h now` : 指定现在立即关机  

`shutdown +5 "System will shutdown after 5 minutes"` : 指定 5 分钟后关机，同时送出警告信息给登入用户  


时间:  
  `now` : 立即  
  `hh:mm` : 表示绝对时间, hh 表示小时, mm 表示分钟  
  `+m` : 表示 m 分钟后  

### poweroff

### halt

### reboot

## 磁盘和光盘

### fdisk

fdisk [options] device  
fdisk -l [device...]  

`fdisk --help`  
-l, --list                    显示分区并退出  
-l, --list
              List  the  partition  tables  for  the specified devices and then exit.  If no devices are given, those mentioned in /proc/partitions (if that  file  exists) are used.  

`fdisk /dev/nvme0n1`  
`fdisk -l`  

### mkfs

`mkfs.ext4 /dev/nvme0n2`  
`mkfs.xfs /dev/nvme0n7p1`  

### lsblk

`how lsblk`, `man lsblk`  
lsblk - list block devices  
-l, --list           使用列表格式的输出  
-l, --list           use list format output  
-f, --fs             输出文件系统信息  
-f, --fs             output info about filesystems  

`lsblk` : 列出块设备信息  

### blkid

blkid /dev/nvme0n1p1  

### cfdisk

来源: https://www.bilibili.com/video/BV1w541157Uo/?spm_id_from=333.337.search-card.all.click&vd_source=4c689340250a54b505efbbe1062f94cf  

`cfdisk /dev/nvme0n1`  

### eject

`how eject`  

用来退出抽取式设备  

-r 或--cdrom: 退出光盘  

### mount

`mount --help`  
-f, --fs             输出文件系统信息  
-f, --fs             output info about filesystems  
-a, --all               挂载 fstab 中的所有文件系统  
-a, --all               mount all filesystems mentioned in fstab  

来源: `how mount`  

`mount /dev/hda1 /mnt` : 将 /dev/hda1 挂在 /mnt 之下  
`mount -o ro /dev/hda1 /mnt` : 将 /dev/hda1 用唯读模式挂在 /mnt 之下  
`mount -o loop /tmp/image.iso /mnt/cdrom` : 将 /tmp/image.iso 这个光碟的 image 档使用 loop 模式挂在 /mnt/cdrom 之下。用这种方法可以将一般网络上可以找到的 Linux 光碟 ISO 档在不烧录成光碟的情况下检视其内容。  

来源: SCCC 教学  

`mount /dev/sr0 /mnt` : 将光盘挂载到 /mnt 目录  

来源: <https://developer.aliyun.com/article/331194>

`mount -t iso9660 /dev/cdrom /media/cdrom` : 挂载光盘  

使用 `df -h` 可以查看是否挂载成功  

### umount

来源: `how umount`  

下面两条命令分别通过设备名和挂载点卸载文件系统，同时输出详细信息：  
* 通过设备名卸载  
  `umount /dev/nvme0n2p1`  
  `umount -v /dev/sda1`  
  `/dev/sda1 umounted`  
* 通过挂载点卸载  
  `umount /mnt/mymount/`  
  `umount -v /mnt/mymount/`  
  `/tmp/diskboot.img umounted`  

### mdadm

`man mdadm`  
-D, --detail  
       Print details of one or more md devices.  
-s, --scan  
       Scan config file or /proc/mdstat for missing information.  In general, this option gives mdadm permission  to  get
       any  missing information (like component devices, array devices, array identities, and alert destination) from the
       configuration file (see previous option); one exception is MISC mode when using --detail or --stop, in which  case
       --scan says to get a list of array devices from /proc/mdstat.
-A, --assemble  
       Assemble a pre-existing array.  
-S, --stop  
       deactivate array, releasing all resources.  


《Linux就该这么学》  
mdadm -Q /dev/md0  
mdadm -D /dev/md10  

《Linux就该这么学》  
`mdadm -Cv /dev/md0 -n 4 -l 10 /dev/sdb /dev/sdc /dev/sdd /dev/sde` : -C 参数代表创建一个 RAID 阵列卡, -v 参数显示创建的过程, /dev/md0 是创建后的 RAID 磁盘阵列的名称, -n 4 参数代表使用 4 块硬盘来部署这个 RAID 磁盘阵列, -l 10 参数则代表 RAID 10 方案, 后接 4 块硬盘设备  

## 系统监控

### free

一般直接 `free -h` 即可  

来源:  
- SCCC-职教云
- `free --help`

查看内存信息，包括物理内存，虚拟内存、共享内存和系统缓存  
-h, --human         show human-readable output  

### df

`how df`  
用于显示磁盘分区上的可使用的磁盘空间  

df --help  

Usage: df [OPTION]... [FILE]...
Show information about the file system on which each FILE resides, or all file systems by default.

-i, --inodes          list inode information instead of block usage  
-i, --inodes          显示 inode 信息而非块使用量  
-h, --human-readable  print sizes in powers of 1024 (e.g., 1023M)  
-h, --human-readable  以 1024 进制的单位显示大小（例如：1023M）  
-H, --si              print sizes in powers of 1000 (e.g., 1.1G)  
-H, --si              以 1000 进制的单位显示大小（例如：1.1G）  
-T, --print-type      print file system type  
-T, --print-type      显示文件系统类型  
-k                    like --block-size=1K  
-k                    等于 --block-size=1K  


来源: <https://gnu-linux.readthedocs.io/>

`df -i` : 查看每个硬盘分区的 inode 总数和已经使用的数量  
`df -h /etc` : 将 /etc 底下的可用的磁盘容量以易读的容量格式显示  

### du

Summarize disk usage of the set of FILEs, recursively for directories.  

`du --help`  
-h, --human-readable  print sizes in human readable format (e.g., 1K 234M 2G)  
-s, --summarize       display only a total for each argument  

`du -h`  
`du -h ./virtio-win-0.1.266.iso`  
`du --human-readable /usr/` : 查看 /usr/ 目录的大小  

## 进程管理

### ps

`man ps`  
ps - report a snapshot of the current processes.  

来源: `how ps`, `ps --help`  

-A, -e               all processes  
-f                   full-format, including command lines  

`ps -ef` : 显示所有进程信息，连同命令行  
`pa aux`  
    `ps aux | grep msfconsole`  

### top

`小飞侠Geek`  
使用 top 找到占用资源比较多的进程  
动态查看进程, 默认每 5 秒钟刷新一次  

`?`  
`H` : 同 `?`  

`man top`  
top - display Linux processes  



### kill

`kill -9 processId` : 杀掉某个进程  


## 环境变量

来源: https://www.freecodecamp.org/chinese/news/how-to-set-an-environment-variable-in-linux/

USER - 这指的是当前登录的用户。  
HOME - 这显示了当前用户的主目录。  
SHELL - 这存储了当前用户的 shell 路径，如 bash 或 zsh。  
LANG - 这个变量指向当前的语言 /locales 设置。  
MAIL - 这显示了当前用户的邮件存储的位置。  

`env` : 用于显示为当前会话定义的所有环境变量  
`printenv`  

打印已经定义的环境变量:  
- `printenv VARIABLE_NAME`  
  例如: `printenv SHELL`  
- `echo $varname`  
  例如: `echo $SHELL`  

定义环境变量: `export VARIABLE_NAME=value`, 例如 `export JAVA_HOME=/usr/bin/java`

# 软件包

## rpm

来源: SCCC 教学, `rpm --help`, `how rpm`  

-i, --info  
       Display package information, including name, version, and description.  This uses the --queryformat if one was specified.  
-q : 使用询问模式，当遇到任何问题时，rpm 指令会先询问用户  
-f, --file                         query/verify package(s) owning installed file  
-l, --list                         List files in package.  


`rpm -qa` : 查看系统安装所有软件包  
`rpm -q openssh` : 获得某个软件包的文件全名  
  可以获得系统中安装的 mysql 软件包全名, 从中可以获得当前软件包的版本等信息. 这个例子中可以得到信息 mysql-3.23.54a-11  
`rpm -qi openssh` : 查看包的信息  
`rpm -ql 包名` : 一个 rpm 包中的文件安装到那里去了  
  注意这里的是不包括.rpm 后缀的软件包的名称, 也就是说只能用 mysql 或者 mysql-3.23.54a-11 而不是 mysql-3.23.54a-11.rpm。如果只是想知道可执行程序放到那里去了, 也可以用 which, 比如: which mysql  
某个程序是哪个软件包安装的，或者哪个软件包包含这个程序  
  `rpm -qf $(which 程序名)` : 返回软件包的全名  
  `rpm -qif $(which 程序名)` : 返回软件包的有关信息  
  `rpm -qlf $(which 程序名)` : 返回软件包的文件列表  

## yum

`yum list` : 显示所有已经安装和可以安装的程序包  
`yum update` : 全部更新  

## dnf

> dnf命令来自英文词组“Dandified YUM”的缩写，是新一代的软件包管理器，其功能是用于安装、更新、卸载Linux系统中的软件。最初应用于Fedora 18系统中，目标非常明确的想要解决掉yum命令的诸多瓶颈问题，例如占用大量内存、臃肿的软件依赖关系、运行速度缓慢等等诟病。

install  
  `dnf install httpd` : 安装指定的软件  
  -y  
  `dnf install httpd -y` : 安装指定的软件，且无需二次确认  


参考链接：https://www.linuxcool.com/dnf

## apt

`apt install wget` : 安装软件包, 此处为 wget  
`apt install wget -y` : 通常使用 apt 命令安装软件包时都会提示占用空间的大小，并确认是否继续安装，如果你想跳过此提示，可以指定 apt 命令的 -y 选项  
`sudo apt remove package-name-1 package-name-2` : 删除软件包  
`apt update` : 从 APT 软件源中获取最新索引数据  
`apt upgrade` : 更新系统的软件包  
`apt upgrade wget` : 更新单个软件包, 此处为 wget  


# 日期和时间

## date

date --help

Usage: date [OPTION]... [+FORMAT]
  or:  date [-u|--utc|--universal] [MMDDhhmm[[CC]YY][.ss]]

设置、显示、修改时间

`-s` : 设置时间. `date -s 18:19:33` 能设置系统时间  

%Y   year  
%m   month (01..12)  
%d   day of month (e.g., 01)  
%H   hour (00..23)  
%M   minute (00..59)  
%S   second (00..60)  
%F   full date; same as %Y-%m-%d  
%T   time; same as %H:%M:%S  

示例:  
`date +%Y-%m-%d` 或者 `date +"%Y-%m-%d"` 或 `date "+%Y-%m-%d"` , 也可以把双引号改为单引号  

## cal

显示指定月份或年份的日历

`cal 7 2019` : 查看 2019 年 7 月的日历  

# 实用工具

## watch



# 其他

## 后台运行

