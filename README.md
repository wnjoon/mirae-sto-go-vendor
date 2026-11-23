# mirae-sto-go-vendor

Go 모듈 반입본 (`go mod download`, Go 1.27.4 기준, 172개 모듈).

## 다운로드

Release 에서 버전별로 받는다. URL 형식은 아래와 같다.

```text
https://github.com/wnjoon/mirae-sto-go-vendor/releases/download/<버전>/vendor.tar.gz
```

파일명은 버전과 관계없이 `vendor.tar.gz` 로 같고, 버전은 URL 의 `<버전>` 자리(release 태그)로 지정한다.

v0.1:

```bash
curl -LO https://github.com/wnjoon/mirae-sto-go-vendor/releases/download/v0.1/vendor.tar.gz
curl -LO https://github.com/wnjoon/mirae-sto-go-vendor/releases/download/v0.1/vendor.tar.gz.sha256
```

- 링크가 다른 도메인으로 리다이렉트되므로 `curl` 에는 `-L` 이 필요하다.
- 전체 목록은 [Releases](https://github.com/wnjoon/mirae-sto-go-vendor/releases) 에서 확인한다.

## 검증과 압축 해제

```bash
shasum -a 256 -c vendor.tar.gz.sha256    # Linux: sha256sum -c
tar -xzf vendor.tar.gz
shasum -a 256 -c SHA256SUMS                   # 풀린 파일 전체 검증
```

## 구성

| 경로 | 내용 |
|---|---|
| `vendor/goproxy/` | GOPROXY 형식 모듈 저장소 (모듈 zip, `.mod`, `.info`, `.ziphash`) |
| `vendor/repos/` | 6개 repo 의 `go.mod` / `go.sum` |
| `manifest.csv` | 모듈별 버전 · Go h1 해시 · go.sum 대조 · zip SHA-256 · 원본 저장소/커밋 |
| `SHA256SUMS` | `vendor/` 아래 전체 파일의 SHA-256 |
