# aladinAPI
알라딘 api를 이용하여 중고책 현황 웹페이지 제작 (EC2)

cmd에서 사용(ssh 연결 전)
연결: 
ssh -i "C:\pem\jjeong2.pem" ubuntu@13.238.150.170

파일 다운:
scp -i "C:\pem\jjeong2.pem" ubuntu@ec2-13-238-150-170.ap-southeast-2.compute.amazonaws.com:/home/ubuntu/allbook.py C:\Users\20191648

파일 업로드: 
scp -i "C:\pem\jjeong2.pem" C:\pem\allbook.py ubuntu@13.238.150.170:/home/ubuntu

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////
일정 시간마다 실행
crontab -e

서버내 가상환경 명령어
source myenv/bin/activate
deactivate

서버 로그 명령어
sudo tail -f /var/log/syslog

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////
슈퍼셋 설정(서버 접속 전에 매번 해줘야 함)
환경 변수 설정:
export FLASK_APP=superset
export SUPERSET_CONFIG_PATH='/home/ubuntu/.superset/superset_config.py'

초기화:
superset db upgrade
superset init

슈퍼셋 서버 실행:
superset run -h 0.0.0.0 -p 8088 --with-threads --reload --debugger

public으로 접속하는 슈퍼셋 주소
http://13.238.150.170:8088/superset/dashboard/1/?standalone=true

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////

슈퍼셋 서버 시작하는 방법

1. myenv(가상 환경) 실행 : 슈퍼셋과 파이썬 버전 호환 문제로 가상 환경을 만들어서 해당 환경에 슈퍼셋을 다운 받음
2. 환경 변수 설정 및 초기화 (위 코드 참고)
3. 서버 실행 (위 코드 참고)
4-1. http://13.238.150.170:8088 으로 접속 (admin 경로임. 아이디 : Jun, 비밀번호 : ju001102)
4-2. public으로 접속 시, http://13.238.150.170:8088/superset/dashboard/1/?standalone=true 로 접속.


/////////////////////////////////////////////////////////////////////////////////////////////////////////////////
서버 용량 관련 명령어
df -h
swapon -s
swapon --show
/root/swapfile swap swap auto 0 0

/////////////////////////////////////////////////////////////////////////////////////////////////////////////////

구동 환경 :

백엔드:
알라딘 OpenAPI
Amazon EC2 (서버)
Python 3.12.3 및 3.10.16
LINUX Crontab
Superset 2.3.3 (DB 쿼리 처리)
GIT

프론트:
Superset 2.3.3 (데이터 시각화 및 페이지 출력)

로컬:
MYSQL (로컬 저장소 사용, api로 책 정보를 받아 로컬 DB에 저장)

