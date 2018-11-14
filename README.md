# smi2srt
smi 자막을 srt로 변환해주는 파이썬 프로그램 (EMBY 라이브러리 자막 관리용으로 적합).
[PySAMI](https://github.com/g6123/PySAMI)
의 smi parser를 가져옴 이 부분의 라이센스는 유지됨.
파이썬의 cchardet 모듈을 이용해 자막 인코딩 자동 탐지.

## 요구사항:
- Python 2/3 (2.7~/3.6~)
- cchardet

## 설치:
- cchardet 설치:
~~~bash
pip install cchardet
~~~
- smi2srt 설치:
1. smi2srt 파일의 경로를 $PATH environment에 추가. 혹은 /usr/local/bin에 파일 복사

## 사용법:
~~~bash
smi2srt -l <TARGET_LANGUAGE> <MOVIE_LIBRARY_DIR>
~~~

- <TARGET_LANGUAGE> (default = kr) : smi 파일로부터 어느 언어를 불러올지를 지정합니다. 기본 값은 kr(한국어)입니다.
- <MOVIE_LIBRARY_DIR> : 영화 라이브러리 경로입니다. 세부 경로까지 recursive하게 탐색하므로 라이브러리 디렉토리의 최상위 PATH를 입력하시면 됩니다.

프로그램 실행 후 변환이 완료된 자막 파일과 실패한 자막 파일이 출력됩니다.

## 변경사항:

### 2018년 11월 14일
정규표현식에 문제가 있어 tag가 연속으로 사용될 시 자막이 삭제되는 문제 해결
예)
~~~html
<SYNC Start=732><P Class=KRCC><font color="#ff8080">학교에 선전포고를 한<br>세계 제일의 겁쟁이 신데렐라는</font> 
~~~
변환후 
--> 아예내용이 없이 생성됩니다.
 -2cpu 허진녕 님 제보

### 2018년 7월 18일
chardet 대신 속도가 빠른 cchardet으로 인코딩 감지 라이브러리 변경

### 2018년 7월 23일
코드 첫 줄을 #!/usr/bin/env python 로 수정해 설치과정에서 첫 줄 수정을 하지 않아도 되도록 함

### 2018년 8월 10일
'\r' 문자 처리
특정 언어가 특정 시점에 존재하지 않는 경우 예외처리
