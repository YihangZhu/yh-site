# Tips for training an ML model

After submitting a job, revising, or deleting the code will not impact the
submitted job.

Using pinmemory can speed up dataloader. It is mentioned
[here](https://discuss.pytorch.org/t/when-to-set-pin-memory-to-true/19723).

In dataloader, pin memory can not be used together with `persistent_worker`. The
issue is discussed
[here](https://github.com/pytorch/pytorch/issues/48370).

When loading models trained in parallel, an extra step is required:
[here](https://discuss.pytorch.org/t/failed-to-load-model-trained-by-ddp-for-inference/84841).

`tensor.detach()` returns a new tensor as discussed
[here](https://discuss.pytorch.org/t/detach-no-grad-and-requires-grad/16915/10).

Runtime on Sulis: given that we can only use `home/` folder, the runtime highly
depends on the load on the file system. Specifically, if the load on `home/`
directory is high, our code may require a much longer runtime compared to when
the load on `home/` is low.

FP16 vs FP32:
[here](https://datascience.stackexchange.com/questions/73107/fp16-fp32-what-is-it-all-about-or-is-it-just-bitsize-for-float-values-pytho)

get time in bash:
[here](https://unix.stackexchange.com/questions/428217/current-time-date-as-a-variable-in-bash-and-stopping-a-program-with-a-script)

When enumerating data loader while using multiple GPUs it could time a long
time. The issue is discussed
[here](https://discuss.pytorch.org/t/enumerate-dataloader-slow/87778/4), and the
solution (multi-epoch data loader) works very well. Experimental results are as
follows.

!!! info "Figure to add"
    Chart of the multi-epoch dataloader experimental results. Save it from the
    [original page](https://sites.google.com/view/zhuyihang/ml-training-tutorial/train-on-the-hpcs/tips-for-ml-training)
    into `docs/assets/dataloader-results.png`, then replace this block with
    `![Experimental results](../../assets/dataloader-results.png)`.
