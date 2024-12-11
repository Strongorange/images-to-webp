
# 이미지 WebP 변환기

이 프로젝트는 다양한 이미지 파일(JPG, JPEG, PNG)을 WebP 형식으로 변환할 수 있는 간단한 Docker 컨테이너를 제공합니다. 가로와 세로 크기 조절 옵션을 포함하여 이미지의 크기를 축소할 수 있으며, 가로 길이만 지정하면 원본 비율을 유지합니다.

## 기능

- 지원 이미지 포맷: JPG, JPEG, PNG
- 이미지를 WebP 형식으로 변환
- 이미지 크기를 조절하는 리사이징 옵션 제공
- 가로 길이만 지정 시 자동으로 원본 비율 유지

## 빠른 시작

### 1. Docker 이미지 다운로드

Docker Hub에서 Docker 이미지를 다운로드합니다:

```bash
docker pull strongorange/image-to-webp:latest
```

### 2. 이미지 준비

- 로컬에 `images` 폴더를 생성합니다.
- 변환하려는 이미지를 `images` 폴더에 넣습니다.

### 3. Docker 컨테이너 실행

`images` 폴더가 위치한 디렉토리에서 다음 명령어를 실행합니다:

```bash
docker run --rm -v $(pwd)/images:/data -e WIDTH=800 strongorange/image-to-webp
```

### 명령어 설명

- `-v $(pwd)/images:/data`: 로컬의 `images` 폴더를 컨테이너의 `/data` 디렉토리에 마운트합니다.
- `-e WIDTH=800`: 출력 이미지의 가로 길이를 800으로 설정합니다. 세로 길이는 원본 비율에 맞추어 자동으로 조정됩니다.
- `-e QUALITY=100`: 출력 이미지의 품질을 결정합니다. 기본값은 75 입니다.

명령어 실행 후, 변환된 이미지들은 `images` 폴더 안의 `webp` 하위 폴더에 저장됩니다.

---

## 예시

`images` 폴더에 `example.png` 파일이 있는 경우:

```plaintext
images/
├── example.png
```

위 명령어 실행 후 결과:

```plaintext
images/webp/
├── example.webp
```

## 추가 참고사항

- `WIDTH`와 `HEIGHT` 환경 변수를 모두 지정하면 출력 이미지의 가로와 세로 길이를 설정할 수 있습니다. `WIDTH`만 지정할 경우, 세로 길이는 원본 비율에 맞추어 자동으로 조정됩니다.
- 지원 포맷: JPG, JPEG, PNG.

---

## 라이선스

이 프로젝트는 MIT 라이선스를 따릅니다.
