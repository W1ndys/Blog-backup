---
title:  CTF-crypto&misc常用解密工具
tags:  CTF
categories:  [CTF,工具]

---

# 编码解码

## Python脚本

### 比较两个字符串输出不同的部分

```
def compare_strings(str1, str2):
    str11 = ""
    str12 = ""
    for i in range(min(len(str1), len(str2))):
        if str1[i] != str2[i]:
            str11+=str1[i]
            str12+=str2[i]
    print(str11)
    print(str12)
# 定义两个字符串
str1 = "第一个字符串"
str2 = "第二个字符串"

# 调用函数
compare_strings(str1, str2)
```

### 删除所有回车

```
text = "你的文本\n包含\n回车"
new_text = text.replace("\n", "")
print(new_text)
```

## 在线工具包

- [Cyberchef的自动解密magic模式](https://ctf.mzy0.com/CyberChef3/#recipe=Magic(3,false,false,''))

> 自动解密base等编码，很方便

- [CyberChef (mzy0.com)](https://ctf.mzy0.com/CyberChef3/)

> Cyberchef的主站，功能强大，非常推荐

- [Bugku在线工具](https://ctf.bugku.com/tools)

> Bugku的在线工具包，也很齐全

- [一个工具箱 - 好用的在线工具都在这里！ (atoolbox.net)](http://www.atoolbox.net/)

## Bugku在线工具包分包

### 编码

#### base家族

Base100编码解码https://ctf.bugku.com/tool/base100

Base92编码解码https://ctf.bugku.com/tool/base92

Base91编码解码https://ctf.bugku.com/tool/base91

Base85编码解码https://ctf.bugku.com/tool/base85

Base64编码解码https://ctf.bugku.com/tool/base64

Base62编码解码https://ctf.bugku.com/tool/base62

Base58编码解码https://ctf.bugku.com/tool/base58

Base32编码解码https://ctf.bugku.com/tool/base32

Base16编码解码https://ctf.bugku.com/tool/base16

#### 其他

核心价值观编码https://ctf.bugku.com/tool/cvecode

### 解密

与佛论禅密码https://ctf.bugku.com/tool/todousharp

#### JS

Brainfuck/OoKhttps://ctf.bugku.com/tool/brainfuck

Sojson.v5解密https://ctf.bugku.com/tool/sojson5

Sojson.v4 解密https://ctf.bugku.com/tool/sojson4

### 古典密码

UUencodehttps://ctf.bugku.com/tool/uuencode

XXencode密码https://ctf.bugku.com/tool/xxencode

维基利亚密码https://ctf.bugku.com/tool/vigenere

希尔密码https://ctf.bugku.com/tool/hill

栅栏密码https://ctf.bugku.com/tool/railfence

凯撒密码https://ctf.bugku.com/tool/caesar

ADFGX密码https://ctf.bugku.com/tool/adfgx

### 3DES/CryptoJS/TripleDes

TripleDes(3DES)https://ctf.bugku.com/tool/tripledes



# 

工具很多

------

持续更新中……

