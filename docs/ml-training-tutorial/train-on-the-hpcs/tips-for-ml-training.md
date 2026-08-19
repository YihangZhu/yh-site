# Tips for training an ML model

Once you submit a job, later revising or deleting the code will not affect
that already-submitted job.

Using `pin_memory` can speed up the dataloader. It's discussed
[here](https://discuss.pytorch.org/t/when-to-set-pin-memory-to-true/19723).

In the dataloader, `pin_memory` cannot be used together with
`persistent_workers`. The issue is discussed
[here](https://github.com/pytorch/pytorch/issues/48370).

When loading a model that was trained in parallel (DDP), an extra step is
required — see
[here](https://discuss.pytorch.org/t/failed-to-load-model-trained-by-ddp-for-inference/84841).

`tensor.detach()` returns a new tensor, as discussed
[here](https://discuss.pytorch.org/t/detach-no-grad-and-requires-grad/16915/10).

Runtime on Sulis: since we can only use the `home/` folder, runtime depends
heavily on the load on that file system. If `home/` is under heavy load, our
code can take much longer to run than when the load is low.

FP16 vs FP32:
[here](https://datascience.stackexchange.com/questions/73107/fp16-fp32-what-is-it-all-about-or-is-it-just-bitsize-for-float-values-pytho)

Getting the time in Bash:
[here](https://unix.stackexchange.com/questions/428217/current-time-date-as-a-variable-in-bash-and-stopping-a-program-with-a-script)

When enumerating the dataloader while using multiple GPUs, it could take a
long time. The issue is discussed
[here](https://discuss.pytorch.org/t/enumerate-dataloader-slow/87778/4), and
the solution (multi-epoch dataloader) works very well. Experimental results
are as follows.

!!! info "Figure to add"
    Chart of the multi-epoch dataloader experimental results. Save it from the
    [original page](https://sites.google.com/view/zhuyihang/ml-training-tutorial/train-on-the-hpcs/tips-for-ml-training)
    into `docs/imgs/dataloader-results.png`, then replace this block with
    `![Experimental results](../../imgs/dataloader-results.png)`.
