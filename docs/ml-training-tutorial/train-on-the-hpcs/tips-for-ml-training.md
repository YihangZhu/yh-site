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
the solution (multi-epoch dataloader) works very well.

## Impact of batch size, number of workers, and dataloader

Using iNaturalist2018, a standard ResNet50, running for 2 epochs, with the
multi-epoch dataloader:

| workers | GPUs | batch size per GPU | time per epoch (s) | prep time (s) | total time (s) |
|--:|--:|--:|--:|--:|--:|
| 10 | 12 | 64 | 420 | 66 | 905 |
| 20 | 12 | 64 | 300 | 119 | 802 |
| 40 | 12 | 64 | 350 | 248 | 966 |

Same setup, with the standard dataloader:

| workers | GPUs | batch size per GPU | time per epoch (s) | prep time (s) | total time (s) |
|--:|--:|--:|--:|--:|--:|
| 10 | 12 | 64 | 650 | 5 | 1338 |
| 20 | 12 | 64 | 650 | 5 | 1263 |
| 40 | 12 | 64 | 650 | 4 | 1308 |

Using CIFAR10, a standard ResNet32, running for 200 epochs, with the
multi-epoch dataloader:

| workers | GPUs | batch size per GPU | total batch size | prep time (s) | total time (s) | runtime (s) | best acc (%) |
|--:|--:|--:|--:|--:|--:|--:|--:|
| 10 | 12 | 64 | 768 | 58 | 544 | 486 | 91.92 |
| 15 | 12 | 64 | 768 | 84 | 564 | 480 | 91.44 |
| 20 | 12 | 64 | 768 | 110 | 592 | 482 | 91.65 |
| 40 | 12 | 64 | 768 | 214 | 703 | 489 | 91.83 |
| 10 | 12 | 32 | 384 | 57 | 993 | 936 | 92.11 |
| 10 | 12 | 128 | 1536 | 57 | 322 | 265 | 89.78 |
| 15 | 6 | 128 | 768 | 91 | 518 | 427 | 91.77 |
| 15 | 3 | 256 | 768 | 91 | 509 | 418 | 91.31 |

Results suggest that:

- The first two tables show that the multi-epoch dataloader takes much less
  time than the standard dataloader, and using fewer workers saves even more
  time with it.
- The number of workers shouldn't be too large or too small — around 15 seems
  to work well.
- Batch size affects both performance and runtime: the smaller the batch
  size, the longer the runtime.
- When GPU memory allows it for the target batch size, using fewer GPUs is
  better, likely because gradient communication between GPUs takes time.
