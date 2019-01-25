# Yapen Django Ver.(4)

##### 2019/1/24 목요일

크롤러 구조

```
for location in Location.objects.all():
	for sub_location in location.sub_location.all():
		crawler(location.location_number, sub_location.sub_location_number
```