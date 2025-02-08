参考教程 https://developer.aliyun.com/adc/scenario/c8d3efc90d634366bc012a69129c9aef  

`echo $SHELL` : 打印输出当前系统环境使用的 shell 解析器类型  

注意 `echo HOME` 与 `echo $HOME` 的区别

shell 脚本注释格式  

```shell
# 注释内容
```

`chmod a+x helloworld.sh` : 添加可执行权限  

`echo "b ai'd u"`  
`echo 'b ai"d u'`  

`var1=Linux` : var1 与等号之间, 等号与 Linux 之间, 都不能有空格, 也可以这样用 `var1="Li nux"`  
`echo $var1` : 这样输出变量的值  

`export name="Tom"` : 在 shell 环境中定义一个临时变量 name  

使用场景:  
`export https_proxy=http://192.168.178.1:10809 http_proxy=http://192.168.178.1:10809 all_proxy=socks5://192.168.178.1:10808` : 暂时定义代理, 来源 <https://zhuanlan.zhihu.com/p/115450863>  

```
echo `export` > echoExport.txt
```

还可以这样使用 `echo $(pwd)`

测试题: [https://www.bilibili.com/video/BV17T4y1F7WV/?p=4&spm_id_from=pageDriver&vd_source=4c689340250a54b505efbbe1062f94cf]  
已知目录 /root/itheima 目录, 执行 batch.sh 脚本, 实现在 /root/itheima 目录下创建一个 one.txt, 在 one.txt 文件中增加内容 "Hello Shell"。  

