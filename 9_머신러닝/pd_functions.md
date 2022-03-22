datetime

https://rfriend.tistory.com/497

timestamp가 지수표현으로 되어서 제대로 나오지 않는다.

pandas e(지수표현)안나오게 하기 https://zel0rd.tistory.com/33

```python
pd.to_datetime(df['timestamp_column'], unit='s')
```

이렇게 하니까 해결됐다. [결론부터 말해...](https://bkool.tistory.com/)



str.extract()

str.contains()