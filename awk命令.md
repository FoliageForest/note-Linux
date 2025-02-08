-F value         sets the field separator, FS, to value.  

- 基本用法:  
  - `awk '{print $0}' demo.txt` : 该实例中， `demo.txt` 是 `awk` 所要处理的文本文件。前面单引号内部有一个大括号，里面就是每一行的处理动作 `print $0`。其中， `print` 是打印命令，`$0` 代表当前行，因此上面命令的执行结果，就是把每一行原样打印出来。  
  - `echo 'this is a test' | awk '{print $0}'` : `print $0` 就是把标准输入 `this is a test`，重新打印了一遍。  
  - `echo 'this is a test' | awk '{print $3}'`: `awk` 会根据空格和制表符，将每一行分成若干字段，依次用 `$1`、`$2`、`$3` 代表第一个字段、第二个字段、第三个字段等等。该代码中，`$3` 代表 `this is a test` 的第三个字段 `a`。  
  - `awk -F ':' '{ print $1 }' demo.txt` : 为了便于举例，我们把 `/etc/passwd` 文件保存成 `demo.txt`。这个文件的字段分隔符是冒号（`:`），所以要用 `-F` 参数指定分隔符为冒号。然后，才能提取到它的第一个字段。  

- 变量:  
  - `echo 'this is a test' | awk '{print $NF}'` : 除了 `$ + 数字` 表示某个字段，`awk` 还提供其他一些变量。变量 `NF` 表示当前行有多少个字段，因此 `$NF` 就代表最后一个字段。  
  - `awk -F ':' '{print $1, $(NF-1)}' demo.txt` : `$(NF-1)` 代表倒数第二个字段。该代码中，`print` 命令里面的逗号，表示输出的时候，两个部分之间使用空格分隔。  
  - `awk -F ':' '{print NR ") " $1}' demo.txt` : 变量 `NR` 表示当前处理的是第几行。该代码中，`print` 命令里面，如果原样输出字符，要放在双引号里面。  

- 函数:  
`awk -F ':' '{ print toupper($1) }' demo.txt` : 函数 `toupper()` 用于将字符转为大写。该代码中，第一个字段输出时都变成了大写。  

- 条件:  
  - `awk -F ':' '/usr/ {print $1}' demo.txt` : `awk` 允许指定输出条件，只输出符合条件的行。输出条件要写在动作的前面。该代码中，`print` 命令前面是一个正则表达式，只输出包含 `usr` 的行。  
  - `awk -F ':' 'NR % 2 == 1 {print $1}' demo.txt` : 只输出奇数行。  
  - `awk -F ':' 'NR >3 {print $1}' demo.txt` : 输出第三行（不包括第三行）以后的行。  
  - `awk -F ':' '$1 == "root" {print $1}' demo.txt` : 输出第一个字段等于指定值的行。  
  - `awk -F ':' '$1 == "root" || $1 == "bin" {print $1}' demo.txt` : 输出第一个字段等于指定值的行。  

- if 语句:  
  - `awk -F ':' '{if ($1 > "m") print $1}' demo.txt` : `awk` 提供了 `if` 结构，用于编写复杂的条件。上面代码输出第一个字段的第一个字符大于 `m` 的行。  



`man awk`  
`awk --help`  
参考(一字不漏地): https://www.ruanyifeng.com/blog/2018/11/awk.html  
