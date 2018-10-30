# Paired-t-test
対応ありt検定
- 対応するデータ間の差について「差の母平均は0である」という帰無仮説を検定する


### 使い方
##### データの準備
- `testData.csv`に比較したい標本を`,`で区切りながら貼り付ける  
- 各行の先頭に群の名前を書く
- 群間で対応しているデータが同じ列に並ぶように貼る
- 二群以上のデータを用意しても可(その場合は全ての組み合わせに対して検定を行う)
```
GroupA,1,1,2,3,1,3,2,4,1,2
GroupB,6,5,1,3,5,1,2,3,4,4
GroupC,2,1,1,1,2,3,2,2,2,3
GroupD,3,4,5,2,3,3,5,2,3,5
```

##### 実行
- 有意水準0.05で実行
```
python paired-t-test.py
```
- 有意水準を設定したい場合
```
python paired-t-test.py --level 0.01
```

- 別にデータを用意している場合
```
python paired-t-test.py --input "csvファイルへのパス"
```

##### 結果
p値(p-value)が出力される  
有意差が観測されたペアには`*`がつく
```
$ python paired-t-test.py

       GroupA            GroupB           GroupC             GroupD
GroupA      -  0.11076492157    0.797624520972   *0.0298581821752
GroupB      -              -  *0.0340763616342      0.89287385758
GroupC      -              -                 -  *0.00456754978545
GroupD      -              -                 -                  -
```