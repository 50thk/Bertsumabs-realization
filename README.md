# KoBertsumabs
**This code is for EMNLP 2019 paper [Text Summarization with Pretrained Encoders](https://arxiv.org/abs/1908.08345)**
- Using SKT KoBert
- [Ai hub 문서요약 텍스트 공개모델](https://aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&aihubDataSe=realm&dataSetSn=97) 활용
- Kobetsum의 생성요약을 구현하여 소스코드 및 프로젝트를 오픈한 사례가 없어 참고하기에 어려움이 있었음.
- 처음으로 오픈소스를 수정하며 프로젝트를 진행하였고, 배운 점이 많았음.
  - bertsum의 오픈소스는 영어에 초점을 두었고, 한국어에 맞추기 위해서는 한국어로 pretrain된 모델을 선정하여 모델과 tokenizer에 맞춰 오픈소스를 수정하면 모든 기능을 한국어 버전으로 구현할 수 있다는 것을 깨달았고, 프로젝트를 진행하며 해당 부분은 스스로 수정하여 배포할 수 있을 거라는 자신이 생김.
  - Dacon 대회에서 우수한 성적을 거둔 이야기연구소 주식회사의 raw data 전처리를 진행하는 코드를 가져와 사용하고, 이를 검증해보았는데 문제점을 발견할 수 있었음. 이것을 통해 무작정 가져다 쓰는 것이 아닌 코드를 훑어보고, 이를 검증하는 것에 대한 중요성을 깨달았음
  - padding의 길이값을 정해놓는 것이 아닌 이야기연구소 주식회사의 방식처럼 문장에 맞춰 padding의 길이를 맞추는 방식을 사용했으면 학습시간의 단축에 도움이 되었을 것임.
  - 전체의 데이터 셋을 사용할 수 있었으면 더 좋은 결과가 나왔을 것 같아 아쉬움이 남음.
