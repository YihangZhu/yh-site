# Training with multiple GPUs

## Distributed training

A sample of the framework for running distributed training can be found
[here](https://github.com/YihangZhu/train_ml_on_HPC.git).

An overview of the distributed training process is provided using the figure
below.

[![srun launches main.py once per node; the multiprocessing package runs main_worker() on each of the three GPUs in a node; the distributed package synchronises all six GPUs over an IP address and port. Node 0 holds global GPU ranks 0-2 and node 1 holds ranks 3-5, for a world size of 6.](../../imgs/ddp.png)](../../imgs/ddp.png)

Let's assume that we are running experiments with a SLURM job system, using two
nodes and 3 GPUs per node. `main.py` is our job as illustrated in the figure
below. After we execute our job using `srun main.py` (see the script
[here](slurm.md) for details), `main.py` will be executed separately and
independently on each of the two nodes. This means that if variables are
modified or created in `main.py` on one node, they will not affect the
variables of `main.py` on the other node.

Then on each node, the multiprocessing package is used to execute the code in
`main.py` — let's call it `main_worker()` — in parallel on each of the three
GPUs available in the node. So now `main_worker()` is actually executed by six
GPUs in parallel, considering the two nodes we are using.

In each `main_worker()`, we create a dataset, a learning model, and an
optimizer, and train the model over multiple epochs. So we need something to
provide a tunnel for communication between the six GPUs and synchronise the
tasks running on them. The distributed package in PyTorch (DDP) is what
handles this. DDP is initialised at the start of `main_worker()` via
`init_process_group(...)`, which requires the global GPU rank (see the figure
below), an IP address, and a free port (see the script [here](slurm.md) for
details of how to get them).

## Principles when using DDP

1. If the total number of GPUs is set to 10 while only six are available,
   `init_process_group(...)` will keep waiting until the job is automatically
   killed after a long wait.
2. Each GPU has its own learning model. The learning models on the six GPUs
   are identical. At each epoch, `distributed_sampler` in DDP assigns each
   GPU a mini-batch of the same batch size, e.g. 128. So in total we are
   actually using a batch size of 128*6=768 for training. Each learning model
   then processes its mini-batch and computes gradients. DDP averages out all
   the gradients and sends them to each GPU, and each learning model is then
   updated using the same gradients.
3. Training errors differ across GPUs, because each is using a different
   mini-batch.
4. Testing errors are identical across GPUs, so we only need to print the
   best test error and save the corresponding checkpoint on one GPU — e.g.,
   the GPU with a global GPU rank of 0.

Each GPU is controlled by one process, also called a CPU, a worker, or a core.
Usually we request a bunch of workers when executing `srun main.py`, e.g., 42
workers per GPU. So if we use 12 workers per GPU for the dataloader and one
for controlling the GPU, 29 workers remain idle.

You can try out DDP yourself with the framework available
[here](https://github.com/YihangZhu/train_ml_on_HPC).

## Further reading

How to run tasks with multiple GPUs and PyTorch:
[here](https://yangkky.github.io/2019/07/08/distributed-pytorch-tutorial.html),
[here](https://github.com/PrincetonUniversity/multi_gpu_training/tree/main/02_pytorch_ddp)
and [here](https://gist.github.com/TengdaHan/1dd10d335c7ca6f13810fff41e809904)

How to get the IP address of the node:
[here](https://tuni-itc.github.io/wiki/Technical-Notes/Distributed_dataparallel_pytorch/)

How to find a free port:
[here](https://stackoverflow.com/questions/28989069/how-to-find-a-free-tcp-port)
and
[here](https://stackoverflow.com/questions/1365265/on-localhost-how-do-i-pick-a-free-port-number)
