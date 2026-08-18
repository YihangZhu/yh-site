# Free GPU resources

## [Google Colab](https://colab.research.google.com/)

Each run can use a maximum of one GPU, which is usually an
[Nvidia T4](https://research.google.com/colaboratory/faq.html). The time limit
for consecutive usage is 12 hours. The availability of the GPU resource is not
guaranteed. The details about how to use Google Colab are available
[here](train-on-colab.md).

The University of Leicester student/staff can use two HPCs for free: Alice and
Sulis.

## [Alice](https://alice-docs.le.ac.uk/)

It has six GPU nodes. Each has 128GB RAM, 28 CPU cores and 2 x Nvidia Tesla
P100 GPU cards.

According to
[here](https://uniofleicester.sharepoint.com/sites/Research-Computing/SitePages/request-access-alice.aspx),
access to Alice needs to be applied. Access to Alice is organized in terms of
projects and you need to join a project in order to have access. (1) Find out
the project you can join by asking your colleagues or supervisor. (2) Ask your
supervisor to send the [IT desk](https://remote.le.ac.uk/help/) an email to ask
them to grant you access.

Documentation of Alice, e.g., file system and hardware architecture, is
available [here](https://alice-docs.le.ac.uk/Getting_Started/login/).

## [Sulis](https://sulis-hpc.github.io/techspecs/)

It has 30 GPU nodes. Each node has 3 NVIDIA A100 40 GB RAM passively-cooled
GPUs; 2 x AMD EPYC 7742 (Rome) 2.25 GHz 64-core processors per node.

Access to Sulis can be applied by following the instruction
[here](https://sulis-hpc.github.io/gettingstarted/), which also provide
documentation of Sulis, e.g., file system and hardware Specifications. When
applying the account for Sulis, an ssh key is required, which can be generated
via the Terminal (for Linux or MacOS users) or Command Prompt (for Windows
users). [Section ssh-related](train-on-the-hpcs/ssh-related.md) also provides
some details on this topic. username of your account should be your university
username, e.g., ab123. Do not use putty the first time log in, it will skip the
QR code and you cannot scan it.

The details about how to use the HPCs for training ML models are available
[here](train-on-the-hpcs/index.md).

The available resources in Sulis can be found
[here](https://safe.epcc.ed.ac.uk/Project).
