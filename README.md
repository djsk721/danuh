<p align="center" width="100%">


## Update Logs

- 2023.08.23: Polyglot-ko 1.3B를 기반으로 [AIHUB](https://aihub.or.kr/) 160만 개 데이터가 학습된 [Danuh-1.3B-V1.0]모델(QLoRA로 학습, 병합모델)


# Danuh: Korean translation model based on Polyglot-ko

[Polyglot-ko](https://huggingface.co/EleutherAI/polyglot-ko-1.3b)를 기반으로 만들어진 한국어 번역 모델


## danuh-1.3B-V1.0

### 데이터셋


[AIHUB "한국어-영어 번역(병렬) 말뭉치"](https://www.aihub.or.kr/aihubdata/data/view.do?currMenu=115&topMenu=100&aihubDataSe=realm&dataSetSn=126)


한국어-영어 전체 약 160만 문장의 데이터를 사용했습니다.

### 전처리
- i'm, we'll 등 과 같은 문장들을 풀어서 쓰도록 전처리
- 영문자 !, ?, ., ,(쉼표) 이외의 문자를 삭제

### 학습

#### V1.0

QLoRA를 사용해 RTX4080 16GB 1대로 학습을 진행했습니다.
- Epoch: 1
- learning-rate: 3e-4
- batch_size: 16
- Lora r: 8
- Lora target modules: query_key_value

<!-- ![Train Loss Graph]()
![Learning Rate Graph]() -->



## 한계점

- 160만 개의 데이터(추가적인 데이터 추가 필요)
- 문장과 단어 두가지 동시에 번역을 위한 추가적인 수정 필요

## TO DO LIST

- 데이터 추가 학습
- huggingface 및 wandb 연동을 통한 기록 필요
- Train Loss Graph와 Learning Rate Graph 기록 필요
- Loss 율이 생각보다 크게 줄지 않음(약 1.3)