# 第 6 章 进程皆有资源限制

|本期版本| 上期版本
|:---:|:---:
`Mon Aug  5 12:26:15 CST 2024` | `Sat May  7 22:32:00 CST 2022`


### 6.1 找出限制

* [`Process.getrlimit`](https://docs.ruby-lang.org/en/3.1/Process.html#method-c-getrlimit)
* 数组的第一个元素是软限制（soft limit）,第二个元素是硬限制（hard limit）

### 6.2 软限制与硬限制

* 任何进程都可以修改自身的软限制，只有超级用户能修改硬限制
* 如果你对更改系统级别的限制感兴趣，可以查看 `sysctl(8)`

### 6.3 提高软限制

* [`Process.setrlimit`](https://docs.ruby-lang.org/en/3.1/Process.html#method-c-setrlimit)

### 6.4 超出限制

* 如果超出了软限制，则会抛出 `Errno::EMFILE` 异常

### 6.7 系统调用

* `getrlimit(2)`、`setrlimit(2)`


## Ref

* [Linux 系统参数调整：ulimit 与 sysctl - 於清樂 - 博客园](https://www.cnblogs.com/kirito-c/p/12254664.html)