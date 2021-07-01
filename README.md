# Rebase guide

Checkout 到不同的 branch 來玩玩吧。

## 合併 commits

有時候，我們會希望把多個 commits 合併成一個 commit，這時我們可以用 rebase 來處理。

接下來，就試試在 `commit1` 和 `commit2` 中間，把 `squash me into commit1` 合併到 `commit1` 吧。

1. `git rebase -i main`
2. 把 squash me into commit1 前面的 pick 改成 `s` 或者 `squash`，並儲存結束
3. 輸入合併後 commit 的 commit message ，在這個例子中，可以把 `squash me into commit1` 這行刪除，並儲存結束

現在用 `git log` 相信就能看到在 `commit1` 後就是 `commit2` ， `squash me into commit1` 被合併到 `commit1` 了。

### Tips

你並不一定要用別的 branch 才能 rebase 的，你也可以用 `git log` 找出更前面的 commit id ，並以它為底來 rebase 。
