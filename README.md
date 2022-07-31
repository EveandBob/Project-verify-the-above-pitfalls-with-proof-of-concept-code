#写在之前
项目中用到的函数简介：https://github.com/EveandBob/Introduction-to-some-functions-in-elliptic-curves-not-projects-

# 项目名称
当A和B选择的k相同时，A和B能互相知道对方的私钥

# 项目内容
这里面当A和B选择的K相同时，通过下面算法可以知道互相的私钥

![Screenshot 2022-07-31 124054](https://user-images.githubusercontent.com/104854836/182013632-9f13e5b7-b1aa-4cfd-a171-e1fe247e3d83.jpg)
# 部分代码

```python
def ALice_sign(msg,IDA):
    print("ALice的公钥为：")
    r,s=sign(msg, IDA)
    return r,s

#Bob的K：0x6CB28D99385C175C94F94E934817663FC176D925DD72B727260DBAAE1FB2F96F
#Bob 获取私钥并且签名：
def Bob_sign(msg,IDB):
    print("Bob的公钥为：")
    r,s=sign(msg, IDB)
    return r,s


def get_sK_wen_Alice_and_Bob_has_the_one_k(msg,IDA,IDB):
    k = 0x6CB28D99385C175C94F94E934817663FC176D925DD72B727260DBAAE1FB2F96F
    A_r, A_s=ALice_sign(msg,IDA)
    B_r, B_s = Bob_sign(msg, IDB)
    DA=((k-A_s)*get_inverse(A_r+A_s,n))%n
    DB=((k-B_s)*get_inverse(B_r+B_s,n))%n
    print("计算出的ALice的公钥为：")
    print(DA)
    print("计算出的Bob的公钥为：")
    print(DB)
```

# 实验结果
![Screenshot 2022-07-31 144520](https://user-images.githubusercontent.com/104854836/182013698-98b8fb3d-3c19-46d6-b2ff-4eadd0d9e44b.jpg)

