# Learning to Cartoonize Using White-box Cartoon Representations
paper : https://openaccess.thecvf.com/content_CVPR_2020/papers/Wang_Learning_to_Cartoonize_Using_White-Box_Cartoon_Representations_CVPR_2020_paper.pdf


git : https://github.com/SystemErrorWang/White-box-Cartoonization

![image](https://user-images.githubusercontent.com/71298482/147909527-30cf4d28-5319-4ef9-9d06-c0160652e1de.png)


만화 그리는 사람의 행동 컨설팅을 한 결과, cartoon painting 방식에 크게 3가지로 구분함 → 3가지 representation으로 쪼개어 활용한다.

- surface representation
- structure representation
- texture representation

**Surface Reperesentation**

smooth 한 surface를 표현한다 → 만화가가 detail한 retouch 하기 전 대충 draft 하는 것에 착안한 방법

**Structure Representation**

sparse color block을 표현하기 위한 방법 → celluloid cartoon처럼 블럭을 색칠하는 것에 착안

**Texture Representation**

color와 무관한 texture 및 edge를 표현하기 위함


![image](https://user-images.githubusercontent.com/71298482/147997190-9174d15a-c031-4df1-afb3-9020e631cbe5.png)

**Proposed Approach**

The Surface Representation

- Image Smoothing과 global semantic structure를 유지하기 위해 guided filter 사용
    - guided filter?
    
     ![image](https://user-images.githubusercontent.com/71298482/147997236-6bcf1b61-2b24-470e-b8b3-9f06796bb153.png)
    
    - denoising을 위해 gaussian filter 적용시, edge가 뭉개지는 문제 존재
    - bilateral filter 사용시 edge는 살지만, 영상 기울기값 부근에서 왜곡이 발생할 수 있음

- Loss
   
   
   ![image](https://user-images.githubusercontent.com/71298482/147998018-b6a37097-46ca-4eee-82e2-d140d9d35aae.png)


The Structure Representation

- Felzenszwalb의 Superpixel image segementation 방법을 활용 + Selective Search
![image](https://user-images.githubusercontent.com/71298482/147997293-09e43bdf-1060-489b-8d7a-5362039db448.png)

https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=laonple&logNo=220925179894

- Region의 컬러값을 평균으로 취하지는 않고, adaptive하게 결정
    - adaptive 말고 average로 적용시, 전역적인 contrast가 낮거나 어두운 이미지를 얻거나, hazing effect 유발
    ![image](https://user-images.githubusercontent.com/71298482/147997374-b10256bf-f1c3-4f17-9471-2c5d83191cd9.png)

    - high level feature extract을 위해 vgg16 적용

- Loss

![image](https://user-images.githubusercontent.com/71298482/147998061-09bb6fce-913d-4c99-bafa-978c328cdab3.png)




The Texture Representation

- High- frequency feature 표현
    - real world photo와 cartoon 은 color, luminance(밝기) 정보로 쉽게 구분이 가능 → high frequency texture를 유지하면서 color 와 luminance의 영향을 줄여주기 위해 흑백으로 변환 + random하게 rgb를  섞어줌

- Loss

![image](https://user-images.githubusercontent.com/71298482/147998087-8c4d561d-c4ff-4535-84f3-522c52c2453a.png)

