# 나만의 개발 환경 

내가 사용하는 개발 도구를 정리해보자. 

추후에 스크립트로 작성해보자. :)

## Homebrew

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```



### Iterm2

```
brew cask install iterm2
```

### Tree

```
brew install tree
```





### Typora



### Git

```
brew install git git-lfs

git config --global user.name "Your Name"
git config --global user.email "you@your-domain.com"
git config --global core.precomposeunicode true
git config --global core.quotepath false
```

터미널 설정 

Open ~/.bash_profile

```
c_cyan=`tput setaf 6` 
c_red=`tput setaf 1` 
c_green=`tput setaf 2` 
c_sgr0=`tput sgr0`

parse_git_branch ()
{
   if git rev-parse --git-dir >/dev/null 2>&1
   then
      gitver=$(git branch 2>/dev/null| sed -n '/^\*/s/^\* //p')
   else
      return 0
   fi
   echo -e $gitver
}

branch_color ()
{
   if git rev-parse --git-dir >/dev/null 2>&1
   then
      color=""
      if git diff --quiet 2>/dev/null >&2
      then
         color="${c_green}"
      else
         color=${c_red}
      fi
   else
      return 0
   fi
   echo -ne $color
}

export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\](\[$(branch_color)\]$(parse_git_branch)\[${c_sgr0}\])\$ '
```

별칭 설정 

```g
[alias]
    co = checkout
    rb = rebase -i
    st = status
    cm = commit
    pl = pull
    ps = push
    lg = log --graph --abbrev-commit --decorate --format=format:'%C(cyan)%h%C(reset) - %C(green)(%ar)%C(reset) %C(white)%s%C(reset) %C(dim white)- %an%C(reset)%C(yellow)%d%C(reset)' --all
    ad = add
    tg = tag -n
    df = diff
    br = branch
    alias = "!git config --list | egrep '^alias.+'"
```
아이디, 비밀번호 캐싱 (ex 10일)

```
git config --global credential.helper 'cache --timeout=864000'
```



### Sublime

```
brew cask install sublime-text
```

### Chrome

```
brew cask install google-chrome
```

### SourceTree

```
brew cask install sourcetree
```

### Sequel-pro

### Java

```
brew tap AdoptOpenJDK/openjdk
brew cask install <version>
```
- OpenJDK8 with Hotspot JVM version : adoptopenjdk8
- OpenJDK11 with Hotspot JVM version : adoptopenjdk11


https://github.com/AdoptOpenJDK/homebrew-openjdk


### Intellij

<https://github.com/google/styleguide>

```
keymap -> Find in Path 설정
```

- plugins 
  - Lombok 
  - CheckStyle-IDEA
  - Key Promoter X
  - SonarLint
  - .ignore 
  - String Manipulation
- QueryDSL 주의사항
  - Enable Annotation processing 
  - generated 소스 코드 추가 (Add Content Root)


### Docker

```
brew cask install docker
```

### Kubernetes

```
brew cask install kubernetes-cli
```


### nodejs

```
 brew cask install node
```

