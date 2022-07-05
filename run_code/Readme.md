## Train
- DataSet : AI Hub 문서요약 텍스트 - 뉴스데이터(10%)
// 학습 용량 문제로 10% 밖에 활용하지 못함.

- DataSet preprocessing : Dacon 경진대회의 이야기연구소 주식회사에서 공유한 코드 사용
>https://dacon.io/codeshare/4047?dtype=recent
>> 아래와 같이 내가 사용하는 모델에 맞게 또는 검증 부분에서 확인된 오류 부분을 수정
>>> 기존 코드
>>> reporter_pattern = re.compile(r"^\/?([가-힣]+)\s?(기자|팀)?\s*\.?$")
>>> 수정 코드
>>> reporter_pattern = re.compile(r"^\/?([가-힣]+)\s?(기자|팀)+\s*\.?$")
>>> 등
    
## Model
- AI Hub 문서요약 텍스트에서 제공한 AI모델 중 bertsumabs를 사용
> 모델 소개 영상에서 .bat 파일의 실행영상밖에 공유가 되지 않았기 때문에 preprocess, train, test에 적합한 데이터를 가공하여 적용시키기 위해 오픈소스 모델을 리뷰하며 진행했습니다.

- 전체 데이터의 10%에서 80%를 Train으로, 10%, 10%를 각각 Validate, Test Set로 진행함.
> 용량, 시간, 비용 문제

## Test
- gold(target data)와 candidate(predict data)를 자체 검증
> 잘 요약된 문장도 있지만, 내용을 잘못 혼합한 문장, target에 비해 길이가 훨씬 긴 문장 등 보완이 필요해 보임.
- 더 좋은 결과를 얻기 위해선?
> 전체의 10%의 데이터가 아닌 더 많은 데이터를 학습에 이용
>> train 과정에서 더 좋은 성능을 낼 parameter를 적용하여 학습
>>> bertsumext 또한 진행하여 bertsumabs의 encoder에 ext를 finetuning하는 bertsumextabs를 수행
>>>> 예측 문장의 최소길이를 보완(현재 50)

## Project
- 모델의 코드를 다방면으로 수정 
- 들어오는 데이터는 각 문장이 나누어져 있지 않기 때문에 kss 패키지를 통해 문장을 분리
- news(input data) -> split sentences -> bertdata -> bertsumabs / 추가적으로 news data를 전처리하는 과정도 필요할 것임.
- dash를 이용한 웹 구현
> [https://github.com/raqoon886/KorBertSum ](https://github.com/raqoon886/KorBertSum/blob/master/Newsdata_summarybot.ipynb)의 코드를 수정하여 사용하였음.
- 현재, Django 웹프레임워크를 이용하여 구현하려고 하는데 문제 발생
> 본인의 Windows에서의 Python 버전으로는 구현하는데 있어, 각 package들 버전이 호환 불가한 문제 발생
>> 이를 해결하기 위해 CI에 대한 학습을 진행 중에 있음.
