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
smi2srt [-r|--remove_original]  <MOVIE_LIBRARY_DIR>
~~~

- <MOVIE_LIBRARY_DIR> : 영화 라이브러리 경로입니다. 세부 경로까지 recursive하게 탐색하므로 라이브러리 디렉토리의 최상위 PATH를 입력하시면 됩니다.
- -r or --remove_original : 변환이 성공한 smi 원본 파일을 삭제합니다.
- -i or --ignore : decoding error를 무시하고 변환 작업을 진행합니다.

프로그램 실행 후 변환이 완료된 자막 파일과 실패한 자막 파일이 출력됩니다.

## 변경사항:

### 2021년 7월 25일
P CLASS 감지하여 smi 파일 내 언어를 자동으로 추출하고, 언어별로 변환된 결과를 저장.
예) aaa.smi -> aaa.kr.srt, aaa.en.srt, aaa.es.srt
따로 language 옵션 지정 안해도 되도록 변경
suffix option 삭제

### 2019년 3월 26일
원본 smi파일을 삭제할 수 있는 옵션 추가

### 2018년 11월 14일
정규표현식에 문제가 있어 tag가 연속으로 사용될 시 자막이 삭제되는 문제 해결
예)
~~~html
<SYNC Start=732><P Class=KRCC><font color="#ff8080">학교에 선전포고를 한<br>세계 제일의 겁쟁이 신데렐라는</font> 
~~~
변환후 
--> 아예내용이 없이 생성됩니다.
 -2cpu 허진녕 님 제보

### 2018년 8월 10일
'\r' 문자 처리
특정 언어가 특정 시점에 존재하지 않는 경우 예외처리

### 2018년 7월 23일
코드 첫 줄을 #!/usr/bin/env python 로 수정해 설치과정에서 첫 줄 수정을 하지 않아도 되도록 함

### 2018년 7월 18일
chardet 대신 속도가 빠른 cchardet으로 인코딩 감지 라이브러리 변경

