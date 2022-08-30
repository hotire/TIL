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

~~~
brew install python
~~~

python 설치 후 ~/.zshrc에 

~~~
alias python=/usr/local/bin/python3.9 // python 
~~~

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

### Typora

- https://typora.kr.uptodown.com/mac/versions
- https://typora.kr.uptodown.com/mac/download/3642551

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
brew install --cask <version>
```
- OpenJDK8 with Hotspot JVM version : adoptopenjdk8
- OpenJDK11 with Hotspot JVM version : adoptopenjdk11


https://github.com/AdoptOpenJDK/homebrew-openjdk

### Javahome

~~~
javahome_usage() {
echo "javahome - switch to different JDK version"
echo "Usage: javahome [-h] [-v VERSION]"
echo echo " -h : display usage"
echo " -v : specific JDK version to switch"
echo
echo "Examples: "
echo "># javahome -v 1.8 : switches to JDK8"
echo "># javahome -v 12 : switches to JDK12"
echo "># javahome : display all installed JDK and display current JDK"
}

javahome () {
if [ "$1" = "-h" ] ; then
	javahome_usage
fi
if [ "$#" -eq 0 ] ; then
	/usr/libexec/java_home -V
fi
if [ "$#" -eq 2 ] && [ "$1" = "-v" ] ; then
export JAVA_HOME=`/usr/libexec/java_home $@`
echo "Setting JAVA_HOME:" $JAVA_HOME
echo "Added JAVA_HOME/bin to PATH" PATH=$PATH:$JAVA_HOME/bin
echo $PATH

echo
        java -version
fi

}
~~~
### Memory Analyzer

- https://www.eclipse.org/mat/previousReleases.php

1.12.0 version 다운

동작하지 않을 경우 Contents/Info.plist 에서 <array></array> 사이에 

<string>-vm</string><string>/Library/Java/JavaVirtualMachines/jdk-11.jdk/Contents/Home/bin/java</string>

추가 

### visualVM

- https://visualvm.github.io/download.html

- heapSize 변경 etc/visualvm.conf 에서 default_options에 -J-Xms24m -J-Xmx256m을 원하는 값으로 수정하면 된다.


- 손상되었기 때문에 열 수 없습니다. 해당 항목을 휴지통으로 이동해야 합니다. 에러 인 경우 Xattr -cr '앱 경로' (xattr -cr /Applications/VisualVM.app)



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
 brew install node
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

