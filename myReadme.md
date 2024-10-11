# error

## 错误1 34Bus 有时会报错
An error occurred during training:
Traceback (most recent call last):
  File "run.py", line 205, in main
    mean_reward = p.train_step()
  File "/root/code/ATLA_robust_RL/src/policy_gradients/agent.py", line 1108, in train_step
    avg_ep_reward = self.train_step_impl(adversary_step = False, increment_scheduler = (i==self.ADV_POLICY_STEPS-1))
  File "/root/code/ATLA_robust_RL/src/policy_gradients/agent.py", line 1143, in train_step_impl
    saps, avg_ep_reward, avg_ep_length = self.collect_saps(num_saps, collect_adversary_trajectory=adversary_step)
  File "/root/code/ATLA_robust_RL/src/policy_gradients/agent.py", line 842, in collect_saps
    output = self.run_trajectories(num_saps,
  File "/root/code/ATLA_robust_RL/src/policy_gradients/agent.py", line 554, in run_trajectories
    ret = self.multi_actor_step(next_actions, envs)
  File "/root/code/ATLA_robust_RL/src/policy_gradients/agent.py", line 406, in multi_actor_step
    new_state = env.reset()
  File "/root/code/ATLA_robust_RL/src/policy_gradients/custom_env.py", line 112, in reset
    start_state = self.env.reset(load_profile_idx=self.worker_idx)
  File "/root/code/ATLA_robust_RL/src/powergym/powergym/env.py", line 473, in reset
    self.circuit.reset()
  File "/root/code/ATLA_robust_RL/src/powergym/powergym/circuit.py", line 103, in reset
    self.compile() # this include resetting regulators in dss
  File "/root/code/ATLA_robust_RL/src/powergym/powergym/circuit.py", line 88, in compile
    self.dss.Text.Command = "compile " + self.dss_file
  File "/root/miniconda3/lib/python3.8/site-packages/dss/dss_capi_gr/IText.py", line 22, in Command
    self.CheckForError(self._lib.Text_Set_Command(Value))
  File "/root/miniconda3/lib/python3.8/site-packages/dss/_cffi_api_util.py", line 81, in CheckForError
    raise DSSException(error_num, self._get_string(self._lib.Error_Get_Description()))
dss._cffi_api_util.DSSException: (180, 'Line Code:300 not found.')

# results
## 汇总

### 34 Bus
#### 34Bus 训练 eps=0.15
nature
mean: -10.938817851589679, std:1.7763568394002505e-15, min:-10.93881785158968, max:-10.93881785158968
Random eps=0.15
mean: -12.071974619836054, std:0.29818021247946386, min:-12.869060644970276, max:-11.468984709851584
worst eps=0.15
mean: -11.192413672056562, std:1.7763568394002505e-15, min:-11.192413672056563, max:-11.192413672056563

#### 34Bus 训练 eps=0.3
nature
mean: -10.750718077698274, std:0.0, min:-10.750718077698274, max:-10.750718077698274
random eps=0.3
mean: -12.794254280615382, std:0.43103912794249527, min:-13.79323268788238, max:-11.705493033832061
worst eps=0.3
mean: -11.913870146259624, std:1.7763568394002505e-15, min:-11.913870146259626, max:-11.913870146259626


### 13Bus
#### 13 Bus 训练 eps=0.15
nature
mean: -6.174274571406734, std:0.0, min:-6.174274571406734, max:-6.174274571406734
Random eps=0.15 
mean: -6.77565109048962, std:0.1400259684496538, min:-7.084899770900996, max:-6.49402602984889
Worst 攻击 eps=0.15
mean: -6.237913092412653, std:0.0, min:-6.237913092412653, max:-6.237913092412653


python test.py /root/code/ATLA_robust_RL/atla_ppo_123Bus/agents/50d22a76-603f-449f-86fa-b565a8d6433c




