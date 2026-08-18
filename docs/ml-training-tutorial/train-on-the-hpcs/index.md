# Tutorial for training on HPC

- Each HPC is a cluster of computers. Each computer is called a **node**. After
  login an HPC, we can access the **file system**, e.g., `home/` or `scratch/`,
  and we can put our stuff, e.g., code or data, in a folder. File systems for
  Sulis and Alice are discussed
  [here](https://sulis-hpc.github.io/gettingstarted/storage.html) and
  [here](https://uniofleicester.sharepoint.com/sites/Research-Computing/SitePages/filesystems-alice.aspx),
  respectively.
- When running our Python code on an HPC, we need to have a **Python
  environment**, which will be detailed in [Python Venv Section](python-venv.md).
- An HPC uses a **job schedule system** to manage jobs, e.g., submit jobs,
  monitor jobs, delete jobs, etc. Both Alice and Sulis use Slurm. The ways to
  manage jobs in the job system are elaborated [here](slurm.md).
- When training a model on an HPC with multiple GPUs, we need to use the
  distributed package in PyTorch, which will be further discussed
  [here](training-with-multiple-gpus.md).
- Finally, HPCs usually use Linux systems, therefore, we usually use ssh-related
  stuff to interact with an HPC, including login or uploading code from our
  computer to an HPC or copying results from an HPC to our computer, etc. The
  commonly used ssh commands are elaborated [here](ssh-related.md).
- When using an HPC for training, many issues may be encountered. The common
  issues are summarized [here](tips-for-ml-training.md).
- A sample of the framework for training an ML model on the HPC is available on
  [GitHub](https://github.com/YihangZhu/train_ml_on_HPC).
