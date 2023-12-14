# reinforece-DDPG-
openai gymnasium mountaincar continuous example

ddpg 알고리즘으로 문제를 해결하였습니다.

하나의 알고리즘을 파라미터 조정, 리워드 계산방식 변화를 통해 3개의 모델을 만들어보았습니다.

1. reward1 : 속도 관련 절대값 함수 >>  reward = float(- step/500 + abs(car_vel)/500)
   주요 파라미터 :
   
아래의 [model weight] 받은 후 테스트 코드 돌리기 (1번 모델만 저장하여서 업로드하였음)
acotormountain_car_r1.h5
criticmountain_car_r1.h5
================================================================================
## 학습된 weights로 테스트 >> 50번째 칸에 있음 앞에 라이브러리 전부 설치해야 돌아감
ENV_NAME = 'MountainCarContinuous-v0'
env = gym.make(ENV_NAME)

state_size = env.observation_space.shape[0]
action_size = env.action_space.shape[0]
max_action = env.action_space.high[0]

# 비디오 레코딩

agent.actor.load_weights("/content/save_weights/actor/mountain_car_r1.h5")
agent.critic.load_weights("/content/save_weights/critic/mountain_car_r1.h5")
env = RecordVideo(env, './test', episode_trigger =lambda episode_number: True )



time = 0
state = env.reset()

while True:
    action = agent.actor(tf.convert_to_tensor([state], dtype=tf.float32)).numpy()[0]
    # print(action.shape)
    state, reward, done, _ = env.step(action)
    time += 1

    if done:
       print('try: ', time, 'Reward: ', reward)
       break

### video
show_video(mode='test')
================================================================================
2. reward1 : 속도 관련 절대값 함수 >>  reward = float(- step/500 + abs(car_vel)/500)
   주요 파라미터 :
   파라미터들을 학습시간이 더 걸려도 성능을 높이는 방향으로 일부 조정
   



3. reward2 : 속도 관련 2차 함수 >>  reward = float(- step/500 + abs(car_vel)/500)
   주요 파라미터 :
   파라미터들을 학습시간이 더 걸려도 성능을 높이는 방향으로 일부 조정
   
