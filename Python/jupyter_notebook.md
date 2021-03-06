# Jupyter Notebook

## 0. 간단 소개

파이썬을 실행할 때 가장 처음 보게 되는 것이 Python REPL(Read-eval-print loop)이다. 터미널에서 python 혹은 python3 라고 입력하면 나오는 파이썬 커널이다. 가볍기도 하고 시커먼 화면이 멋있기도 해서 간단한 코드(주로 타입 확인, 함수 매개변수 테스트)를 써볼 때 쓴다.

Python REPL의 확장 버전이 IPython Notebook이다. repl에선 여러 줄의 코드를 실행하기가 어렵다. 할 수는 있지만 여러 줄의 함수를 선언할 때 한 글자라도 틀리면 다시 처음부터 해야한다. 그래서 여러 줄 단위 실행 및 결과 확인, 편집 유용성 등의 기능이 추가되어 만들어진 것이 IPython Notebook이다. 실행 모습을 보면 감이 바로 팍 올 것이다. 물론 Python 스크립트 파일을 만들어서 커널로 실행하든, 서브라임 텍스트로 빌드해도 된다. 하지만 어떤 문법 공부 혹은 데이터를 다양하게 다루며 테스트를 할 때 굉장히 많은 코드 cell들이 생기게 된다. 1-10라인은 A 테스트, 11-20라인은 B 테스트 등으로 말이다. 이 때 일반 에디터로 작업하면 매 번 다른 코드들은 주석처리를 해서 실행하거나 cell 단위로 여러 파일을 생성해서 각각 실행해야 한다. 솔직히 귀찮다. 한 파일 내에서 쉽게 코드 cell 단위로 실행할 수 있다는 점이 최고 장점이다.

