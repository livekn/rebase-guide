# Rebase guide

Checkout 到不同的 branch 來玩玩吧。

## 在中間插入 commit

有時候，我們會希望在 commits 之間插入新的 commit，這時我們可以用 rebase 來處理。

接下來，就試試在 `commit1` 和 `commit3` 中間，插入一個 commit 吧。

1. `git rebase -i main`
2. 把 commit1 前面的 pick 改成 `e` 或者 `edit` ，並儲存結束
3. 新增一個檔案，並把 commit 加進來 `touch file2 && git add file2 && git commit -m 'commit2'`
4. `git rebase --continue` 直到結束

現在用 `git log` 相信就能看到在 `commit1` 和 `commit3` 中間，多了一個 `commit2` 了。

### Tips

你並不一定要用別的 branch 才能 rebase 的，你也可以用 `git log` 找出更前面的 commit id ，並以它為底來 rebase 。
