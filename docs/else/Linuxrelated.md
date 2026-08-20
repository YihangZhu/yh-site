---
noindex: true
search:
  exclude: true
---

# Linux-related

## Unpack files

```bash
tar -xvzf iNaturalist2018/train_val2018.tar.gz -C /datasets/inaturalist2018/
```

- Flag `-z` only for files with a name ending with `.gz`.
- Flag `-C` for specifying the destination folder.

```bash
unzip imagenet/imagenet-object-localization-challenge.zip -d /datasets/imagenet/
```

- Flag `-d` is for specifying the destination folder.

## Editing a file in the terminal

`vi file`, click `i` for modifying the file. After editing, press `esc` and input `:wq` to save and exit.

SSH-related for interacting with a remote server, e.g., data transfer via `scp`, login, is detailed [here](../ml-training-tutorial/train-on-the-hpcs/ssh-related.md).

## References

- **Basic Linux commands**: <https://kinsta.com/blog/linux-commands/>, <https://www.hostinger.co.uk/tutorials/linux-commands>
- **X11 forward on macOS**: <https://docs.cse.lehigh.edu/xforwarding/xforwarding-mac/>

[Back to Else](index.md)