다만 IPython Notebook은 파이썬 전용이다. 그리고 한 번 실행하고 Python 버전을 바꾸려면 로컬 서버를 내렸다가 다시 올려야한다. 이런 문제를 해결한 것이 Jupyter Notebook이다. Jupyter는 쉽게 실행 커널을 바꿀 수 있다. 서버가 돌아가는 상황에서 파이썬의 버전을 바꿀 수도 있고, 아예 다른 언어로도 바꿀 수 있다.(다른 언어 커널 추가하는 것은 [nacyot](http://blog.nacyot.com/articles/2015-05-08-jupyter-multiple-pythons/)님 블로그에 자세한 설명이 있다.) 그래서 현재는 만약 IPython을 실행한다면 곧 없어질거라며 Jupyter를 쓰라는 메시지를 보게 될 것이다.

## 1. 설치

```sh
pip install jupyter
```

끝.

## 2. 실행

terminal에서 `jupyter notebook`이라고 치면 기본 브라우저에서 notebook 창이 새로 뜬다. 오른쪽 위에 new 누르고 Python3 notebook 선택하면 새로운 파일이 열린다. 확장자는 ipynb다.

## 3. 단축키

h를 누르면 키 도움 팝업이 뜬다. command 모드, edit 모드 별로 대표적인 것 몇 개만 정리한다. 다른 magic 명령어 등을 알아보려면 다음 [슬라이드](http://www.slideshare.net/TaeYoungLee1/20150306-ipython) 참고.

- command mode
    + `enter` : edit mode로 바꿈. 선택된 cell로.
    + `a`, `b` : 순서대로 위, 아래에 cell 추가
    + `y`, `m`, `r`: 순서대로 cell 모드를 code, markdown, raw로 바꾸기
    + `1`, `2`, `3`, `4`, `5`, `6` : 선택된 셀을 마크다운으로 바꿔서 heading을 적용한다.
    + `j`, `k` : 셀 이동. 아래, 위. vim 키랑 똑같다. shift 누른 후에 키를 누르면 여러 개 선택된다.
    + `x`, `c`, `shift+v`, `v` : cut, copy, 위에 붙여넣기, 아래에 붙여넣기
    + `dd`: 선택된 cell 삭제. 역시 vim 느낌
    + `z`: 삭제 취소
    + `shift+M` : 선택된 cell 합병. 하나만 선택되면 바로 아래꺼랑 합병
    + `L` : 라인 넘버 생기게 하기
    + `shift+spacebar`, `spacebar` : 스크롤 업, 다운
- edit mode
    + `ESC`: command 모드로 바꿈.
    + `enter`: 한 뭉치에서 줄 바꿈이다. 에디터에서 편집하는 것처럼 하면 된다.
    + `shift+enter` or `ctrl+enter`: 한 뭉치 실행
    + `ctrl + shift + -` : 커서 위치 아래 부분을 split한다.

## 4. Magic commands

- 노트북 자체를 관리할 수 있는 명령어들. `%` or `%%` 기호를 앞에 쓰면 된다.
- `timeit`
    + `%timeit my_func(10)` : 해당 함수를 실행하는 시간과 loop 등을 쉽게 알려준다.
    + `%%timeit` : 셀 전체의 실행시간을 알고싶으면 셀 맨 위에 이렇게 써주면 된다.
- `%matplotlib inline`
    + 디폴트는 matplotlib이 그리는 이미지가 독립된 윈도우에 위치한다.
    + 하지만 위처럼 특정 backend를 선택하도록 지정해주면 이미지를 렌더하는 소프트웨어를 선택할 수 있다.
    + 위 예제는 노트북이 바로 이미지를 렌더하는 예다.
- 레티나 고화질 모니터를 쓴다면 맨 위에 아래처럼 쓰면 선명한 이미지를 얻을 수 있다

    ```
    %matplotlib inline
    %config InlineBackend.figure_format = 'retina'
    ```

- `%pdb` : 디버거 사용할 수 있다. 자세한 내용은 https://youtu.be/bZZTeKPRSLQ

## 5. Export

`.ipynb` 파일 자체가 거대한 json 파일이다. 그래서 지정하는대로 쉽게 다른 포맷으로 변경할 수 있는데 다음 명령어로 할 수 있다. 더 자세한 내용은 다음 [링크](https://nbconvert.readthedocs.io/en/latest/usage.html)에서 확인한다.

```sh
jupyter nbconvert --to html notebook.ipynb
jupyter nbconvert --to pdf notebook.ipynb
```

## 6. Slideshow

- 만든 노트북을 쉽게 슬라이드로 만들 수 있다.
- 메뉴 -> View -> Cell Toolbar -> Slideshow
- 셀에 원하는 속성을 넣어주면 된다.
    + Slides : 메인 슬라이드 의미. 왼쪽, 오른쪽으로 넘어가는 메인 플로우.
    + Sub-slides : 메인 슬라이드의 하위내용. 위 아래 커서로 이동 가능
    + Fragments : 처음엔 숨겨지지만 버튼을 누르면 등장한다.
    + Skip : 넘기는 셀
    + Notes : speaker notes로 만들 수 있음
- 슬라이드 파일로 만들기: `jupyter nbconvert notebook.ipynb --to slides`
- 브라우저에 띄우기: `jupyter nbconvert notebook.ipynb --to slides --post serve`

## 7. Jupyter Server

서버에서 jupyter notebook server를 실행하는 방법

- 키 파일을 만든다.

    ```sh
    mkdir ~/.ssl
    cd ~/.ssl
    sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout "cert.key" -out "cert.pem" -batch
    ```

- 주피터 서버 비밀번호를 만든다. `ipython` 실행해서 다음 코드로 비밀번호를 생성하고, sha로 시작하는 해싱 코드를 복사해둔다.

    ```py
    from IPython.lib import passwd
    passwd()
    # type your password
    exit
    ```

- jupyter config
    + 파일 생성: `jupyter notebook --generate-config`
    + 파일 편집해서 아래 내용 추가: `vi ~/.jupyter/jupyter_notebook_config.py`

    ```py
    c = get_config()
    c.NotebookApp.certfile = u'/home/ubuntu/.ssl/cert.pem'
    c.NotebookApp.keyfile = u'/home/ubuntu/.ssl/cert.key'
    c.IPKernelApp.pylab = 'inline'
    c.NotebookApp.ip = '*'
    c.NotebookApp.open_browser = False
    c.NotebookApp.password = 'sha1:fc216:3a35a98ed980b9...'
    c.NotebookApp.port = 8888
    ```

- tmux로 세션 연 다음에 주피터 노트북 서버를 실행한다.
    + `nohup jupyter notebook`
    + nohup은 verbose를 출력하지 않고 파일로 기록해주는 역할을 한다.
- ip와 port를 그대로 치지말고 꼭 `https`를 맨 앞에 붙여준다. 크롬은 ip 주소를 그대로 치면 http로 접속하기 때문에 ssl error가 날 수 있다.
