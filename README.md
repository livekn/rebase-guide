# Rebase guide

Checkout 到不同的 branch 來玩玩吧。

## 在中間修改 commit 內容

有時候，我們會希望修改指定的 commit，這時我們可以用 rebase 來處理。

在 `commit1` 和 `commit3` 中間，有一個錯誤的 `commit02` ，我們就試試修正成 `commit2` 吧。

1. `git rebase -i main`
2. 把 commit02 前面的 pick 改成 `e` 或者 `edit` ，並儲存結束
3. 把 file02 改名成 file2 `mv file02 file2`
4. 把修正寫進原本的 commit 中 `git add . && git commit --amend`
5. 這時候你可以再輸入 commit message，把錯誤的 commit02 改成 `commit2` 吧
6. 完成修改後， `git rebase --continue` 直到結束

現在用 `git log` 相信就能看到在 `commit1` 和 `commit3` 中間，是正確的 `commit2` 了。

### Tips

你並不一定要用別的 branch 才能 rebase 的，你也可以用 `git log` 找出更前面的 commit id ，並以它為底來 rebase 。
