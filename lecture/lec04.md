# Python基礎講習　関数

## 1.関数の定義

pythonでは｛｝ではなくインデント(空白)を用いる

```python
def 関数名():
    処理
```

## 2.引数、戻り値

戻り値を書かなくていいこと以外はjavaと変更点は特にない

pythonも戻り値は一つしか返せないので注意

```python
def 関数名(引数 1,引数 2, ・・・):
    処理
    return 戻り値
```

## 3.関数の応用

こんな使い方も

```python
def plus_and_minus(a,b):
    return a+b,a-b

plus,minus = plus_and_minus(2,1)
```

可変長引数といいタプルやディクショナリを渡すことができる

```python
def ohashi(*name):
    for n in name:
        print(n)
ohashi('大','橋','か','な')
→大橋かな
```

## 4.グローバル変数

pythonはグローバル関数が関数内でも使えるが代入はグローバル文を使う
```python
name='大橋かな'
def hello():
    print(name)
hello()
→大橋かな

def change_name():
    global name
    name='小橋'
hello()
→小橋
```  

## 課題

人数とお金を入力する関数、お金を人数で割り勘する関数、割り勘した値段を表示する関数を用いて割り勘システムを作りなさい。

