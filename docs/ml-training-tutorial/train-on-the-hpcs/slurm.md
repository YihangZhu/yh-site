# Slurm

## Commonly used commands

- **submit an SBATCH job:** `sbatch job.slurm`. `job.slurm` can be echoed and
  submitted by executing a bash script, `launch.sh`, with `bash launch.sh`. Two
  samples of `launch.sh` are provided at the end of this page. When submitting
  an SBATCH job, the resource will be allocated to you for running the
  experiments and released immediately when your jobs are done. And your job
  will be running on the HPC even after you log out of the HPC.
- **request an interactive job:**

    ```bash
    srun --nodes=1 --ntasks-per-node=1 --cpus-per-task=42 --mem-per-cpu=3850 \
         --gres=gpu:ampere_a100:1 --partition=gpu --time=1:00:00 \
         --account=su004-xxx --pty bash -i
    ```

    The syntax is the same as when submitting an SBATCH job. The only difference
    is that when requesting an interactive job, the resource will be allocated to
    you and you can keep using it until you exit or reach the time limit that you
    requested, i.e., 40 hours here.

- **cancel a job:** `scancel job-id`
- **cancel all the jobs:** `scancel -u username`
- **monitor jobs:** `squeue`
- **monitor jobs of the user:** `squeue -u username`

Documents:
[here](https://docs.hpc.shef.ac.uk/en/latest/hpc/scheduler/index.html#submit-batch-bessemer)

Status code: can be found
[here](https://docs.hpc.shef.ac.uk/en/latest/referenceinfo/scheduler/SLURM/Common-commands/squeue.html)

## A simple sample

```bash
#!/bin/bash

# prepare the script.slurm for launching the job
echo "#!/bin/bash" > script.slurm
echo "#SBATCH --job-name=slurm_0" >> script.slurm      # the name of your job
echo "#SBATCH --output=ic_0.err" >> script.slurm       # a file for recording the print out of your experiment
echo "#SBATCH --nodes=1 " >> script.slurm              # request n nodes
echo "#SBATCH --ntasks-per-node=1" >> script.slurm     # total number of times running main.py
echo "#SBATCH --cpus-per-task=42" >> script.slurm      # each GPU contain 128 cpus (workers), each GPU is a task.
echo "#SBATCH --mem-per-cpu=3850" >> script.slurm      # required memory per cpu
echo "#SBATCH --gres=gpu:ampere_a100:1" >> script.slurm # maximum 3 GPUs per node.
echo "#SBATCH --partition=gpu" >> script.slurm
echo "#SBATCH --time=48:00:00" >> script.slurm         # maximum 48 hours of consecutive running
echo "#SBATCH --account=su004" >> script.slurm         # budget account of leicester university

echo "module load GCCcore/11.3.0" >> script.slurm
echo "module load Python/3.10.4" >> script.slurm
echo "source /gpfs/home/y/yz681/code/py3_10_4/bin/activate" >> script.slurm
echo "python --version" >> script.slurm
echo "cd /gpfs/home/y/yz681/code/ic/" >> script.slurm
echo "srun python main.py " >> script.slurm

cat script.slurm   # print the script to check whether everything is right.
sbatch script.slurm # launch the job
rm script.slurm     # remove script.slurm
```

## A comprehensive sample

```bash
#!/bin/bash

nodes=3        # the total number of nodes you request
gpus=3         # the number of GPUs per node you request
world_size=8   # the total number of GPUs you will need
mode='train'

for i in {0..0}; do # change it to {0..1} will execute for i=0 and i=1

# prepare the script.slurm for launching the job
echo "#!/bin/bash" > script.slurm
echo "#SBATCH --job-name=slurm_${i}" >> script.slurm   # the name of your job
echo "#SBATCH --mail-user=yz681@leicester.ac.uk" >> script.slurm
echo "#SBATCH --mail-type=ALL" >> script.slurm
echo "#SBATCH --output=ic_${i}.err" >> script.slurm    # a file for recording the print out of your experiment
echo "#SBATCH --nodes=${nodes} " >> script.slurm       # request n nodes
echo "#SBATCH --ntasks-per-node=1" >> script.slurm     # total number of times running main.py
echo "#SBATCH --cpus-per-task=42" >> script.slurm      # each GPU contain 128 cpus (workers), each GPU is a task.
echo "#SBATCH --mem-per-cpu=3850" >> script.slurm      # required memory per cpu
echo "#SBATCH --gres=gpu:ampere_a100:${gpus}" >> script.slurm # maximum 3 GPUs per node.
echo "#SBATCH --partition=gpu" >> script.slurm
echo "#SBATCH --time=48:00:00" >> script.slurm         # maximum 48 hours of consecutive running
echo "#SBATCH --account=su004" >> script.slurm         # budget account of leicester university

echo "module load GCCcore/11.3.0" >> script.slurm
echo "module load Python/3.10.4" >> script.slurm
echo "source /gpfs/home/y/yz681/code/py3_10_4/bin/activate" >> script.slurm
echo "python --version" >> script.slurm
echo "cd /gpfs/home/y/yz681/code/ic/" >> script.slurm

# get a free port for running distributed training
echo "port=\$(expr 10000 + \$(echo -n \$SLURM_JOBID | tail -c 4))" >> script.slurm

# get the ip addres for running distributed training
echo "ip1=\`hostname -I | awk '{print \$1}'\`" >> script.slurm
echo "echo \$ip1" >> script.slurm

# srun will run main.py in each node independently, each is associated with a unique number os.environ['SLURM_PROCID'],
# which can be read in python, used as node rank.
echo "srun python main.py --cfg config/cifar/Res32_cifar10_1.yaml --nodes ${nodes} --gpus ${gpus} --world_size ${world_size} --ip \$ip1 --port \$port --wks 12 --mode ${mode}" >> script.slurm

cat script.slurm    # print out script.slurm
sbatch script.slurm # launch the job
rm script.slurm     # remove script.slurm

done
```
