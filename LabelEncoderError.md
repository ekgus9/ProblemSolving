# Label Encoder 사용 중 에러



LGBM 알고리즘을 짜던 도중 아래 코드 부분에서 에러가 발생하였다.

```
result = pd.DataFrame(prediction, columns = lb.inverse_transform(np.linspace(0, 38, 39, dtype='int16')),index=test.index)
```

> NotFittedError: This LabelEncoder instance is not fitted yet. Call 'fit' with appropriate arguments before using this estimator.



> ValueError: y contains previously unseen labels:



columns 부분을 제거하면 에러가 발생하지 않았기 때문에 LB.inverse_transform(np.linspace(0, 38, 39, dtype='int16')) 부분에서 발생한 걸로 보이는 데 어디가 문제인지 알 수 없었다. 
한참을 고민하다 label encoder을 columns에서 필요한 타겟 데이터 부분만이 아닌 다른 데이터에서 무분별하게 사용했음을 알게 되었다.



따라서 타겟 데이터를 label encoding 하는 부분의 label encoder을 다른 변수로 명명하여 에러를 해결하였다.

```
LB = LabelEncoder()
```

```
result = pd.DataFrame(prediction, columns = LB.inverse_transform(np.linspace(0, 38, 39, dtype='int16')),index=test.index)
```
