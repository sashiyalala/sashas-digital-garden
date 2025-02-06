---
{"dg-publish":true,"permalink":"/☆⋆｡𖦹°‧★🛸42/⋆˖⁺‧₊☽◯☾₊‧⁺˖⋆meta/workflow/🐈‍⬛🐙 multiple remotes @ 42/","tags":["42madrid","meta","git"]}
---



the generic form of a 42 repository is kinda like this:
```sh
git@vogsphere-v2.42madrid.com:vogsphere/intra-uuid-37017c37-f279-43c5-86b7-f629581e8a9b-6259240-facosta
```

I've renamed [[☆⋆｡𖦹°‧★🛸42/⋆˖⁺‧₊☽◯☾₊‧⁺˖⋆meta/workflow/🐈‍⬛🐙🚀 my git remotes @ 42\|🐈‍⬛🐙🚀 my git remotes @ 42]]
so to clone a 42 repo, use this URL instead:
```sh
git@git.42:vogsphere/intra-uuid-37017c37-f279-43c5-86b7-f629581e8a9b-6259240-facosta
```

work on your github repo as usual
>[!danger] make sure the default branch on github is called `master` and not main
> `master` is the name of the default branch @ 42
> basically, avoid any possible issues with different names

when you're ready to upload to the **42 repo**, clone it with the upper address⬆
then, in the **42 repo** you'll just see that remote:
```sh
➜  ft_printf_wip git:(master) git remote -v
origin  git@git.42:vogsphere/intra-uuid-37017c37-f279-43c5-86b7-f629581e8a9b-6259240-facosta (fetch)
origin  git@git.42:vogsphere/intra-uuid-37017c37-f279-43c5-86b7-f629581e8a9b-6259240-facosta (push)
```

add the github remote, I like to call it `shorigin`
```sh
➜  ft_printf_wip git:(master) git remote add shorigin git@github.com:sashiyalala/n-remotes-42.git
```

now you have both remotes available:
```sh
➜  ft_printf_wip git:(master) git remote -v
origin  git@git.42:vogsphere/intra-uuid-37017c37-f279-43c5-86b7-f629581e8a9b-6259240-facosta (fetch)
origin  git@git.42:vogsphere/intra-uuid-37017c37-f279-43c5-86b7-f629581e8a9b-6259240-facosta (push)
shorigin        git@github.com:sashiyalala/ft_printf.git (fetch)
shorigin        git@github.com:sashiyalala/ft_printf.git (push)
```

# first upload
you'll see nothing in the repo, so you need to do these steps
1. *fetch* from the **github** remote 
```sh
git fetch shorigin
```
2. *pull* from the **github** remote's branch `master`
```sh
git pull shorigin master
```
3. *push* the pulled commits from **github**->**42**
```sh
git push origin master
```

Now, if you clone the 42 repo again, you should be able to see the same you see in github
