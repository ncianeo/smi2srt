# smi2srt
smi 자막을 srt로 변환해주는 파이썬 프로그램 (EMBY 라이브러리 자막 관리용으로 적합).
[PySAMI][pysamilink]
[pysamilink]:https://github.com/g6123/PySAMI "PySAMI"
의 smi parser를 가져옴 이 부분의 라이센스는 유지됨.
파이썬의 chardet 모듈을 이용해 자막 인코딩 자동 탐지.

## 요구사항:
- Python 2/3 (2.7~/3.6~)
- chardet

## 설치:
- chardet 설치:
~~~bash
pip install chardet
~~~
- smi2srt 설치:
1. smi2srt 파일을 열어 첫 줄의 #!/usr/bin/python3 부분을 설치된 파이썬 경로로 수정.
2. smi2srt 파일의 경로를 $PATH environment에 추가.

## 사용법:
~~~bash
smi2srt -l <TARGET_LANGUAGE> <MOVIE_LIBRARY_DIR>
~~~

- <TARGET_LANGUAGE> (default = kr) : smi 파일로부터 어느 언어를 불러올지를 지정합니다. 기본 값은 kr(한국어)입니다.
- <MOVIE_LIBRARY_DIR> : 영화 라이브러리 경로입니다. 세부 경로까지 recursive하게 탐색하므로 라이브러리 디렉토리의 최상위 PATH를 입력하시면 됩니다.

프로그램 실행 후 변환이 완료된 자막 파일과 실패한 자막 파일이 출력됩니다.
