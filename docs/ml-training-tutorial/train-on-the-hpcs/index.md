# Tutorial for training on an HPC

- Each HPC is a cluster of computers. Each computer is called a **node**. After
  logging in to an HPC, we can access the **file system**, e.g., `home/` or
  `scratch/`, and put our stuff, e.g., code or data, in a folder. File systems
  for Sulis and Alice are discussed
  [here](https://sulis-hpc.github.io/gettingstarted/storage.html) and
  [here](https://uniofleicester.sharepoint.com/sites/Research-Computing/SitePages/filesystems-alice.aspx),
  respectively.
- When running our Python code on an HPC, we need a **Python environment**,
  which is detailed in the [Python venv section](python-venv.md).
- An HPC uses a **job scheduling system** to manage jobs, e.g., submit jobs,
  monitor jobs, delete jobs, etc. Both Alice and Sulis use Slurm. Managing jobs
  in the job system is covered [here](slurm.md).
- When training a model on an HPC with multiple GPUs, we need to use the
  distributed package in PyTorch, which is further discussed
  [here](training-with-multiple-gpus.md).
- Finally, HPCs usually run Linux, so we use SSH to interact with them —
  logging in, uploading code from our computer, or copying results back, etc.
  The commonly used SSH commands are covered [here](ssh-related.md).
- When using an HPC for training, many issues may come up. The common ones
  are summarised [here](tips-for-ml-training.md).
- A sample of the framework for training an ML model on the HPC is available on
  [GitHub](https://github.com/YihangZhu/train_ml_on_HPC).
