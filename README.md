# DecisionTreeClassifier
## 在不使用library的情形下自己定義分類樹
### _feature_split
#### 目的:
從現有數據的特徵中，選擇一個特徵作為當前節點的劃分標準，期望在不停劃分的過程中，決策樹的分支節點所包含的樣本盡量屬於同一類，該節點的純度會越高！

透過Information Gain去判斷該劃分是否為一個恰當的劃分。計算出各個特徵的threshold後，就能以threshold為判斷基準進而得到information gain!

當得到最小的criterion時，以該feature為主去做分割！

### _build_tree
#### 目的:
從root node開始以information gain最大的特徵去做節點的劃分特徵，由該feature的threshold去建立child node。

以top-down的方式來建構tree，直到沒有特徵可以選擇為止！

### _find_min_alpha
#### 目的
計算alpha的目的是為了判斷該剪枝是否為一個好的剪枝，當alpha越小的時候，代表該cut越好!

也就是說，做完cut的決策樹在判斷類別時候會更加準確！

以bottom up的方式去計算每個node的alpha，直到找到最小的alpha。

### _pruned
#### 目的
以每個node的alpha值去判斷是否適合做減枝，找到擁有最小alpha值的node就將它設定為cut node！

以bottom up的方式去尋找該tree的哪一個點的node其alpha值最小，擁有最小值alpha的node即設定為cut node。

## Result
### Decision tree before post-pruning accuracy:
tree train accuracy: 0.718776

tree test accuracy: 0.655106 

### Decision tree after post-pruning accuracy:
tree train accuracy: 0.718776

tree test accuracy: 0.658960

## The effect of different max_depth
![image](https://user-images.githubusercontent.com/62006029/197932621-549040db-3b53-4d83-8a98-1efcccf4588b.png)

可以觀察到當增加深度有可能會產生overfitting（訓練準確度提高但測試準確度降低），也就是説generalization ability會下降！

## Summary
剪枝的目的是為了避免決策樹發生overfitting的情況，當max_depth = 8的時候，做剪枝前後的準確度只有些為提升。
但當max_depth ＝10的時候，產生overfitting的機率變高了（深度越深，越容易發生overfitting）。
當max_depth越深的時候，做完剪枝準確度提高的程度會比max_depth值較小的時候還要大！




