# sLM Finetuning (Llama 3.2 1B or 3B)
> written by Sangjae Lee


## Llama 3.2 1B Model을 파인튜닝 하는 방법
- Sagemaker JumpStart (Web Console)
- Sagemaker JumpStart + Sagemaker SDK (JumpStartEstimator)
- Huggingface + Sagemaker (Huggingface Estimator)
- Huggingface Training Library (TRL)
- Pure Pytorch
- 각종 Recipe. ex) Llama recipe


## 데이터셋 준비
- Llama 및 오픈소스 모델을 파인튜닝하는데 가장 높은 장벽은 의외로 데이터셋 마련 부분이다.
- 양질의 데이터셋을 준비하기도 어렵거니와 각 모델을 학습할 때 필요한 데이터 포맷도 제각각이다.
- 심지어는 동일한 오픈소스 모델을 학습 할 때 조차 모델의 버전, 파인튜닝하는 수단과 라이브러리 및 플랫폼에 따라서도 달라진다.
- 이러한 부분을 잘 인지하고 정확한 가이드가 없다면 많은 시행착오를 거치곤 한다. ^^;;;


## JumpStart Web Console
- Sagemaker Studio AI > JupyterLab > JumpStart 에서 Meta > llama 3.2 1B Instruct Model 선택
- Dataset이 포함된 Bucket 지정하고, 기본 설정
- EULA 동의 하고, Submit

### Dataset 준비
여기에서 중요하는 것은 Dataset의 준비이다. 
Dataset의 형태는 jsonl 형식의 파일로 다음과 같은 포맷을 사용하면 된다. 
다른 여러 데이터 포맷에 대한 가이드가 있으나, 대부분 실행 되지 않는다. 
다음 포맷은 실제 web console에서 예제 데이터로 제시되고 있는 것을 참조하였다. 
```json
{"dialog":[{"content":"<<질문>>","role":"user"},{"content":"<<응답>>","role":"assistant"}]}
{"dialog":[{"content":"<<질문>>","role":"user"},{"content":"<<응답>>","role":"assistant"}]}
...
```

실제 샘플
```json
{"dialog":[{"content":"Consigliami 5 nomi per il mio cucciolo di dobberman","role":"user"},{"content":"Ecco 5 nomi per il tuo cucciolo di dobermann:\n\n- Zeus\n- Apollo\n- Thor\n- Athena\n- Odin","role":"assistant"}]}
{"dialog":[{"content":"Necesito c\u00f3digo de programaci\u00f3n","role":"user"},{"content":"\u00a1Claro! \u00bfCu\u00e1l es el objetivo del programa? \u00bfCuales son las caracter\u00edsticas y requisitos del programa? \u00bfEn qu\u00e9 lenguaje de programaci\u00f3n quieres el c\u00f3digo?","role":"assistant"}]}
```

--- modified ---
















