# tweet_sentiment_bert

## データセット 
データセットは[tweet_sentiment_extraction](https://www.kaggle.com/c/tweet-sentiment-extraction/overview)を用いた<br>
<img src="https://github.com/Jumpei-Fujita/tweet_sentiment_bert/blob/main/dataset.png" width="70%"><br>

## 前処理
訓練データのうち1000件を検証データに用いた。また、特殊文字の除去、@からスタートする文字列の除去などを行った。<br>
||訓練データ|検証データ|テストデータ|
|:--|:--|:--|:--|
|データ数|26486|1000|3535|


## モデル構築
<img src="https://github.com/Jumpei-Fujita/tweet_sentiment_bert/blob/main/model.png" width="50%"><br>
BERTをファインチューニングし、感情分析モデルを構築した。
アーキテクチャの概略は上の通りである。
最適化手法はAdamを選択し、ハイパーパラメータとしては以下がある。
|ハイパーパラメータ| |
|:--|:--|
|```lr```|学習率|
|```epochs```|学習エポック数|
|```batch_size```|バッチサイズ|


## 結果
### 1.学習の様子
訓練時のlossの推移<br>
<img src="https://github.com/Jumpei-Fujita/tweet_sentiment_bert/blob/main/graph.png" width="70%"><br>
訓練時の検証ようデータに対する正解率の推移<br>
<img src="https://github.com/Jumpei-Fujita/tweet_sentiment_bert/blob/main/acc.png" width="70%"><br>
訓練時のlossの推移は移動平均を取っている。
若干過学習が起こっているため、early stoppingなどを用いる必要が考えられる。
### 2.テストデータに対する結果
||neutral|positive|negative|
|:--|:--|:--|:--|
|recall|0.77|0.83|0.75|
|precision|0.71|0.61|0.59|
|f-value|0.74|0.70|0.66|

## コードの実行手順
tweet_sentiment.ipynbを上から順に実行していく


