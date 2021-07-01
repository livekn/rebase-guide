# Rebase guide

Checkout 到不同的 branch 來玩玩吧。

## 調整 commit 順序

有時候，我們會希望調整 commit 順序，這時我們可以用 rebase 來處理。

在這個 branch 中， commit 是 `commit1` -> `commit3` -> `commit2` ，我們就試試改正成 `commit1` -> `commit2` -> `commit3` 吧。

1. `git rebase -i main`
2. 把 commit2 的那行搬到 commit3 前，在 vi 中，可以我以先移到 `commit2` 那行，輸入 `dd` 把它刪除，再到 `commit3` 那行，輸入 `P` （大寫），把刪除的那行貼到上面，並儲存結束

現在用 `git log` 相信就能看到順序是正確的 `commit1` -> `commit2` -> `commit3` 了。

### Tips

你並不一定要用別的 branch 才能 rebase 的，你也可以用 `git log` 找出更前面的 commit id ，並以它為底來 rebase 。
