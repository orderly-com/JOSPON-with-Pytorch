# JOSPON-with-Pytorch
Judge of sentence positive or negative with PyTorch
句子正負面情緒判斷類神經網路模型，使用PyTorch
> PyTorch練習小專案

[資料集來源(賣外評論資料)](https://github.com/SophonPlus/ChineseNlpCorpus)

# 模型定義
- 包含兩個隱藏層
- hidden、hidden2 使用 `relu`
- out 使用 `sigmoid`
```
(hidden): Linear(in_features=200, out_features=150, bias=True)
(hidden2): Linear(in_features=150, out_features=100, bias=True)
(out): Linear(in_features=100, out_features=1, bias=True)
```

# 方法
- 取得句子向量
    - 使用預訓練word2vec模型搭配jieba斷詞，將所有單詞向量相加平均
    - 使用檔案:`w2v_train.py`、`w2v_sentence_vector.py`

- 將資料集中句子全部轉換成向量
    - 使用檔案:`make_w2v_set.py`

- 訓練神經網路模型
    - 使用檔案:`jwp_train_bce.py`

# 結果
## 訓練結果
```
epoch: 50 loss: 0.592 train_acc: 0.798 test_acc: 0.754 LR: 0.004
```
## 測試結果
```
輸入評價:東西好吃
1.0
正面

輸入評價:東西難吃
0.0
反面

輸入評價:速度很快，還不錯吃
1.0
正面

輸入評價:動作慢，不太好吃
0.389
反面
```