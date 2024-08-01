# 第 3 章 进程皆有标识

|本期版本| 上期版本
|:---:|:---:
`Thu Aug  1 15:28:00 CST 2024` | `Sat May  7 21:53:59 CST 2022`

* 在系统中运行的所有进程都有一个唯一的进程标示符， 称为 `pid` 
* [`Process.pid`](https://docs.ruby-lang.org/en/3.2/Process.html#method-c-pid)、[`$$`](https://docs.ruby-lang.org/en/3.2/globals_rdoc.html)

### 3.1 交叉参考

```ruby
puts Process.pid
```

```bash
ps -p 5349
```

### 3.2 实践领域

```bash
top -pid 5349
```

```bash
lsof -p 5349
```

```bash
htop -p 4273
```


### 3.3 系统调用

* `getpid(2)`