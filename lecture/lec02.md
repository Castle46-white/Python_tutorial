# Python基礎講習　コレクション
リスト, タプル, 辞書, 集合

## リスト
複数の要素を `,`(カンマ)で区切り、` [ ] `で囲んだもの  
Javaの配列とリストを複合したような扱いができる  
インデックスを持っており、インデックスを指定することで要素にアクセスできる  
複数の型が混在していても格納できる  
マイナスのインデックスを指定できる（この場合末尾から何番目という意味になる）
```python
names = [100,'ikawa','','shiro']
print(names)
print(names[1])
print(names[-1])
```
出力
```
[100,'ikawa','','shiro']
ikawa
shiro
```
### 要素の追加、変更
```python
#変更
names[2] = 2.5
#追加
names.append('aaa')

print(names)
```
出力
```
[100,'ikawa',2.5,'shiro','aaa']
```


## タプル
リストと似ているが、一度定義すると変更できない  
` ( ) ` を用いて定義する
```python
tuple = (1, 2, 3)

#これはエラーになる
tuple[1] = 5
```

## 辞書
` key ` と ` value ` をセットにして格納する
` key ` は日本語でも問題ない
```python
scores = {'English': 100, 'Math': 85, '理科': 60 }
print(score[English])

#kyeのリストを取得
print(score.keys())

#valueのリストを取得
print(score.values())

#(key, value)というタプルのリスト
print(score.items())
```

```
100
dict_keys(['English', 'Math', '理科'])
dict_values([100, 85, 60])
scores.items()
```


## 集合
重複なしのリストのようなもの
```python
x = set( [1 , 2 , 5] )	# セットの宣言
y = { 2 , 4 }			# { }でも宣言可
x.add( 24 )			    # セットに追加
z = x  |  y 			# 和集合　z = { 1 , 2 , 4 , 5 }
z = x & y			    # 積集合　z = { 2 }
```


## 課題
1. 1〜10までをリストに格納し、それぞれの値を2乗した値を出力せよ
2. 下記のdictionaryオブジェクトを使用してそれぞれのkeyとvalueを取得し、valueが20以上の場合「(keyの中身):hot」と出力し、超えていない場合は「(keyの中身):cold」と出力せよ
```python
temperatures  = { 'x': 24 , 'y': 18, 'z': 30}
出力結果:
x:hot
y:cold
z:hot
```
3. 1~10の範囲で整数をランダムに重複なしで5個生成し、生成された数値を表示せよ
 