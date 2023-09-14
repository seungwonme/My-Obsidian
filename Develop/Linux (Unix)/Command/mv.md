```shell
mv abc.txt def.txt # abc.txt 파일을 def.txt로 이름을 바꾸어 이동, 파일 이름을 바꾸는 것과 결과가 같습니다.

mv abc.txt xyz
# xyz라는 디렉토리가 없다면 abc.txt 파일을 xyz로 이름을 바꾸어 이동합니다.
# xyz라는 디렉토리가 있다면 xyz 디렉토리 안으로 abc.txt 파일을 이동합니다.

mv abc.txt xyz/def.txt
# abc.txt 파일을 xyz 디렉토리 안으로 def.txt로 이름을 바꾸어 이동합니다.

mv abc xyz
# abc가 디렉토리이고 xyz라는 디렉토리가 없다면, abc 디렉토리를 xyz로 이름을 바꾸어 이동합니다.
# abc가 디렉토리이고 xyz라는 디렉토리가 있다면, abc 디렉토리를 xyz 디렉토리 안으로 이동합니다. 즉 xyz/abc가 됩니다.

mv abc xyz/zzz
# abc가 디렉토리이고 xyz/zzz라는 디렉토리가 없다면, abc 디렉토리를 xyz 디렉토리 안으로 zzz로 이름을 바꾸어 이동합니다.
# abc가 디렉토리이고 xyz/zzz라는 디렉토리가 있다면, abc 디렉토리를 xyz/zzz 디렉토리 안으로 이동합니다. 즉 xyz/zzz/abc가 됩니다.
```