# 2차 프로젝트 백엔드 회원가입 SMS 인증 Logic 레포

1. 일일히 Key value와 expiration date를 넣기엔 부하적인 측면과 구현부분에서 무리가있고 비효율적이라 판단, redis를 사용하여 In-memory에서 관리하는 방법을 택함.
2. LIMIT_TIME을 문자 발송 신호를 받은 후 180초로 설정함. LIMIT_TIME이 지나면 stringRedisTemplate.delete로 redis에서 해당 key value를 삭제함.
3. 4자리 무작위 난수를 생성하고 해당 난수를 redis에 저장하고 CoolSMS api를 통해 Front로 받은 phoneNumber로 보냄.
4. verifySms 함수로 인증번호 일치 여부 확인
5. 문자 발송실패, 인증번호 불일치 Exception 정의해둠
6. Redis 기본 configuration 완료
7. Front와 통신을 위한 CORS configuration 완료


TODO :
**Spamming 방지를 위해 delay설정 구현**
번호입력형식이 정해져있어서(00012345678) 정규식사용 로직코드 FE팀에게 전달해야함
인증키가 disk까지 안가는데 굳이 encrypt 해야할까? 고민좀 해야함

총 구현시간 : 9시간 39분
