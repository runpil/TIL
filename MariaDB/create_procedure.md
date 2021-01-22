## MySQL & MariaDB 스토어드 프로시저 생성
```sql
# 프로시저 생성
DELIMITER $$  # 스토어드 프로그램 시작. 구분문자 $$
CREATE PROCEDURE SP_TEST()
BEGIN  # 코드 시작
    SELECT 'TEST PROCEDURE';
END $$  # 코드 끝. 구분문자 $$ 닫기
DELIMITER ;

# 프로시저 실행
CALL SP_TEST()
```
## 만날 수 있는 오류
```
ERROR 1064 (42000): You have an error in your SQL syntax; 
check the manual that corresponds to your MySQL server version 
for the right syntax to use near '()' at line 1
```
- BEGIN ~ END 구문 내 쿼리 마지막에 세미콜론(;) 을 하지 않은 경우 발생