### 01. datetime 

https://rfriend.tistory.com/497

timestamp가 지수표현으로 되어서 제대로 나오지 않는다.

★ pandas e(지수표현)안나오게 하기 https://zel0rd.tistory.com/33

```python
pd.to_datetime(df['timestamp_column'], unit='s')
```

이렇게 하니까 해결됐다. [결론부터 말해...](https://bkool.tistory.com/) : 's' 는 seconds의 s라고 한다.



~~(C#) datetime 특정월 마지막 날짜 구하기 https://icodebroker.tistory.com/1443?category=641589~~

~~(C#) datetime 마지막주 일요일 구하기 https://icodebroker.tistory.com/1444~~



### 02. 정규식

점프투파이썬 정규식 https://wikidocs.net/4308#_7

https://hyunhp.tistory.com/24

**괄호와 괄호 안 내용 삭제**

```python
regex = "\(.*\)|\s-\s.*"
text = '오늘은 딸기(서향딸기, 600g, 1팩당 5,000원)가 좋습니다!'
print(re.sub(regex, '', text)) # 오늘은 딸기가 좋습니다!
for i in range(len(df)):
    df['브랜드'][i] = re.sub(regex, '', df['브랜드'][i])
    print(df['브랜드'][i])
```

- 정규 표현식을 사용한 괄호 및 괄호 안 텍스트 설정
  - regex = "\(.*\)|\s-\s.*"
- re.sub() 파라미터 설정
  - re.sub(`수정/변경할 문자열`, `최종적으로 구성될 형태`, `적용될 텍스트`)



**괄호 내용 추출**

```python
regex = r'\(([^)]+)'

# re.findall(텍스트 구성, 찾을 텍스트)
# findall() 함수는 list형식으로 저장되어, 이후에 0번째 리스트만 추출하면 된다.
re.findall(regex, text)[0]
```

정규 표현식을 사용한 괄호 및 괄호 안 텍스트 설정

- regex = r'\\((\[^)]+)'



**단어를 포함하는 행 삭제**

https://hyang2data.tistory.com/13

```python
dfresult = df[~df['Time'].str.contains("2021-03-01", na=False, case=False)]
```



### 00. 기타



**dataframe for 문**

https://ponyozzang.tistory.com/609

```python
for index, row in df.iterrows():
```



**reindex(~), reset_index()**

https://rfriend.tistory.com/255



**dataframe 모든 행, 열나오게**

```python
pd.set_option('display.max_columns', None)
pd.set_option('display.max_rows', None)
```

https://zephyrus1111.tistory.com/44









str.extract()

str.contains()



dataframe for 문 https://ponyozzang.tistory.com/609

df.iteritems()

df.iterrows()