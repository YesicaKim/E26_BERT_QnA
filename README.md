# 학습 결과 정리

- ***Base Model 보다 Pre-trained Model의 성능이 Validation Accuracy 관점에서 0.258 높았다.***
- ***Pre-trained Model에서 3가지 실험을 했는데, 정답을 맞추는 갯수가 감소하는 것을 관찰할 수 있었다.*** 
    - ***base model에서 맞추지 못하는 문제를 Pre-trained Model이 맞춘 경우***
        ![bert_base_pre_trained](https://user-images.githubusercontent.com/39249809/99486070-efd5ac80-29a6-11eb-83a3-bbf0f64766e4.png)
    - ***layer를 4에서 6으로 늘림: Pre-trained 1에서 맞추지 못한 경우를 Pre-trained 2에서 맞춘 경우***
        ![bert_pre_trained_1_2](https://user-images.githubusercontent.com/39249809/99486074-f106d980-29a6-11eb-88f0-a5da9461f433.png)
    - ***multi-head attention 수를 4에서 8로 늘림: Pre-trained 1에서 맞추지 못한 경우를 Pre-trained 2에서 맞춘 경우***
        ![bert_pre_trained_2_3](https://user-images.githubusercontent.com/39249809/99486076-f19f7000-29a6-11eb-82f0-824759ef870c.png)
        
# (1) Base Model (Pre-training 없음)

- learning_rate=5e-4
- config
    - d_ff': 1024
    - d_head': 64
    - d_model': 256
    - dropout': 0.1
    - i_pad': 0
    - layernorm_epsilon': 0.001
    - n_head': 4
    - n_layer': 3
    - n_seq': 384
    - n_vocab': 32007

- Total params: 10,662,914

- ***Total eval loss: 7.9526, Total eval acc: 0.2918***

- Number of answer failed : ***70 Answers Failed*** (Total 102 Questions)

![bert_base_model](https://user-images.githubusercontent.com/39249809/99486065-eea47f80-29a6-11eb-8d73-64590070903b.png)

# (2) Pre-trained model 1

- learning_rate=5e-4
- config
    - d_ff': 1024
    - d_head': 64
    - d_model': 256
    - dropout': 0.1
    - i_pad': 0
    - layernorm_epsilon': 0.001
    - n_head': 4
    - n_layer': 3
    - n_seq': 384
    - n_vocab': 32007

- Total params: 10,662,914

- ***Total eval loss: 8.2706, Total eval acc: 0.3176***

- Number of answer failed : ***78 Answers Failed*** (Total 102 Questions)

![bert_pre_trained_1](https://user-images.githubusercontent.com/39249809/99486072-f06e4300-29a6-11eb-83d4-26e70e831cc0.png)


# (3) Pre-trained model 2

- learning_rate=***1e-4***
- config
    - d_ff': 1024
    - d_head': 64
    - d_model': 256
    - dropout': 0.1
    - i_pad': 0
    - layernorm_epsilon': 0.001
    - n_head': 4***
    - ***n_layer': 6***
    - n_seq': 384
    - n_vocab': 32007

- ***Total params: 13,032,194***

- ***Total eval loss: 8.1025, Total eval acc: 0.3011***

- Number of answer failed : ***79 Answers Failed*** (Total 102 Questions)

![bert_pre_trained_2](https://user-images.githubusercontent.com/39249809/99486075-f106d980-29a6-11eb-9601-898554f8e92b.png)


# (4) Pre-trained model 3


- learning_rate=***1e-4***
- config
    - d_ff': 1024
    - ***d_head': 32***
    - d_model': 256
    - dropout': 0.1
    - i_pad': 0
    - layernorm_epsilon': 0.001
    - ***n_head': 8***
    - ***n_layer': 6***
    - n_seq': 384
    - n_vocab': 32007

- ***Total params: 13,032,194***

- ***Total eval loss: 7.8230, Total eval acc: 0.2949***

- Number of answer failed : ***90 Answers Failed*** (Total 102 Questions)

![bert_pre_trained_3](https://user-images.githubusercontent.com/39249809/99486078-f2380680-29a6-11eb-85f2-3ee79e163f85.png)
