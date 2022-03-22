```
########### Pandas 데이터 분석 ###########

Movie Lens Data Set을 이용해서 다음의 내용을 구하세요

### 1. 사용자가 평가한 모든 영화의 전체 평균 평점을 출력하세요.
3.501556983616962

### 2. 각 사용자별 평균 평점을 구하세요. 
###    출력시 정렬은 userId로 오름차순 정렬합니다.
userId
1      4.366379
2      3.948276
3      2.435897
4      3.555556
5      3.636364
         ...   
606    3.657399
607    3.786096
608    3.134176
609    3.270270
610    3.688556
Name: rating, Length: 610, dtype: float64

## 3. 각 영화별 평균 평점을 구하세요. 
##    출력시 정렬은 movieId로 오름차순 정렬합니다. 
=> 	movieId	title	rating
      0	1	Toy Story (1995)	3.920930
      1	2	Jumanji (1995)	3.431818
      2	3	Grumpier Old Men (1995)	3.259615
      3	4	Waiting to Exhale (1995)	2.357143
      4	5	Father of the Bride Part II (1995)	3.071429
      ...	...	...	...
      9737	193581	Black Butler: Book of the Atlantic (2017)	4.000000
      9738	193583	No Game No Life: Zero (2017)	3.500000
      9739	193585	Flint (2017)	3.500000
      9740	193587	Bungo Stray Dogs: Dead Apple (2018)	3.500000
      9741	193609	Andrew Dice Clay: Dice Rules (1991)	4.000000
      
      9724 rows × 3 columns

## 4. 평균 평점이 가장 높은 영화의 제목을 출력하세요.
##    단, 동률이 있을 경우 모두 출력하고 
##    title을 기준으로 오름차순 정렬하세요.

=> 	movieId	title	rating
      5690	27751	'Salem's Lot (2004)	5.0
      7332	77846	12 Angry Men (1997)	5.0
      9046	141816	12 Chairs (1976)	5.0
      3893	5468	20 Million Miles to Earth (1957)	5.0
      5639	27373	61* (2001)	5.0
      ...	...	...	...
      9711	187717	Won't You Be My Neighbor? (2018)	5.0
      8355	108795	Wonder Woman (2009)	5.0
      9289	158398	World of Glory (1991)	5.0
      9560	173351	Wow! A Talking Fish! (1983)	5.0
      7521	84273	Zeitgeist: Moving Forward (2011)	5.0
      296 rows × 3 columns

## 5. Comedy영화 중 가장 평점이 낮은 영화의 제목을 출력하세요.
##    단, 동률이 있을 경우 모두 출력하고 
##    title을 기준으로 오름차순 정렬하세요.

=> 	movieId	title	genres
      8893	134528	Aloha (2015)	Comedy|Drama|Romance
      5777	31422	Are We There Yet? (2005)	Children|Comedy
      7762	91414	Arthur Christmas (2011)	Animation|Children|Comedy|Drama
      9419	165645	Bad Santa 2 (2016)	Comedy
      4439	6557	Born to Be Wild (1995)	Adventure|Children|Comedy|Drama
      5409	25782	Boudu Saved From Drowning (Boudu sauvé des eau...	Comedy
      6554	54934	Brothers Solomon, The (2007)	Comedy
      5453	26095	Carabineers, The (Carabiniers, Les) (1963)	Comedy|Drama|War
      6545	54768	Daddy Day Camp (2007)	Children|Comedy
      4881	7312	Follow Me, Boys! (1966)	Comedy|Drama
      7553	85334	Hard Ticket to Hawaii (1987)	Action|Comedy
      8417	110773	Haunted House 2, A (2014)	Comedy|Horror
      5662	27595	Jesus Christ Vampire Hunter (2001)	Action|Comedy|Horror|Musical
      8984	138798	Joe Dirt 2: Beautiful Loser (2015)	Comedy
      7820	92681	Journey 2: The Mysterious Island (2012)	Action|Adventure|Comedy|Sci-Fi|IMAX
      6160	44243	Leprechaun 4: In Space (1997)	Comedy|Fantasy|Horror|Sci-Fi
      8248	104644	Maria Bamford: The Special Special Special! (2...	Comedy
      7201	72696	Old Dogs (2009)	Comedy
      9056	141994	Saving Christmas (2014)	Children|Comedy
      5258	8632	Secret Society (2002)	Comedy
      9590	175475	The Emoji Movie (2017)	Animation|Children|Comedy
      8908	135216	The Star Wars Holiday Special (1978)	Adventure|Children|Comedy|Sci-Fi
      8676	122246	Tooth Fairy 2 (2012)	Children|Comedy
      5795	31692	Uncle Nino (2003)	Comedy
      6784	60363	Zombie Strippers! (2008)	Comedy|Horror

## 6. 2015년도에 평가된 모든 Romance 영화의 평균 평점은?
3.396375098502758

## 7. 모든 영화장르 중 사용자 평점이 가장 좋은 
##    영화장르는 무엇인가요?
##    동률이 있으면 영화장르를 기준으로 오름차순 정렬하세요.
????
```

```
########### Pandas 데이터 분석 ###########

기상자료개방포털 홈페이지에서 기상관련 데이터를 제공받아 
데이터 분석

기후통계분석 > 통계분석 > 기온분석 메뉴에서 
기간을 설정하고(1904년1월1일~최근) 지역은 서울을 설정합니다. 
(아래의 문제를 풀기 위해서 대구 지역의 파일도 받아야 합니다.)

CSV 다운로드 버튼을 클릭해 데이터 파일을 다운로드 받습니다.

### 1. 기상 관측 이래, 서울의 최고 기온이 가장 높았던 날은 언제였고, 
         몇도인가요?

### 2. 역사적으로 일교차가 가장 큰 날짜는 몇년 몇월 몇일 인가요?

### 3. 1년 중 평균적으로 일교차가 가장 큰 날짜는 몇월 몇일 인가요?
       몇년 몇월 몇일

### 4. 가장 덥다고 알려진 대구보다 서울이 더 더운날이 가장 많은 연도는 
         언제인가요?
         몇월 몇일
```