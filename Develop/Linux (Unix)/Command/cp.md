```shell 
cp abc.txt def.txt #abc.txt 파일을 def.txt로 이름을 바꾸어 복사합니다.

cp abc.txt xyz 
# xyz라는 디렉토리가 없다면 abc.txt 파일을 xyz 파일로 복사합니다.
# xyz라는 디렉토리가 있다면 xyz 디렉토리 안에 abc.txt 파일을 복사합니다.

cp abc.txt xyz/def.txt # abc.txt 파일을 xyz 디렉토리 안에 def.txt라는 이름으로 복사합니다.

cp -r abc xyz
# abc가 디렉토리이고 xyz라는 디렉토리가 없다면, abc 디렉토리를 xyz로 이름을 바꾸어 복사합니다.
# abc가 디렉토리이고 xyz라는 디렉토리가 있다면, abc 디렉토리를 xyz 디렉토리 안에 복사합니다. 즉 xyz/abc가 됩니다.

cp -r abc xyz/zzz
# abc가 디렉토리이고 xyz/zzz라는 디렉토리가 없다면, abc 디렉토리를 xyz 디렉토리 안에 zzz로 이름을 바꾸어서 복사합니다.
# abc가 디렉토리이고 xyz/zzz라는 디렉토리가 있다면, abc 디렉토리를 xyz/zzz 디렉토리 안에 복사합니다. 즉 xyz/zzz/abc가 됩니다.
```