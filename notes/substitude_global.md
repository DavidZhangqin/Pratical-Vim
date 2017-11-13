## 替换substitude和global命令
========================

### 替换

:[range]s[ubstitude]/{pattern}/{string}/[flags]

#### 标志位flags

- g 全文
- c 确认
- n 抑制替换
- e 屏蔽错误
- & 重用上次使用的标志位

#### 替换域

- \r \t \\
- \1 \2 \0(匹配模式所有内容)
- &=\0 ~上一次重用
- \={vim script} 执行vim表达式
- `%s//{string}/g`
- `%s//<C-r>0/g` `%s//\=@0/g` 复制内容替换
- `s/target/replacement/g` `g& == :%s//~/&` 对所有行重复上次替换操作
- `'<,'>&&` 新的范围重复执行替换
- `/\v^(xx),(xx),(xx)$` `:%s//\3\2\1` 列替换

#### 例子

1. <h2> => <h1> </h2> => </h1>

```
/\v<\/?h\zs\d
:%s//\=submatch(0)-1/g
```

2. The dog hit the man.   dog <=> man

```
:let swapper={"dog":"man","man":"dog"}
:echo swapper["dog"]
/\v(<man>|<dog>)
:%s//\={"dog":"man","man":"dog"}[submatch(1)]/g
:%s//swapper[submatch(1)]/g
```

#### 多文件执行

```
:args **/*.txt
set hidden
/Pragmatic\ze Vim
:argdo %s//Practical/ge

检查:
/Pragmatic\ze Vim
:vimgrep /<C-r>// **/*.txt

:argdo update
:argdo %s//Practical/ge | update
```

### global命令

:[range]g[lobal][!]/{pattern}/[cmd]

- `:g/re/p` 刚好是grep，即grep的由来
- `:g/re/d` 删除
- `:v/re/d` 保留匹配行 :vglobal
- :print 是global缺省[cmd]

#### 把包含TODO的所有行添加到寄存器a后

```
qaq 删除a寄存器内容
:g/TODO/y[ank] A
:reg a
```

#### 其他例子

```
:g/TODO/t$ 把所有TODO复制到文件末尾
:g/{/.+|,/}/-1 sort css文件属性按字母排序
```

