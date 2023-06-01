# opensw23_teamLee

#Team Introduction

개인팀 : 201711326 이기천

------------------------
#Topic Introduction

GAN은 Generative Adversarial Networks의 약자로 우리말로는 “적대적 생성 신경망”이라고 번역되는 AI기술 중 하나입니다.  GAN은 생성자와 판별자 학습 시키는 방식으로 작동하여, 실제 데이터와 비슷한 데이터를 생성합니다. 제가 사용할 StyleGAN은 낮은 해상도의 생성자와 판별자를 시작으로 마지막에는 목표로 하는 해상도의 생성자와 판별자를 갖도록 설계되어  점진적으로 해상도를 올리도록 하였습니다.


해당 모델을 사용하여 가짜 이미지를 생성하거나, 사람의 사진을 웹툰의 그림으로 바꾸는 등 많은 활용이 가능합니다. Kaggle의 stanford-dogs-dataset을 활용하여 강아지를 생성하는 model을 만들어보고, model이 강아지를 어떻게 생성하는 지를 확인해보록 하겠습니다.

---------------------------
Results

![fakedog](https://github.com/Spstars/opensw23_teamLee/assets/83457482/3cd4dd47-7e95-4aa5-b403-a09dc5d3db23)

학습시간의 한계로, 배경이 아쉽게 나온 강아지를 볼 수있습니다.

Analysis/Visualization

#Installation

해당 내용은 StyleGan2을 학습하기 위해 Colab 환경을 사용한 예시입니다.


Colab에서 conda 가상환경을 이용해 python을 3.7로 다운그레이드합니다. 

    ! wget https://repo.anaconda.com/miniconda/Miniconda3-py37_4.9.2-Linux-x86_64.sh
    ! chmod +x Miniconda3-py37_4.9.2-Linux-x86_64.sh
    ! bash ./Miniconda3-py37_4.9.2-Linux-x86_64.sh -b -f -p /usr/local
    import sys
    sys.path.append('/usr/local/lib/python3.7/site-packages/')
    !which conda  # should return /usr/local/bin/conda
    !conda --version
    !ls /usr/local/lib/python3.7/dist-packages
    

Colab 환경에서 딥러닝 계산을 돕는 pytorch를 install하고, tdqm같은 보조 라이브러리를 다운받습니다.


이 라이브러리들은 로컬 환경에 실행할 떄도 필요하니, 파이썬 버전에 맞게 다운로드 받으면 되겠습니다.(파이썬 버전 3.7, pytorch 버전 1.7,1.8,1.9 권장) 

    !pip install torch==1.8.0+cu111 torchvision==0.9.0+cu111 torchaudio==0.8.0 -f https://download.pytorch.org/whl/torch_stable.html
    !pip install requests tqdm pyspng ninja imageio-ffmpeg==0.4.3 numpy

그 뒤에, git clone 명령어로 git을 클론합니다.

     !git clone https://github.com/NVlabs/stylegan2-ada-pytorch.git
     
해당 repo를 사용할 준비가 완료되었으며 train.py와 dataset_tool.py에 따라서 데이터셋과 학습을 준비하고, generate.py로 새로운 이미지를 만들 수 있습니다.


    #기존 파이썬 버전과 유의
    !python3.7 train.py --data=[데이터] --source==[모델 저장 위치]        


로컬환경에서 사진을 생성할떄는 generate.py를 사용합니다.

    python generate.py --outdir=out --trunc=1 --seeds=85,265,297,849  --network=https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada-pytorch/pretrained/metfaces.pkl

여기서 network에 자신이 만든 pkl파일을 넣으면 자신만의 모델을 만드는 것이 가능합니다.


Presentation