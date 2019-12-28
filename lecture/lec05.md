# Python基礎講習　Numpy Pandas
## ☺インストール
Pycharmのファイル→設定→プロジェクト・インタープリター→右上の+ボタンを押してnumpyとpandasを検索してパッケージのインストールをする。
わからなければslackで聞いてください。
## 📐NumPy
　NumPyはPythonで科学計算を行うためのライブラリで多次元配列を扱うため機能を提供します。
### 🤔標準リストの苦悩
　なぜPython標準のリストだけでなく外部ライブラリの力を借りなければならないのか、それを説明するために配列の計算を例に挙げて説明します。
　以下は偶数と奇数の配列を加算しようとしているプログラムです。
###### 入力 : 
```python
odds = [1, 3, 5]
evens = [2, 4, 6]
odds + evens
```
###### 出力 : 
```shell
[1, 3, 5, 2, 4, 6]
```
　エラーは発生せずプログラム自体は動作しています。しかし期待していたものとはかけ離れていることが分かるでしょうか。私たちは配列の計算をしているはずなのに、結果はリストが結合されただけです。では実際にPython標準のリストで配列の計算を行うにはどのようにすればよいのでしょうか。
　以下は偶数と奇数の配列を加算するプログラムです。
###### 入力 : 
```python
odds = [1, 3, 5]
evens = [2, 4, 6]
result = []
for i in range(0, 3):
	result.append(odds[i]+evens[i])
result
```
###### 出力 : 
```shell
[3, 7, 11]
```
　期待通りの結果が出ました。めでたし。	...とは問屋が卸しません。たかが加算でこんなに長いコードを書かなければならないのです。乗算は二重for文になります。たかが加算・乗算の度にこんなコードを書いていたらいくら時間があっても足りません。
### 😮NumPyでは
　NumPyを利用すると最初のプログラムで配列の加算ができます。以下は偶数と奇数の配列を加算するプログラムです。
###### 入力 : 
```python
import numpy as np
adds = np.array([1, 3, 5])
evens = np.array([2, 4, 6])
adds + evens
```
###### 出力 : 
```shell
array([3, 7, 11])
```
　乗算についても同様に行えます。以下は偶数と奇数の配列を乗算するプログラムです。
###### 入力 : 
```python
import numpy as np
adds = np.array([1, 3, 5])
evens = np.array([2, 4, 6])
adds * evens
```
###### 出力 : 
```shell
array([ 2, 12, 30])
```
　詰まるところ、NumPyの何が良いのかというと直感的で可読性の高いコードになっているという点です。計算は重要な過程ではありますが本質ではありません。プログラムの殆どが加乗算のfor文で敷き詰められているコードなんて誰も見たくはありません。他にも様々なフレームワークで引数として用いられたり、for文よりもパフォーマンスが早いなどのメリットがあります。
### 🎯NumPyの基礎
　今回はNumPyの基本要素である`ndarray`の生成から操作までの一部を紹介します。ndarrayは高速で柔軟な大規模データ処理を提供します。
#### 生成編
##### `array()`
　一番簡単にndarrayオブジェクトを生成するにはNumPyの`array`関数を使用します。
　以下はarray関数を使用してndarrayオブジェクトを生成する例です。
###### 入力 : 
```python
import numpy as np
data = [[1, 2, 3, 4], [5, 6, 7, 8]]
array = np.array(data)
array
```
###### 出力 : 
```shell
array([[1, 2, 3, 4],
       [5, 6, 7, 8]])
```
##### `arange()`　
　`arange`関数は0から指定した値の数の大きさを持つ配列を作成します。
###### 入力 : 
```python
import numpy as np
array = np.arange(10)
array
```
###### 出力 : 
```shell
array([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
```
##### `zeros()`
　`zeros`関数を使うと要素がすべて0の配列を生成します。
###### 入力 : 
```python
import numpy as np
array = np.zeros(5)
array
```
###### 出力 : 
```shell
array([0., 0., 0., 0., 0.])
```
##### 型の指定
　ndarrayオブジェクトは`dtype`引数でデータ型を指定できます。
###### 入力 : 
```python
int_array = np.array([1, 2, 3], dtype=np.int32)
float_array = np.arange(5, dtype=np.float64)
bool_array = np.zeros(7, dtype=np.bool)
int_array
float_array
bool_array
```
###### 出力 : 
```shell
array([1, 2, 3])
array([0., 1., 2., 3., 4.])
array([False, False, False, False, False, False, False])
```
#### 操作編
　NumPyの操作にはソートや記述統計量の算出など様々ですが、今回はインデックス参照を紹介します。
　インデックス参照とはC言語でいう配列`a`に対する`a[N]`です。Pythonにはこれにバラエティがあります。
#####  N :  
　`N:` で配列の指定開始地点を指定します。以下はその例です。
###### 入力 : 
```python
import numpy as np
array = np.array([2, 4, 6, 8, 10, 12, 14])
array[2:]
```
###### 出力 : 
```shell
array([ 4,  6,  8, 10, 12, 14])
```
##### : N
`: N`で配列の指定終了地点を指定します。以下はその例です。
###### 入力 : 
```python
import numpy as np
array = np.array([2, 4, 6, 8, 10, 12, 14])
array[:3]
```
###### 出力 : 
```shell
array([2, 4, 6])
```
##### :
`:` ですべての要素。上の2例から書き方は想定できると思うのでサンプルプログラムは省略します。
##### N : N
`N : N`で配列の指定開始地点と終了地点を指定します。省略。
## 🐼Pandas
　Pandasは構造化されたデータやテーブル形式のデータをわかりやすく扱うための機能を提供します。Pandasを始めるにはSeriesとDataFrameというデータ構造に慣れる必要があります。
### 1️⃣Series
　Seriesは1次元の配列のようなオブジェクトです。ただ配列とは違い、インデックス番号やそれ相応のデータラベルの配列も持ちます。
　以下のプログラムは得点と自動で割り振られるインデックス番号を表示するプログラムです。
###### 入力 : 
```python
import pandas as pd
points = pd.Series([60, 75, 47, 100, 94])
points
```
###### 出力 : 
```shell
0     60
1     75
2     47
3    100
4     94
dtype: int64
```
　以下のプログラムは得点とインデックスを表示するプログラムです。
###### 入力 : 
```python
from pandas import Series
points = Series([60, 75, 47, 100, 94], index=['Alice', 'Bob', 'Carol', 'Dave', 'Frank'])
points
```
###### 出力 : 
```shell
Alice     60
Bob       75
Carol     47
Dave     100
Frank     94
dtype: int64
```
　Pythonのディクショナリ型でシリーズを作ることもできます。以下はディクショナリ型で得点とインデックスのSeriesを作成し表示するプログラムです。
###### 入力 : 
```python
import pandas as pd
data = {'Alice': 60, 'Bob': 75, 'Carol': 47, "Dave": 100, 'Frank': 94}
points = pd.Series(data)
points
```
###### 出力 : 
```shell
Alice     60
Bob       75
Carol     47
Dave     100
Frank     94
dtype: int64
```
　Seriesは入れ替えを容易に行えます。以下はディクショナリ型で表示した後にインデックスの一部の内容を変えたプログラムです。
###### 入力 : 
```python
import pandas as pd
data = {'Alice': 60, 'Bob': 75, 'Carol': 47, "Dave": 100, 'Frank': 94}
points = pd.Series(data)
points
status = {'Carol', 'Bob', 'Dave', 'Frank', 'Ellen'}
points = pd.Series(data, index=status)
points
```
###### 出力 :  [^1]
```python
Alice     60
Bob       75
Carol     47
Dave     100
Frank     94
dtype: int64
Frank     94.0
Ellen      NaN
Dave     100.0
Bob       75.0
Carol     47.0
dtype: float64
```
　順番はバラバラになっていますが、得点とインデックスの紐づけは間違っていないことが分かります。この例では`data`に含まれていない`Ellen`というインデックスを加えました。そこはNaN(Not a Number)と呼ばれ日本語で非数や欠損値の扱いとなります。欠損値はpandasのisnull関数またはnotnull関数を使うと特定できます。
　以下はisnull関数で欠損値を特定するプログラムです。
###### 入力 : 
```python
import pandas as pd
data = {'Alice': 60, 'Bob': 75, 'Carol': 47, "Dave": 100, 'Frank': 94}
status = {'Carol', 'Bob', 'Dave', 'Frank', 'Ellen'}
points = pd.Series(data, index=status)
pd.isnull(points)
```
###### 出力 :  [^1]
```shell
Ellen     True
Carol    False
Dave     False
Bob      False
Frank    False
dtype: bool
```
[^1]: インデックスの表示の順番は0.20.x以降でバラバラになるみたいです。私の環境でPandasのバージョンを変えて(もちろんPythonのバージョンも変えて)実行してみましたが結果は変わりませんでした。0.18.xだと降順またはインデックス順になるようです。もしかしたら何らかのオプションが追加されたのかも？
### 📅DataFrame
　DataFrameはテーブル形式のデータ構造を持ち、行と列の両方にインデックスを持ちます。
　以下は身長・体重・性別のデータフレームを表示するプログラムです。
###### 入力 : 
```python
data = {'height': [165.5, 174.5, 156.3, 161.4],
'weight': [66.4, 72.4, 54.9, 52.2],
'sex': ['female', 'male', 'female', 'male']}
frame = pd.DataFrame(data)
frame
```
###### 出力 : ###### 出力 : 
```shell
   height  weight     sex
0   165.5    66.4  female
1   174.5    72.4    male
2   156.3    54.9  female
3   161.4    52.2    male
```
　勿論、行のインデックスはデータラベルの配列でも大丈夫です。以下はその例です。
###### 入力 : 
```shell
data = {'height': [165.5, 174.5, 156.3, 161.4],
'weight': [66.4, 72.4, 54.9, 52.2],
'sex': ['female', 'male', 'female', 'male']}
frame = pd.DataFrame(data, index=['Alice', 'Bob', 'Carol', 'Ellen'])
frame
```
###### 出力 : 
```shell
       height  weight     sex
Alice   165.5    66.4  female
Bob     174.5    72.4    male
Carol   156.3    54.9  female
Ellen   161.4    52.2    male
```
### 📝ファイルの読み込み
　Pandasは外部ファイルを読み込む機能を提供します。今回はcsvファイルを読み込む方法を紹介します。
　先ずは読み込むためのファイルを作成します。以下の内容のファイルを作成してください。
##### `only_points.csv`
```csv
6, 10, 8
8, 7, 10
5, 10, 5
```
　Pandasにはcsvファイルを読み込むために`read_csv()`があります。戻り値はDataFrameです。以下はonly_points.csvをread_csv関数で読み込む例です。
###### 入力 : 
```python
import pandas as pd
points = pd.read_csv('only_points.csv', header=None)
points
```
###### 出力 : 
```shell
   0   1   2
0  6  10   8
1  8   7  10
2  5  10   5
```
　headerの行数目を指定することも出来ます。
##### `points_with_header.csv`
```csv
C, Java, Python
6, 10, 8
8, 7, 10
5, 10, 5
```
###### 入力 : 
```python
import pandas as pd
points = pd.read_csv('points_with_header.csv', header=0)
points
```
###### 出力 : 
```shell
   C   Java   Python
0  6     10        8
1  8      7       10
2  5     10        5
```
　indexの列数目を指定することも出来ます。
##### `points_with_header_and_index.csv`
```csv
, C, Java, Python
Alice, 6, 10, 8
Bob, 8, 7, 10
Carol, 5, 10, 5
```
###### 入力 : 
```python
import pandas as pd
points = pd.read_csv('points_with_header_and_index.csv', header=0)
points
```
###### 出力 : 
```shell
        C   Java   Python
Alice   6     10        8
Bob     8      7       10
Carol   5     10        5
```
## 🎁演習問題
　NumPyとPandasを組み合わせた問題です。自分で調べることも必要な問題になります。
　`points_with_header_and_index.csv`を読み込んで、インデックスに合計・平均・標準偏差を追加してください。必要な計算はNumPyで行ってください。
下のように出力されるようにやってみよう。
###### 出力 : 
```shell
        C   Java   Python  sum  ave  dev
Alice   6     10        8    **  **   **
Bob     8      7       10    **  **   **
Carol   5     10        5    **  **   **
```
## 📖参考文献
- [NumPy Documentation](https://numpy.org/devdocs/user/whatisnumpy.html)
- [Pandas Documentation](https://pandas.pydata.org/pandas-docs/stable/)
- [Pythonによるデータ分析入門](https://www.oreilly.co.jp/books/9784873118451/)
- [pandasでcsv/tsvファイル読み込み](https://note.nkmk.me/python-pandas-read-csv-tsv/)