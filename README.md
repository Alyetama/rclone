# Rclone for Python

🚀 Python wrapper for rclone.

[![Supported Python versions](https://img.shields.io/badge/Python-%3E=3.6-blue.svg)](https://www.python.org/downloads/) [![PEP8](https://img.shields.io/badge/Code%20style-PEP%208-orange.svg)](https://www.python.org/dev/peps/pep-0008/) 


## Requirements
- 🐍 [Python>=3.6](https://www.python.org/downloads/)


## ⬇️ Installation

```sh
pip install rclone
```


## ⌨️ Usage

```py
from rclone.rclone import Rclone

rc = Rclone()
```


## 📕 Examples


```py
pathname = 'gdrive:/remote/path'  # you can also use a local path


rc.copy('foo.txt', 'remote:/path/to/dst')
# 100%|███████████████████████████████████████| 0.16/0.16 [00:00<00:00,  1.13MB/s]
```

```py
rc.move('bar.bin', 'remote:/path/to/dst')
# 100%|███████████████████████████████████████| 0.16/0.16 [00:00<00:00,  1.34MB/s]
```

```py
rc.unit = 'B'
rc.copy('foo.txt', 'remote:/path/to/dst')
# 100%|███████████████████████████| 159414.0/159414.0 [00:00<00:00, 1003822.00B/s]
```

```py
rclone.ls('remote:/path/to/dir')
# ['foo.bin', 'bar.txt', 'foo/']
```

```py
rclone.lsjson('remote:/path/to/dir')
# [
#     {
#         'Path': 'bar.txt',
#         'Name': 'bar.txt',
#         'Size': 0,
#         'MimeType': 'text/plain; charset=utf-8',
#         'ModTime': '2022-03-22T13:07:53.557168464-04:00',
#         'IsDir': False
#     }
# ]
```

```py
rclone.ls('remote:/path/to/dir', '-R')  # you can supply additional flags to any command as positional argments
# ['foo.bin', 'bar.txt', 'foo/', 'foo/foo1.txt', 'foo/foo2', 'foo/bar/foobar.txt']
```

```py
rclone.size('remote:/path/to/dir')
# {'total_objects': 5, 'total_size': 170397}
```

You can also use whatever subcommands/flags with `execute()`:

```py
# 
rclone.execute('ls "remote:/path/to/dir" --exclude *.txt')
#       27 foo.bin
#   159414 foo.csv.zip
#     4808 rclone.py
```
