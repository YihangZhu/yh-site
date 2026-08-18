# Training with multiple GPUs

## Distributed training

A sample of the framework for running distributed training can be found
[here](https://github.com/YihangZhu/train_ml_on_HPC.git).

An overview of the distributed training process is provided using the figure
below.

!!! info "Figure to add"
    Overview diagram of the distributed training process. Save it from the
    [original page](https://sites.google.com/view/zhuyihang/ml-training-tutorial/train-on-the-hpcs/training-with-multiple-gpus)
    into `docs/assets/ddp-overview.png`, then replace this block with
    `![Distributed training overview](../../assets/ddp-overview.png)`.

Let's assume that we are running experiments with a SLURM job system, using two
nodes and 3 GPUs per node. `main.py` is our job as illustrated in the figure
below. After we execute our job using `srun main.py` (see the script
[here](slurm.md) for details), `main.py` will be executed separately and
independently in each of the two nodes. This means that if the variables are
modified or created in `main.py` in one node, it will not affect the variables
of `main.py` in the other nodes.

Then in each node, the multiprocessing package will be used to execute the code
in `main.py`, let's call it `main_worker()`, in parallel at each of the three
GPUs available in the node. So now actually `main_worker()` is executed by six
GPUs in parallel, considering the two nodes that we are using.

In each `main_worker()`, we will create a dataset, learning model, and optimizer
and train the learning model with multiple epochs. So we need something to
provide a tunnel for communication between the six GPUs and synchronize the
tasks running in the six GPUs. The distributed package in python (DDP) is the
hero plays the role. The DDP will be initialized at the beginning of the code
`main_worker()` via function `init_process_group(...)` which requires global GPU
rank (see the figure below), an IP address and a free port (see the script
[here](slurm.md) for details of how to get them).

## Principles when using the DDP

1. if we set the total number of GPUs as 10 while only having six GPUs,
   `init_process_group(...)` will keep waiting until the job is killed
   automatically after a long waiting.
2. Each GPU has a learning model created. The learning models of the six GPUs
   are identical. At each epoch, `distributed_sampler` in the DDP will assign
   each GPU a mini-batch of the same batch size, e.g. 128. So in total actually
   we are using a batch size of 128*6=786 for the training. Then each learning
   model processes its mini-batch and gets gradients. The DDP will average out
   all the gradients and send them to each GPU, then each learning model is
   updated using the same gradients.
3. The training errors are different at different GPUs, because they are using
   different mini-batches.
4. The testing errors are identical at different GPUs, so we only need to print
   out the best test error and save the corresponding checkpoint at one GPU,
   e.g., at the GPU which has a Global GPU rank of 0.

Each GPU is controlled by one process which is also called a CPU or a worker or
a core. Usually, we request a bunch of workers when executing `srun main.py`,
e.g., 42 works per GPU. So if we use 12 workers per GPU for the dataloader and
one is used for controlling the GPU, then 29 workers will remain idle.

You can try out the DDP yourself with the framework available
[here](https://github.com/YihangZhu/train_ml_on_HPC).

## Further reading

How to run tasks with multiple GPU and PyTorch:
[here](https://yangkky.github.io/2019/07/08/distributed-pytorch-tutorial.html),
[here](https://github.com/PrincetonUniversity/multi_gpu_training/tree/main/02_pytorch_ddp)
and [here](https://gist.github.com/TengdaHan/1dd10d335c7ca6f13810fff41e809904)

How to get the IP address of the node:
[here](https://tuni-itc.github.io/wiki/Technical-Notes/Distributed_dataparallel_pytorch/)

How to find a free port:
[here](https://stackoverflow.com/questions/28989069/how-to-find-a-free-tcp-port)
and
[here](https://stackoverflow.com/questions/1365265/on-localhost-how-do-i-pick-a-free-port-number)
