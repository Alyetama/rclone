# rclone
Unofficial Python wrapper for Rclone


## Requirements:
- [Python >=3.6](https://www.python.org/downloads/)
- [Rclone](https://rclone.org/downloads/)

## Installation

```
pip install rclone
```

## Example usage

```py
from rclone import rclone

pathname = 'gdrive:/remote/path'  # you can also use a local path

rclone.copy('foo.txt', pathname)
# 100%|███████████████████████████████████████| 0.16/0.16 [00:00<00:00,  1.13MB/s]

rclone.move('bar.bin', pathname)
# 100%|███████████████████████████████████████| 0.16/0.16 [00:00<00:00,  1.34MB/s]

rclone.unit = 'B'
rclone.copy('foo.txt', pathname)
# 100%|███████████████████████████| 159414.0/159414.0 [00:00<00:00, 1003822.00B/s]

rclone.ls(pathname)
# ['foo.bin', 'bar.txt']

rclone.lsjson(pathname)
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

rclone.size('/some/path')
# {'total_objects': 5, 'total_size': 170397}


# You can also use whatever subcommands/flags:
rclone.execute('ls . --exclude *.txt')
#       27 foo.bin
#   159414 foo.csv.zip
#     4808 rclone.py
```
