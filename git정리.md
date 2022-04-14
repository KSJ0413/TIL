# Git & Github 특강 

``` 
Gitbash
```

* date = 시간을 알려줘!
* ls = 여기 뭐 있어?
* touch = 파일 만들기
* mkdir = 폴더 만들기
* cd = change directory
* rm = 지우기

```
code
```

1. git init = 버전 관리 시작

   = 내가 현재 있는 공간을 깃이 관리하는
      마법의 폴더로 만들어줘
   =절대 홈폴더에서 이닛 xxxxxxxxxxx!!

2. git status 
   = 현재 상황을 알려줘
3. git add 파일명
   git add .    = 현재위치 모두 무대로
4. git commit -m "메세지"
5. git log
   git log --oneline

* git remote add origin (주소) 
*  git push origin master







``` 
branch
```

1. git branch  =  __브런치 확인하기__
2. git branch 브런치명  = __브런치 생성하기__
3. git switch 브런치명  = __브런치 바꾸기__
4. git merge 브런치명 = __브런치 합치기__



* Ex) git init  >  touch a.txt  >git add a.txt > git commit -m '왜 이렇게 저장했는지에 대한 메시지' >

``` 
git commit -m '??' : ?안에는 왜 수정했는지에 대한 메시지를 다음사람에게 알려주기 위해 * 
```



​		git switch -c ???  >  git add a.txt  >   git commit -m '???' >  git switch master  >  git add a.txt   >

``` 
		* git switch -c ??? : 바로 git init 한 상태로 새 브런치를 만들고 불러온다*
```



​		git commit -m '???'  > git branch  >  git merge test ; 

``` 
git branch 를 입려하여 현재 생성된 브런치를 볼수있다. * 합치기 전에 확인하자 *
```



``` 
Gitignore :저장소
```



 touch .gitignore }
