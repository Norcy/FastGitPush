# FastGitPush
一键提交 Git 脚本

在每次提交代码时都要输入以下命令，而且 commit message 还需要加双引号，非常麻烦


```sh
git add --all
git commit -m "这是需要加双引号的 message"
git pull --rebase
git push
```


虽然有 `gaa`、`gcm`、`gp` 等 alias 提高单行命令的效率，但是用起来依然麻烦

Now，你只要使用该方法，就可以一键提交，且不需要为 commit message 添加双引号

```sh
ppp 这是 支持 空格的 message
```


## 安装
以 oh-my-zsh 为例，其他终端同理

编辑 `~/.zshcr`，添加以下 alias，然后执行 `source ~/.zshrc`

```sh
alias ppp='_f(){
git add --all && 
who=`whoami`
commitMessage="Auto Commit [by ${who}]"
if [ $# -gt 0 ] ; then
	commitMessage=$*" [by ${who}]"
fi
git commit -m "$commitMessage" && git pull --rebase && git push}; _f'
```


