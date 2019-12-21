# Python基礎講習　変数とデータ型

## 1.式と演算

基本的な演算はjavaと同じ

数字と文字を合わせる場合は変換が必要
```python
print(1+1)
→2

print('1'+'1')
→11

print('大橋'+'かな'*3)
→大橋かなかなかな

age=20
print(大橋かなさんの年齢は + str(age))
→大橋かなさんの年齢は20
```

## 2.変数
pythonでは型指定がいらない

まとめて定義することもできる

例

[Java]

```java
String name = "大橋かな"
List<データ型名> オブジェクト名 = new ArrayList<データ型名>();
```

[python]

```python
name = "大橋かな"
List = []

name,age = '大橋',20
```

入力も簡単

```python
変数名 = input(文字列)
age = input('大橋かなさんの年齢を入力してください')
```

## 3.データ型

代入するデータによって型が決まる

```python
age=20
print(type(age))
→class int
```

データ型の変換も簡単である

int(x),float(x),str(x)など

数字と文字を合わせる場合は変換が必要

format関数というものもあるので興味があれば調べてください（使うことはない多分）

```python
age=20
print(type(age))
→class int

print(type(str(age)))
→class str

print(大橋かなさんの年齢は + str(age))
→大橋かなさんの年齢は20
```

## 課題

キーボードから身長(cm)と体重(kg)の入力を受け、そこからBMIを計算するプログラムを作りなさい。

BMI=体重(kg)÷身長(m)÷身長(m)
