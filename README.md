# Rebase guide

Checkout 到不同的 branch 來玩玩吧。

## 分拆 commit

有時候，我們會希望把 commit 一分為二，這時我們可以用 rebase 來處理。

分拆 commit 最少有兩種方法，各有優缺點，以下分別說明。

### 方法一，操作較簡單，但會丟失原 commit 的 metadata

1. `git rebase -i main`
2. 把 split me 前面的 pick 改成 `e` 或者 `edit` ，並儲存結束
3. 把 commit 退到 unstaged 狀態 `git reset HEAD^`
4. 重新把需要的檔案加進 commit ，在這個例子中，我們要把 file2 加到 commit2 中 `git add file2 && git commit -m 'commit2'`
5. 再 file3 包進 commit3 中 `git add file3 && git commit -m 'commit3'`
6. 完成後， `git rebase --continue` 直到結束

現在用 `git log` 相信就能看到在 `commit1` 和 `commit4` 中間的 commit ，被拆成 `commit2` 和 `commit3` 了。

### 方法二，操作較複雜，一不小心會產生 conflict，但可盡量保留原 commit 的 metadata

1. `git rebase -i main`
2. 在要修改 commit 的上一個 commit 那行，把前面的 pick 改成 `e` 或者 `edit` ，在本例子中，是改 commit1 那行，並儲存結束
3. 把要分拆的部分做進一個新的 commit 中，在本例子中，我們要新增 file2 ，並把它加到 commit2 中 `touch file2 && git add file2 && git commit -m 'commit2'`
4. `git rebase --continue`

現在用 `git log` 相信就能看到在 `commit1` 和 `commit4` 中間的 commit ，被拆成 `commit2` 和 `split me` 了。

如果還希望對 `split me` 改名，可以在步驟 1. rebase 的時候，把 `split me` 前面的 pick 改成 `r` 或者 `reword` ，這樣就能在 rebase 過程中改名了。

### Tips

你並不一定要用別的 branch 才能 rebase 的，你也可以用 `git log` 找出更前面的 commit id ，並以它為底來 rebase 。
