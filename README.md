# smi2srt
smi 자막을 srt로 변환해주는 파이썬 프로그램 (EMBY 라이브러리 자막 관리용으로 적합).
우분투 리눅스 기준으로 작성했고 http://bryan.wiki/263 를 참조함.

요구사항:
- iconv
- sed
- python 2.7 or newer
- libsubtitles-perl (Ubuntu 16.04 or newer)

설치:
데비안 리눅스 환경이라면 python과 libsubtitles-perl만 설치하면 바로 사용이 가능합니다.
smi2srt 파일이 포함된 경로를 PATH dependency에 추가하면 설치 끝.

사용법:
smi2srt -b <BASE_ENCODING> -t <TARGET_ENCODING> <MOVIE_LIBRARY_DIR>

- <BASE_ENCODING> (default = euc-kr) : 변환할 .smi 자막의 인코딩입니다. 대부분의 smi자막파일은 euc-kr로 인코딩 되어있으므로 디폴트로 사용하셔도 됩니다.
- <TARGET_ENCODING> (default = utf-8) : 변환된 .srt 자막의 인코딩입니다. EMBY등의 미디어 서버 라이브러리를 구축하려는 경우 utf-8로 디폴트로 사용하시면 됩니다.
- <MOVIE_LIBRARY_DIR> : 영화 라이브러리 경로입니다. 세부 경로까지 recursive하게 탐색하므로 라이브러리 디렉토의 최상위 PATH를 입력하시면 됩니다.

프로그램 실행 후 변환이 완료된 자막 파일과 실패한 자막 파일이 출력됩니다.


주의사항:
iconv 에러는 <BASE_ENCODING>이 <TARGET_ENCODING>과 다른 경우 발생합니다. 만약, 다운받은 자막의 기본 인코딩이 utf-8이었을 경우 문제없이 변환이 진행되니 무시하셔도 됩니다.
만약 파일의 확장자가 .SMI인 경우 .smi로 변경 후 작업이 진행됩니다.
