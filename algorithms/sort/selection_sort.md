# Selection Sort
> 가장 작은값이 앞으로

```
def selection_sort(list):
	length = len(list) # list의 길이를 변수에 지정
	for x in range(length-1) # 가장 큰 값이 맨뒤로 정렬이 되기 때문에 가장 끝까지 순회할 필요는 없음
		min_index = x # min_index의 초기값은 x
		for y in range(1, length): # y는 min_index와의 비교를 위한 값
			if list[min_index] > list[y]: # min_index의 값이 y의 값보다 크면
				min_index = y # y의 인덱스 값을 min_index값으로 지정
		if list[x] > list[min_index] # min_index값보다 x의 값이 더 크면
			list[x], list[min_index] = list[min_index], list[x] # x의 값과 min_index에 해당하는 값의 자리를 바꿔줌
		return list # 최종적으로 정렬된 list를 리턴
```