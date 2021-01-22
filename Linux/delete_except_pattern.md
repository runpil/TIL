# 특정 문자 패턴 제외하고 삭제
```bash
find . -type f ! -name "test*" -exec rm -rf {} \;
```