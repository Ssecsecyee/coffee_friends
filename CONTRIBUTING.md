# 팀 작업 흐름

- main: 검토 완료본. Vercel 운영 페이지에 연결하는 브랜치.
- develop: 수정 및 검토용 브랜치. Vercel Git 연결 후 미리보기 배포로 확인.

## 수정에서 반영까지

1. develop에서 최신 내용을 받고 HTML, CSS, JS 및 assets를 수정합니다.
2. 변경 사항을 커밋하고 develop에 푸시합니다.
3. GitHub에서 develop → main Pull Request를 만듭니다.
4. Vercel 미리보기와 변경 파일을 확인합니다.
5. 검토가 끝나면 main으로 머지합니다. 운영 URL은 그대로 유지됩니다.
6. 다음 작업 전에 develop을 최신 main과 동기화합니다.

```sh
git switch develop
git pull --ff-only origin develop
# 파일 수정 후
git add index.html styles.css script.js assets
git commit -m "Update product detail page"
git push origin develop
```

main 반영 후 동기화:

```sh
git switch develop
git fetch origin
git merge origin/main
git push origin develop
```

이미지 원본 PNG는 상위 이미지시안 폴더에 보관하고 웹용 WebP만 Git으로 관리합니다. .vercel과 비밀 환경변수 파일은 커밋하지 않습니다.
