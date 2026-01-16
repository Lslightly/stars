---
tags:
    - Go
---

# [goref](https://github.com/cloudwego/goref)

首先在根目录 `go install ./cmd/grf`

在 [`test/testdata/mockleak`](https://github.com/Lslightly/goref/tree/373c1be867ff466b27ca24d7c52b9b3211393719/test/testdata/mockleak) 目录下执行如下命令

```bash
go build -gcflags="-N -l" .
./mockleak # 等待一分钟(通过cmds.AttachSelf函数实现50000次时导出)，或者grf attach该进程
go tool pprof -http=127.0.0.1:8080 grf.profile.gz
```

得到下图：

不同类型的对象的大小会被展示。对象之间的引用关系也会被展示。

![[attachments/Pasted image 20260116205231.png]]

top 如下：

![[attachments/Pasted image 20260116205501.png]]

flame graph:

![[attachments/Pasted image 20260116205601.png]]

source 视图展示的东西比较诡异。

![](attachments/Pasted%20image%2020260116205711.png)


