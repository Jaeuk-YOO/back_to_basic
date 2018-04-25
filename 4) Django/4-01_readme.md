4.01 장고와 관련하여 (18-04-16)
==

[장고걸스 튜토리얼 - Django installation](https://tutorial.djangogirls.org/ko/django_installation/)
--

### virtualenv와 관련하여
> The venv module provides support for creating lightweight “virtual environments” with their own site directories, optionally isolated from system site directories. Each virtual environment has its own Python binary (allowing creation of environments with various Python versions) and can have its own independent set of installed Python packages in its site directories.  

> 해석하자면, venv모듈은 나의 디렉토리에 lightweight한 가상환경을 제공합니다! 옵셔널하게 이것은 시스템 디렉토리와도 분리될 수 있습니다. 개별의 가상환경은 그것만의 파이썬 바이너리를 갖게되고, 파이썬 패키지를 독립적으로 설치되도록 합니다.  
**정리하자면, virtualenv는 나의 디렉토리마다 가상환경을 제공하기 때문에 나의 디렉토리가 즉 독립된 프로젝트처럼 돌아갈 수 있도록 합니다.**

- Q. 왜 장고 프로젝트는 virtualenv를 활용할까.
- A. 독립적인 가상의 파이썬 실행환경을 제공한다. 쉽게 말하면 프로젝트별로 패키지 설치가 가능하다는 이점이 있다.  
[참고자료 1 독립적인 가상의 파이썬 실행환경, virtualenv](http://ulismoon.tistory.com/2)  
[참고자료 2 venv 모듈에 대하여 - python docs](https://docs.python.org/3.5/library/venv.html)

### studies for virtualenv
- 가상환경의 활성화/비활성화
    ```
    가상환경이름/bin/activate :: deactivate
    ``` 
    주의 : 한번 활성화된 가상환경은 수동으로 비활성화하기 전까지 유지된다. 다른 프로젝트로 가기 전에 꼭 비활성화해 환경이 꼬이지 않도록 하자.

- virtualenv를 활용하기 위해서는 pip package install이 필요하다. 그렇다면 pip는 무엇일까!  

    - pip : 파이썬으로 작성된 패키지 소프트웨어를 설치, 관리하는 패키지 관리 시스템  

    - how to install pip? : pip는 자동으로 장고를 인스톨 할때 기본적으로 인스톨이 되어있다. 파이썬 2.7.9 이후 버전과 파이썬 3.4 이후 버전은 기본적으로 포함된다.  
        ```bash
        $ pip install pkgname 
        $ pip uninstall pkgname
        ```
- virtualenv 설치하기  

    1. 가상 환경을 만들어보자.
    ```bash
    $ python3 -m venv 내 가상환경 이름
    $ python3 -m venv myvenv
    ```
    2. 가상환경을 만들었을 때 오류사항이 있으면 아래의 에러가 나타날 수도 있다.  
    ***나는 설치과정에서 해당 에러가 났음.***  
  
    ```bash
    The virtual environment was not created successfully because ensurepip is not available.  On Debian/Ubuntu systems, you need to install the python3-venv package using the following command.
        apt install python3-venv
    You may need to use sudo with that command. After installing the python3-venv package, recreate your virtual environment.
    
    # 쉽게 말하면 virtual environment가 ensurepip가 사용되지 않았기에 제대로 설치되지 않은 것.
    ```
    - ensurepip와 관련해서 bootstraping(self-start process) https://docs.python.org/3.5/library/ensurepip.html  
    > The ensurepip package provides support for bootstrapping the pip installer into an existing Python installation or virtual environment. This bootstrapping approach reflects the fact that pip is an independent project with its own release cycle, and the latest available stable version is bundled with maintenance and feature releases of the CPython reference interpreter.  

    3. 하라는 대로 설치를 해주자.
    ```bash
    $ sudo apt install python3-venv
    ```
    4. 가상환경을 초기화 할때 문제가 생길 수 있다.
    ```
    Error: Command '['/home/eddie/Slask/tmp/venv/bin/python3', '-Im', 'ensurepip', '--upgrade', '--default-pip']' returned non-zero exit status 1
    ```
    5. 에러가 났을 때 
    ```bash
    $ sudo apt install python-virtualenv
    ```
    6. virtualenv 환경은 아래의 명령어로 작동한다.
    ```bash
    $ virtualenv --python=파이썬버전 가상환경이름
    $ virtualenv --python=python3.6 myvenv
    ```
    7. 내가 만든 가상환경에 접근하자.
    ```bash
    $ source myvenv/bin/activate #venv환경을 activating합니다.
    ```
    8. activate가 되면 앞에 (내 가상환경 이름)이 붙습니다!
    ```bash
    (myvenv) $
    ```