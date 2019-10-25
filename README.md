# 日常笔记

## MD5值计算

Windows下面的命令：
```
certutil -hashfile filename MD5
certutil -hashfile filename SHA1
certutil -hashfile filename SHA256
```

## kaggle-api

```
# 下载kernel到本地目录
kaggle kernels pull go1dfish/clear-mask-visualization-and-simple-eda -p ./
```

##  pip源设置

```
http://pypi.douban.com/simple/ 豆瓣
http://mirrors.aliyun.com/pypi/simple/ 阿里
http://pypi.hustunique.com/simple/ 华中理工大学
http://pypi.sdutlinux.org/simple/ 山东理工大学
http://pypi.mirrors.ustc.edu.cn/simple/ 中国科学技术大学
https://pypi.tuna.tsinghua.edu.cn/simple 清华
```

## Python

```

int(x [,base ])         将x转换为一个整数  
long(x [,base ])        将x转换为一个长整数  
float(x )               将x转换到一个浮点数  
complex(real [,imag ])  创建一个复数  
str(x )                 将对象 x 转换为字符串  
repr(x )                将对象 x 转换为表达式字符串  
eval(str )              用来计算在字符串中的有效Python表达式,并返回一个对象  
tuple(s )               将序列 s 转换为一个元组  
list(s )                将序列 s 转换为一个列表  
chr(x )                 将一个整数转换为一个字符  
unichr(x )              将一个整数转换为Unicode字符  
ord(x )                 将一个字符转换为它的整数值  
hex(x )                 将一个整数转换为一个十六进制字符串  
oct(x )                 将一个整数转换为一个八进制字符串  
```

```
/root/.pip/pip.conf

[global]  
index-url=http://mirrors.aliyun.com/pypi/simple/  
[install]  
trusted-host=mirrors.aliyun.com
```

## 设置零时tmp文件夹

```
export TMPDIR=$HOME/tmp
```

## Deep Learning

- https://github.com/Cadene/pretrained-models.pytorch
- https://github.com/lukemelas/EfficientNet-PyTorch
- https://github.com/open-mmlab/mmdetection

```
# 设置pytorch本地缓存文件夹
export TORCH_MODEL_ZOO="/home/liuyuzhong/.torch/"
export TORCH_HOME="/home/liuyuzhong/.torch/"
```

## 数据科学

- ks_2samp: https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.ks_2samp.html


## Pytorch

```
# F2-loss
def f2_loss(logits, labels):
    __small_value=1e-6
    beta = 2
    batch_size = logits.size()[0]
    p = F.sigmoid(logits)
    l = labels
    num_pos = torch.sum(p, 1) + __small_value
    num_pos_hat = torch.sum(l, 1) + __small_value
    tp = torch.sum(l * p, 1)
    precise = tp / num_pos
    recall = tp / num_pos_hat
    fs = (1 + beta * beta) * precise * recall / (beta * beta * precise + recall + __small_value)
    loss = fs.sum() / batch_size
    return (1 - loss)
```
