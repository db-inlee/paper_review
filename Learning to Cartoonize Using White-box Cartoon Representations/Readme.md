# Learning to Cartoonize Using White-box Cartoon Representations
paper : https://arxiv.org/abs/2107.04551


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
