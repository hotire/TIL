# 나만의 개발 환경 

내가 사용하는 개발 도구를 정리해보자. 

추후에 스크립트로 작성해보자. :)

## Homebrew

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

- m1 zsh: command not found: brew 
vi ~/.zshrc 에 
~~~
eval $(/opt/homebrew/bin/brew shellenv)
~~~


### Iterm2

```
brew install --cask iterm2
```

### Tree

```
brew install tree
```

### ZSH

```
brew install ZSH
```

### Informative git prompt for zsh
https://github.com/olivierverdier/zsh-git-prompt

다운받아서, ~/.zshrc에 

```
source path/to/zshrc.sh // zshrc.sh 가 있는 경로 
# an example prompt
PROMPT='%B%m%~%b$(git_super_status) %# '
```
입력한다. 

### Typora

- https://typora.kr.uptodown.com/mac/versions


### Git

```
brew install git git-lfs

git config --global user.name "Your Name"
git config --global user.email "you@your-domain.com"
git config --global core.precomposeunicode true
git config --global core.quotepath false
```

별칭 설정 
~/.gitconfig 

```
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
brew install --cask sublime-text
```

### Chrome

```
brew install --cask google-chrome
```

### SourceTree

```
brew install --cask sourcetree
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

+ Chained method calls - Align when multiline check!

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
brew install --cask docker
```

### Kubernetes

```
brew install --cask kubernetes-cli
```


### nodejs

```
 brew install --cask node
```

### Redis

```shell
brew install redis
```

redis 설치

```
redis-cli shutdown
```

redis 셧다운
