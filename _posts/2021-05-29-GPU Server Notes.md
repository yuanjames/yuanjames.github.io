---
layout: post
comments: false
title : GPUs Server Notes
description: Guidelines for SMML HWU GPUs
categories: [Knowlegde Note]
---

1. Contact HW MACS admin to get the grant for accessing GPUs.

2. The command `ssh xxx@ssh.macs.hw.ac.uk` with the password to access into MACS network. 

3. The command `ssh thanos` to connect GPUs resources. You may find the files and directory by `ls`, or `ls -l` for more details. thanos and ssh.macs.hw.ac.uk share the same home directonry.

4. You may find the conda from `/opt/anaconda3/bin`. Conda is an open-source, cross-platform, language-agnostic package manager and environment management system.

5. Add the path `'export PATH="/opt/anaconda3/bin:$PATH"'` into `~/.bashrc` . Then, you can use the command `conda` in your home directory.

6. The `bashrc` file is not executed (for no login shell), so you need to `vim ~/.bash_profile` and add the below code. Otherwise, you need to do `source ~/.bashrc` every time when you log in by `ssh`.

        ```
        if [ -f ~/.bashrc ] ; then

        source .bashrc

        fi
        ```

7. Execute the command `source ~/.bashrc` to take effect.

8. The command `conda create -n myenv python=3.*` is used to create your python environment.

9. After you create the myenv, you can use the command `source activate myenv` to activate and get in the environment.

10. `conda ***` install your required packages/libs.

11. The Command `nvidia-smi` can be used to check GPU peformance and information, `nvidia-smi -l 1` to update the GPU (dynamic) information per second. `htop` can be used to check CPU information.

12. If you suspend your programme manually, remember to release GPU memory by `kill -9 PID`.

13. If you do not want you programme suspended when you log out, please use `nohup`. For example, `nohup python xxx.py > output.txt 2>&1 &`. 2>1& means the stderr will be directed to stdout. see details [nohup](https://en.wikipedia.org/wiki/Nohup)

14. In order to upload your code to server, you can run `git clone` (if you have already build the repositoary in Github, Gitlab etc). Also, you can use `git pull` to update your code in server. Do remember, your code may have some outputs (e.g., csv), they are not tracked by git until the commit, which means the outputs will not be synchronized (deleted) by `git pull`. In case the ouputs affects next round experimental output, you can `rm xxx` or `git clean` them.

15. If you have some outputs (e.g. txt, csv), you can use `scp xxx@ssh.macs.hw.ac.uk:~/xxx/xxx/targetfile ~/localfile` to copy the file from server to local. see details [scp](https://en.wikipedia.org/wiki/Secure_copy_protocol#:~:text=Secure%20copy%20protocol%20(SCP)%20is,Protocol%20and%20the%20program%20itself.)

16. If you are not familiar with Unix commands, you can use [Remote Development using SSH](https://code.visualstudio.com/docs/remote/ssh).

17. Specify a GPU to run your programme by `os.environ['CUDA_VISIBLE_DEVICES'] = '2'`

18. For convenience, you can `vim  ~/.ssh/config` and add the below code. Then, you can use `ssh hw` to log in, instead of `ssh xxx@ssh.macs.hw.ac.uk`. This revision also works for `scp`.

                ```
                Host hw

                Hostname ssh.macs.hw.ac.uk

                User xxx
                ```

19. You may favour [tmux terminal](https://en.wikipedia.org/wiki/Tmux), it provides more features than ubuntu terminal.

20. When you run your code in GPUs, strongly suggest you set appropriate batch size (128, 256, etc), larger batch size will help GPUs release more power.

21. GPU memory and utility are affected each other to some degree. Memory consuming depends on the size and complexity of model, and batch size. Large batch size will increase the GPU utility. However, the utility really also depends on model complexity. If a model simple enough, whatever how large of your batch size, the utility always keeps a low level.

22. Using Pytorch no_grad() when you evaluate or test model would help you to improve GPUs utilities and save GPUs memory. You can also manually release GPU memory and reflect on `Nvidia-smi` by `torch.cuda.empty_cache()`. Even Pytorch will release GPU memory automatically like Python memory management, but it may not reflect on nividia-smi immediately.

23. By default, TensorFlow maps nearly all of the GPU memory of all GPUs (subject to CUDA_VISIBLE_DEVICES) visible to the process. This is done to more efficiently use the relatively precious GPU memory resources on the devices by reducing memory fragmentation. To limit TensorFlow to a specific set of GPUs we use the `tf.config.experimental.set_visible_devices` method. [Details](https://www.tensorflow.org/guide/gpu#:~:text=Limiting%20GPU%20memory%20growth,-By%20default%2C%20TensorFlow&text=To%20limit%20TensorFlow%20to%20a,config.experimental.set_visible_devices%20method.&text=In%20some%20cases%20it%20is,is%20needed%20by%20the%20process.)