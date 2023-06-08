opensw23_teamLee
=============

Team Introduction
-------------

개인팀 : 201711326 이기천

Topic Introduction
-------------   
## :gem:   

![gan](https://github.com/Spstars/opensw23_teamLee/assets/83457482/6ada5498-a3cf-42c0-8196-925c90189765)


GAN은 Generative Adversarial Networks의 약자로 우리말로는 “적대적 생성 신경망”이라고 번역되는 AI기술 중 하나입니다.  GAN은 생성자와 판별자 학습 시키는 방식으로 작동하여, 실제 데이터와 비슷한 데이터를 생성합니다. 제가 사용할 StyleGAN은 낮은 해상도의 생성자와 판별자를 시작으로 마지막에는 목표로 하는 해상도의 생성자와 판별자를 갖도록 설계되어  점진적으로 해상도를 올리도록 하였습니다.   
   
해당 모델을 사용하여 가짜 이미지를 생성하거나, 사람의 사진을 웹툰의 그림으로 바꾸는 등 많은 활용이 가능합니다. 

사전 학습된 모델을 활용하여 랜덤한 가짜 이미지를 생성합니다. 또한  기본 사진을 공인분들의 모습으로 바꾸어보는데, 이를 투영이라고 하겠습니다.


---------------------------
Results
-------------
서양화 사전학습 네트워크와 이미지 생성을 이용해 서양 초상화를 생성했습니다.

![seed0849](https://github.com/Spstars/opensw23_teamLee/assets/83457482/51b3634d-0501-4290-af5c-a7ca4bc4ded9)

이미지 투영을 하는 프로그램에 유재석님 사진을 넣어, 임의로 주어진 인물이 유재석님을 닮게 하였습니다.

![proj0](https://github.com/Spstars/opensw23_teamLee/assets/83457482/ca67b88c-2516-479a-86c1-c3b67e983548)
![proj130](https://github.com/Spstars/opensw23_teamLee/assets/83457482/0072251f-9132-443b-be17-26134479fe97)

페이커 선수,김종국님 ,성시경님,캡틴 아메리카(크리스 에반스), 수지님, 그리고 저를 투영하여 이미지를 만들어보았습니다.



<details>
<summary>사진접기/펼치기</summary>

1.크리스 에반스
   
   ![cap](https://github.com/Spstars/opensw23_teamLee/assets/83457482/c5528226-d17f-48cc-aeb0-7038e5cd9fdb)
   
   
점점 불쾌할 수 있으니, 불쾌함을 많이 느낀다면 접는 것이 좋겠습니다.  
   
   
2.김종국
   
   ![김종국](https://github.com/Spstars/opensw23_teamLee/assets/83457482/98bc214d-4748-4f1e-99d9-802721a7683a)
   
  
3.성시경
   
   
   ![성시경](https://github.com/Spstars/opensw23_teamLee/assets/83457482/51f9354f-d77f-49d4-847f-ec1d7bd23f8f)
   
 
4.페이커 선수
   
   ![faker](https://github.com/Spstars/opensw23_teamLee/assets/83457482/c579ca3e-a1a7-4596-a28a-e5caa3fe0749)

5.수지
   
   ![suju](https://github.com/Spstars/opensw23_teamLee/assets/83457482/c34f9931-aba4-4ccd-a6c0-2ad4c85b2f09)   
   
   
6. 작성자
   
   
   ![me](https://github.com/Spstars/opensw23_teamLee/assets/83457482/34f71fee-cbee-41d1-90e1-3056a4510461)


</details>



---------------------------

Analysis/Visualization
-------------

투영의 경우를 말씀드리면 크리스 에반스님의 사진과 유재석님의 사진은 불쾌함 없이 투영하는데 성공했습니다.

하지만 모델은 안경을 쓴 분들에게 취약점을 보입니다. 안경을 눈썹으로 인식하거나, 강한 화장으로 인식하는 경우가 많았습니다.

유재석님이 쓴 안경은 무사히 인식했지만, 성시경님의 안경을 화장으로 인식하는 경우가 있었습니다. 올리고 싶지 않을 정도로 불쾌한 사진이 많이 나왔습니다. 

생성 횟수를 늘림으로서 원래 이미지에 가까워지게 시도할 수 있지만, FFHQ 사전 네트워크 학습의 한계로 불쾌한 사진이 많이 생성되고, 크게 도움이 되지 않습니다. 저의 경우에는 numsteps를 기본 값 1000에서 200으로 바꾸어 실행했습니다. 아래 페이커 선수의 500번 투영 영상에서 볼 수 있 듯, 200번 정도 반복하면 투영 사진이 크게 달라지지 않습니다.

페이커 선수를 500 step번 투영한 결과입니다. 200Step부터 결과가 거의 바뀌지 않았습니다. 빠른 결과를 위해서는 300번 정도의 반복을 주는 것이 좋아보입니다.

https://youtu.be/XJrJhpsnqaQ


생성의 경우에는 사전학습 네트워크에 따라 원하는 사진을 잘 생성해내지만, 자신이 원하는 종류의 사진을 지정해서 생성해낼 수 없는 것이 아쉽습니다.

특정 품종의 개나 특정 인물을 생성하기 위해서는 추가로 학습이 필요해 보입니다.

---------------------------
Installation
-------------


딥러닝 계산을 돕는 pytorch를 install하고, tdqm같은 보조 라이브러리를 다운받습니다.


라이브러리들은 로컬 환경뿐만 아닌 Colab환경에서도 실행할 떄도 필요하니, 파이썬 버전에 맞게 다운로드 받으면 되겠습니다.(파이썬 버전 3.7, pytorch 버전 1.7,1.8,1.9 권장) 

    !pip install torch==1.8.0+cu111 torchvision==0.9.0+cu111 torchaudio==0.8.0 -f https://download.pytorch.org/whl/torch_stable.html
    !pip install requests tqdm pyspng ninja imageio-ffmpeg numpy imageio


그 뒤에, git clone 명령어로 git을 클론합니다.


     !git clone https://github.com/Spstars/opensw23_teamLee.git
     
해당 repo를 사용할 준비가 완료되었으며 generate.py로 새로운 이미지를 만들 수 있습니다.



로컬환경에서 사진을 생성할떄는 generate.py를 사용합니다. 사전 훈련된 네트워크를 통해, 과거의 서양 초상화 이미지를 생성합니다.


    python generate.py --outdir=out --trunc=1 --seeds=85,265,297,849  --network=https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada-pytorch/pretrained/metfaces.pkl


--network로 사전 학습된 네트워크를 불러와 사용할 수 있습니다. --network 파라미터를 조절하면 되겠습니다.

* Metface(서양화) 네트워크 : https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada-pytorch/pretrained/metfaces.pkl 
* FFHQ(인물 사진) 네트워크 :  https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada-pytorch/pretrained/ffhq.pkl
* 자동차 사진 네트워크 : https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada-pytorch/pretrained/cifar10.pkl
* 고양이 네트워크 : https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada-pytorch/pretrained/afhqcat.pkl
* 강아지 네트워크 : (https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada-pytorch/pretrained/afhqdog.pkl



자신의 이미지를 이용하여 이미지를 생성하고 싶다면 projector.py를 사용하면 됩니다. out 디렉토리에 결과물이 저장되며, --target의 위치를 사용자가 조절해주시길 바랍니다. 만족스러운 결과물이 300번의 반복안에 기본 값을 300으로 지정했지만 --num-steps을 지정하여 반복 횟수를 바꿀 수 있습니다. 



    python projector.py --outdir=out --target=pics/kim.png  --network=https://nvlabs-fi-cdn.nvidia.com/stylegan2-ada-pytorch/pretrained/ffhq.pkl --num-steps 300


out 디렉토리에 projected_w.npz이 저장되게 되며, projector에서 훈련한 network를 통해 추가로 그림을 생성할 수 있습니다.


    python generate.py --outdir=out --projected-w=out/projected_w.npz  --network=ffhq.pkl

만약 CPU 환경에서 파일을 생성하고 싶다면 force_fp32=True 옵션을 generate.py 와 projector.py 에 있는 G.synthesis()함수에 추가하면 됩니다.


Colab에서는 conda 가상환경을 이용해 python의 버전을 3.7로 다운그레이드합니다. 

    ! wget https://repo.anaconda.com/miniconda/Miniconda3-py37_4.9.2-Linux-x86_64.sh
    ! chmod +x Miniconda3-py37_4.9.2-Linux-x86_64.sh
    ! bash ./Miniconda3-py37_4.9.2-Linux-x86_64.sh -b -f -p /usr/local
    import sys
    sys.path.append('/usr/local/lib/python3.7/site-packages/')
    !which conda  # should return /usr/local/bin/conda
    !conda --version
    !ls /usr/local/lib/python3.7/dist-packages

train.py와 dataset_tool.py에 따라서 데이터셋과 학습을 준비하면 되겠습니다.

    !python3.7 train.py --data=[데이터경로] --source==[모델 저장 위치]      

---------------------------

Presentation
-------------


https://youtu.be/Aq98IffyBb0


---------------------------
