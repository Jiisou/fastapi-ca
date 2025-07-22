# 책 출간 후 오류가 발견된 부분을 수정합니다.

## p7
원문
```
$ poetry shell
Creating virtualenv fastapi-ca-6_... in /Users/name/Library/Caches/pypoetry/virtualenvs
Spawning shell within /Users/name/Library/Caches/pypoetry/virtualenvs/fastapi-ca-6_...

$ emulate bash -c '. /Users/name/Library/Caches/pypoetry/virtualenvs/fastapi-ca-6_.../bin/activate

(fastapi-ca) $
```

수정
```
$ poetry shell
**Looks like you're trying to use a Poetry command that is not available.**

Since Poetry (2.0.0), the shell command is not installed by default. You can use,

  - the new env activate command (recommended); or
  - the shell plugin to install the shell command

Documentation: https://python-poetry.org/docs/managing-environments/#activating-the-environment

Note that the env activate command is not a direct replacement for shell command.

$ poetry env use python3.11
$ poetry env list --full-path
/Users/jisu/Library/Caches/pypoetry/virtualenvs/fastapi-ca-xxx...-py3.11 (Activated)
$ emulate bash -c '/.../bin/activate'
```

## p49. 코드 3.13
원문
```
@router.post("")
def create_user(user: CreateUserBody):
    return user
```

수정
```
@router.post("", status_code=201)
def create_user(user: CreateUserBody):
    return user
```

## p62
원문
```
with SessionLocal() as db:
    db = SessionLocal()  //(3)
    db.add(new_user)  //(4)
    db.commit()  //(5)
```
(3): 앞서 만든 `SessionLocal`을 이용해 새로운 세션 객체를 생성한다.

수정
```
with SessionLocal() as db:  //(3)
    db.add(new_user)  //(4)
    db.commit()  //(5)
```

(3): `SessionLocal` 객체를 생성한다. with 구문을 이용하여 세션이 자동으로 닫히도록 하였다.

## p82
원문
```
password=crypto.encrypt("test")
```
수정
```
password=Crypto().encrypt("test")
```

