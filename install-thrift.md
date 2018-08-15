

#### 下载

- 我这里用的是thrift 0.10.0 , 不是最新的 0.11.0 ， 这个两个非常的不兼容，一定要注意，thrift 0.11.0的server handler的函数实现时要加一个非常怪异的 context.Context参数，但是并不清楚这个参数在服务接口中有什么用处。
- thrift 0.10.0 不知道支不支持PHP7 如果不支持PHP7 就切换到 thrift-0.11.0

```shell
wget http://mirrors.shu.edu.cn/apache/thrift/0.11.0/thrift-0.11.0.tar.gz
```

#### 安装
- 如果有golang语言需要翻墙
- 带nodejs会导致编译不通过


###### 带golang --> 后来经过尝试验证，这里面其实是缺了两个包，我们需要手动安装。
```shell
wget https://codeload.github.com/golang/net/zip/master
unzip net-master.zip
mkdir -p /home/golang/src/golang.org/x/net/
cp -r net-master/* /home/golang/src/golang.org/x/net/
go install net

wget https://codeload.github.com/golang/mock/zip/master
unzip mock-master.zip
mkdir -p /home/golang/src/github.com/golang/mock
cp -r mock-master/* /home/golang/src/github.com/golang/mock/
go install github.com/golang/mock/gomock
```

```shell
./configure --with-boost=/usr/local/thrift --without-nodejs --without-go
make
make check
sh test/test.sh
make install
```

