# Free GPU resources

## [Google Colab](https://colab.research.google.com/)

Each run can use a maximum of one GPU, which is usually an
[NVIDIA T4](https://research.google.com/colaboratory/faq.html). The time limit
for consecutive usage is 12 hours. The availability of the GPU resource is not
guaranteed. Details on how to use Google Colab are available
[here](train-on-colab.md).

University of Leicester students/staff can use two HPCs for free: Alice and
Sulis.

## [Alice](https://alice-docs.le.ac.uk/)

It has six GPU nodes. Each has 128GB RAM, 28 CPU cores and 2 x NVIDIA Tesla
P100 GPU cards.

Access to Alice must be applied for, as described
[here](https://uniofleicester.sharepoint.com/sites/Research-Computing/SitePages/request-access-alice.aspx).
Access is organised in terms of projects, and you need to join a project to
get access: (1) find out which project you can join by asking your colleagues
or supervisor, then (2) ask your supervisor to email the
[IT desk](https://remote.le.ac.uk/help/) requesting access on your behalf.

Documentation for Alice, e.g., its file system and hardware architecture, is
available [here](https://alice-docs.le.ac.uk/Getting_Started/login/).

## [Sulis](https://sulis-hpc.github.io/techspecs/)

It has 30 GPU nodes. Each node has 3 NVIDIA A100 40GB GPUs (passively cooled)
and 2 x AMD EPYC 7742 (Rome) 2.25GHz 64-core processors.

Access to Sulis can be applied for by following the instructions
[here](https://sulis-hpc.github.io/gettingstarted/), which also cover Sulis's
documentation, e.g., file system and hardware specifications. When applying
for a Sulis account, an SSH key is required, which can be generated via the
Terminal (Linux/macOS) or Command Prompt (Windows). The
[SSH page](train-on-the-hpcs/ssh-related.md) also covers this. The username
for your account should be your university username, e.g., ab123. Do not use
PuTTY the first time you log in — it will skip the QR code, and you won't be
able to scan it.

Details on how to use the HPCs for training ML models are available
[here](train-on-the-hpcs/index.md).

The available resources on Sulis can be found
[here](https://safe.epcc.ed.ac.uk/Project).
