# reinforece-DDPG-
openai gymnasium mountaincar continuous example

ddpg 알고리즘으로 문제를 해결하였습니다.

하나의 알고리즘을 파라미터 조정, 리워드 계산방식 변화를 통해 3개의 모델을 만들어보았습니다.

1. reward1 : 속도 관련 절대값 함수 >>  reward = float(- step/500 + abs(car_vel)/500)
   주요 파라미터 :
   
아래의 [model weight] 받은 후 테스트 코드 돌리기 (1번 모델만 저장하여서 업로드하였음)
acotormountain_car_r1.h5
criticmountain_car_r1.h5

2. reward1 : 속도 관련 절대값 함수 >>  reward = float(- step/500 + abs(car_vel)/500)
   주요 파라미터 :
   파라미터들을 학습시간이 더 걸려도 성능을 높이는 방향으로 일부 조정
   



3. reward2 : 속도 관련 2차 함수 >>  reward = float(- step/500 + abs(car_vel)/500)
   주요 파라미터 :
   파라미터들을 학습시간이 더 걸려도 성능을 높이는 방향으로 일부 조정
   
