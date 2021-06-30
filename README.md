# Rebase guide

Checkout 到不同的 branch 來玩玩吧。

## 在中間刪除 commit

有時候，我們會希望把 commit 刪除，這時我們可以用 rebase 來處理。

接下來，就試試在 `commit1` 和 `commit2` 中間，把錯誤的 commit `remove this commit` 刪除吧。

1. `git rebase -i main`
2. 把 `remove this commit` 前面的 pick 改成 `d` 或者 `drop` ，然後儲存結束

現在用 `git log` 相信就能看到在 `commit1` 後面就是 `commit2` 中間，多餘的 `remove this commit` 不見了。

### Tips

你並不一定要用別的 branch 才能 rebase 的，你也可以用 `git log` 找出更前面的 commit id ，並以它為底來 rebase 。
