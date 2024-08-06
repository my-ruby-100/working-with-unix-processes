# 第 14 章 进程可待

|本期版本| 上期版本
|:---:|:---:
`Tue Aug  6 11:37:30 CST 2024` | `Sun May  8 09:55:23 CST 2022`


### 14.1 看顾（Babysitting)


* [`Process#wait`](https://docs.ruby-lang.org/en/3.1/Process.html#method-c-wait) 是一个阻塞调用，该调用使得父进程一直等到它的某个子进程退出之后才继续执行

### 14.2 Proceww.wait 一家子

* 会一直保持阻塞，直到其中任意一个子进程退出为止
* 返回退出的那个子进程的 pid

### 14.3 使用 Process.wait2 进行通信

* [`Process#wait2`](https://docs.ruby-lang.org/en/3.1/Process.html#method-c-wait2) 返回两个值（pid, status）

### 14.4 等待特定的子进程


* [`Process#waitpiad`](https://docs.ruby-lang.org/en/3.1/Process.html#method-c-waitpid)、[`Process#waitpid2`](https://docs.ruby-lang.org/en/3.1/Process.html#method-c-waitpid2)
* 不是等待任意的子进程退出，而是只等待由pid指定的子进程退出


### 14.5 竞争条件

* 内核将退出的进程信息加入队列，这样一来父进程就总是能够依照子进程退出的顺序接收到信息
* 如果不存在子进程，那么调用 `Process#wait` 的任一变体都会抛出 `Errno::ECHILD` 异常


### 14.6 实践领域

* 这种模式有时被称为看顾进程 master/worker 或者 preforking



### 14.7 系统调用

* `waitpid(2)`