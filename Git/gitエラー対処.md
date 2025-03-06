# gitエラー対処
## HTTPリクエストのバッファサイズに制限
```
Enumerating objects: 11, done.
Counting objects: 100% (11/11), done.
Delta compression using up to 8 threads
Compressing objects: 100% (7/7), done.
error: RPC failed; HTTP 400 curl 22 The requested URL returned error: 400
send-pack: unexpected disconnect while reading sideband packet
Writing objects: 100% (7/7), 1.37 MiB | 2.50 MiB/s, done.
Total 7 (delta 1), reused 0 (delta 0), pack-reused 0
fatal: the remote end hung up unexpectedly
Everything up-to-date
```
- バッファサイズ500MBに変更する
```zsh
git config --global http.postBuffer 524288000
```