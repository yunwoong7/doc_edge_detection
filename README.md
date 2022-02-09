<h2 align="center">
Document outline detection
</h2>
<div align="center">
  <img src="https://img.shields.io/badge/python-v3.6-blue.svg"/>
  <img src="https://img.shields.io/badge/torch-v1.4.0-blue.svg"/>
  <img src="https://img.shields.io/badge/opencv-v4.5.5-blue.svg"/>
</div>

이미지를 다루다보면 특정 영역의 윤곽선 검출이 필요한 경우가 있습니다. 예를들면 촬영한 문서 이미지를 스캔한 이미지 형태로 만들기 위해 가장 큰 사각형의 영역을 찾는다거나 특정 물체의 경계를 찾기도 하고 나아가 이미지를 분석하거나 패턴을 파악하기 위해서도 사용됩니다. 일반적으로 가장 많이 알려진 edge detection algorithms은 Sobel, Canny, Prewiit, Roberts, Fuzzy Logic 방법 등이 있습니다.

![Sobel method](https://blog.kakaocdn.net/dn/5B8Ex/btrsRanr7r5/MusQYT0LZ25di0fCg7EOqK/img.png)

![Canny method](https://blog.kakaocdn.net/dn/vXpzg/btrsMaoFYMc/Bffh8G261wTyYewAsh6Ro0/img.png)

![Fuzzy Logic method](https://blog.kakaocdn.net/dn/en4W1v/btrsRQWMIaZ/jrRh4IXNDx9hwPleiWbXR1/img.png)

이미지 연산을 통한 윤곽선 검출은 임계값을 수동으로 적용해야 하는데 하나의 이미지에서 잘 적용되는 임계값은 다른 이미지에서 제대로 작동하지 않을 수 있습니다. 그리고 추출하려는 영역이 배경이미지와 대비가 잘 되지 않는 경우 윤곽선을 찾는건 매우 어렵고 복잡한 이미지 전처리가 필요 할 수도 있죠.

[Tesseract OCR을 소개하는 글](https://yunwoong.tistory.com/72?category=902345)에서 이미 이런 문제를 경험하기도 했습니다.

![correct detection](https://blog.kakaocdn.net/dn/NdJNT/btrsQpy73yN/lVDFoehdb66KeI0ckJhxr1/img.png)

![discorrect detection](https://blog.kakaocdn.net/dn/tIca9/btrsVJpo9QS/hLbouKTnsQzsGN2tkHjqb0/img.png)

수많은 촬영기기 (카메라/스캐너/팩스 등)와 다양한 촬영 환경 (조명/화각/배경 등) 을 고려하여 임계값을 설정하는 것은 불가능하기때문에 보편적으로 적용이 가능하도록 최대한 이미지를 보정하려고 하지만 한계가 있죠.

![img](https://blog.kakaocdn.net/dn/eO1GQ6/btrsWKVU2Q2/CEzoMHx8Uvak79vkNrxZH0/img.png)


이제 Deep Learning Model을 이용하여 이러한 한계를 해결해보려고 합니다. 알고리즘은 HED(Holistically-Nested Edge Detection)와 RCF(Richer Convolutional Features for Edge Detection) 두 알고리즘을 각각 사용하여 테스트 하였습니다. *(소개하는 알고리즘 이외에도 [다양한 Edge Detector](https://github.com/MarkMoHR/Awesome-Edge-Detection-Papers)가 있습니다.)*

![img](https://blog.kakaocdn.net/dn/4GnNP/btrsSvenlDV/KKVrCwV8vboV6t9wxVEgvk/img.png)

---

[**1. Holistically-Nested Edge Detection**](https://yunwoong.tistory.com/103)

* [HED Caffe 모델 파일 다운로드](https://drive.google.com/file/d/11wiyfDPdJsdhJTCECXmCF-P1euasGUy1/view?usp=sharing)

[**2. Richer Convolutional Features (RCF) for Edge Detection**](https://yunwoong.tistory.com/104)

* [사전 훈련된 모델 파일 다운로드](https://drive.google.com/file/d/15dl2GkxsRuy6ovWYZ8uGiYCgNwXAhcNj/view?usp=sharing)