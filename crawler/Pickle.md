# Pickle
> 파이썬 객체를 저장

Why?

```
내가 크롤링한 자료들을 저장할 때, 파이썬 객체 자체로 저장가능하게 함

list = ['a', 'b', 'c']
> 이 list는 일반적인 open(..)으론 저장이 불가능

```

```
import pickle

list = ['a','b','c']
with open('list.txt', 'wb') as f:
	pickle.dump(list, f)
```

