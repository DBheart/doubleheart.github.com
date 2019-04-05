# GITHUB page로 블로그 만들기 
> 아 복잡할것 같았는데 그렇게 복잡하지 않네.
>> 저번에 봤을때는 루비로 만들고 몬가를 막했었던거 같은데 너무 복잡하게 생각한거 같다.

# 켈리(테마)적용하기
>켈리 테마를 적용하는 방법은 3가지 정도로 압축되는 듯 하다.
>> 나는 어떻게 했는지 기억이 안난다. 이것저것 껴맞추다보니 어쩌다 되었다.
>> 심화가 아니면 그냥 github 설정에서 테마적용하는 것으로 끝내도록하자. 
>> 켈리사이트에서 루비에서 변환하고 하는데 하지 말것을 추천한다. 
>> 켈리사이트에서도 밑에 github에서는 따로 하는 가이드를 소개하고 있다.
1. [github 설정에서 테마 적용](https://help.github.com/en/articles/adding-a-jekyll-theme-to-your-github-pages-site-with-the-jekyll-theme-chooser)
    - '_config.yml'파일에 theme:테마로 되어있다.
2. 테마 레파지토리를 다운로드 받아서 만들기
    - [깃허브 가이드](https://pages.github.com/)
    - [켈리 repository](https://github.com/topics/jekyll-theme)
3. 켈리사이트에서 소개하는 방법    
    - [켈리 사이트](https://jekyllrb.com/)
    - 깃허브에서 적용할때는 이렇게까지는 필요없는 것 같다.

# github를 블로그로 쓰기
1. 언어는 마크다운 언어를 쓴다.
2. 파일은 md파일을 만든다.
3. 링크는 md를 링크하면 된다. 
    - [제목](url) 
    - 폴더에 있는것을 링크하려면 절대주소나 상대주소를 쓰면된다.
    - ex) [Log_Manage](./study/log_manage.md)
4. 툴은 비주얼코드로 쓰자. git과 연결도 쉽다.
    - 비주얼코드에서 md가 미리보기도 되니까 딱 좋다.
5. 접근방법은 두가지가 있다.
    - 그냥 깃허브에 접근한다.
    - github page주소 : github page로 만든 repository의 설정게 가면 'Your site is published at'이라고 적힌 부분이 있는데 그게 바로 블로그로서 접근할수 있는 url이다.

# 소스 반영
```
1. git add .
> 어차피 내가 수정한 것이므로 모두다 추가 하면된다.
2. git commit -m "메세지"
3. git push origin master
> 처음에는 암호를 넣어야한다.
> 클론 하는 법은 알거라 생각하고 넘어간다.
> git status : 상태 확인하기, 중간중간 살펴보기로 한다.
```

# 비주얼코드 사용한 유지보수
- [비주얼코드로 markdown사용하는 방법](https://blog.aliencube.org/ko/2016/07/06/markdown-in-visual-studio-code/)
- 'markdown extension pack'이라는 익스텐션이 있는데 설치해서 사용하자. markdown에 필요한 플러그인을 통합적으로 설치해주는 것 같다.
  - 와 markdownlint는 쓰지말자. 설치했다가 물결표시가 장난 아니다. 통합팩에서 다지우고 'all in one', 'emoji','pdf'만 남기고 다 언인스톨했다.
- pdf플러그인에 특이하게 uml도 지원한다고 나와있다.
  - 불행히도 안된다. 아래가 지원한다는 코드이다.
  - 마크다운으로는 아니지만 js로 uml을 그리는게 있다.
    - [시퀀스 다어이그램](https://bramp.github.io/js-sequence-diagrams/)
    - [플로우 차트](http://flowchart.js.org/)
    - plant uml : http://plantuml.com/ko/
    - 온라인 plantuml : https://www.planttext.com/

* 아쉬우니까 plant uml에대해서 따로 이야기 해야 할 것 같다.
* 비주얼 코드에 대해서 도 알아보자 : https://gomcine.tistory.com/entry/VS-Code-Extension-%EC%84%A4%EC%B9%98-%EB%B0%8F-%EC%9C%A0%EC%9A%A9%ED%95%9C-Extension-%EC%86%8C%EA%B0%9C


@startuml
Bob -> Alice : hello
Alice ->Bob : ok
@enduml


# 기타
## [마크다운 문법](https://guides.github.com/features/mastering-markdown/)
### [마크다운 문법-한글소개](https://gist.github.com/ihoneymon/652be052a0727ad59601)
### [좀더 디테일한 마크다운 문법소개](https://heropy.blog/2017/09/30/markdown/)
### [GitHub Page생성시 나오는 가이드](./ref/github_page.md)
## uml기능을 갖춘 마크다운 에디터 : [Typora](https://macnews.tistory.com/4799)
### plant uml소개 : http://hochulshin.com/uml-plantuml/

---

마크다운 통합팩에 포함된 것들

1. Markdown All in One - All you need for Markdown (keyboard shortcuts, table of contents, auto preview and more).
2. markdownlint - Markdown/CommonMark linting and style checking for Visual Studio Code.
3. Markdown PDF - This extension convert Markdown file to pdf, html, png or jpeg file.
4. Markdown+Math - Mdmath allows to use Visual Studio Code as a markdown editor capable of typesetting and rendering TeX math. In fact it now reuses the built in markdown viewer. KaTeX works inside as a fast math renderer.
5. Markdown Preview Enhanced - Markdown Preview Enhanced is an extension that provides you with many useful functionalities such as automatic scroll sync, math typesetting, mermaid, PlantUML, pandoc, PDF export, code chunk, presentation writer, etc.
6. Markdown TOC - Generate TOC (table of contents) of headlines from parsed markdown file.
7. VS Live Share - Adds collaborative editing support directly into VS Code, which makes it possible to work on Markdown files with others in real-time!
8. Markdown Table Prettifier - Makes tables more readable for humans. Compatible with the Markdown writer plugin's table formatter feature in Atom.
9. Markdown Emoji - Adds :emoji: syntax support to VS Code's built-in Markdown preview
