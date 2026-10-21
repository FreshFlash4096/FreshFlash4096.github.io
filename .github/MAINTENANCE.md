# Memoria 저장소 관리

이 저장소는 Publii의 정적 게시 결과물을 GitHub Pages로 제공한다. 기존 글의 URL과 이미지 경로를 보존하면서, 소개와 운영 문서를 함께 관리한다.

## 현재 확인한 구조

2026년 10월 21일, 기준 커밋 `2aa767a52afb81ae258840c7e1b0cb596ac2b7ee`에서 확인했다.

- GitHub Pages 게시 원본은 `main`의 루트(`/`), `build_type`은 `legacy`이며 HTTPS가 적용되어 있다. 사용자 정의 도메인은 없다.
- Pages의 기본 `pages-build-deployment` 작업이 동작한다. 저장소가 정의한 Actions 워크플로는 없다.
- 전체 127개 HTML에 Publii 생성기 표시가 있고, [블로그 소개](https://freshflash4096.github.io/about-this-blog/)도 Publii 작성·GitHub Pages 호스팅을 명시한다.
- 편집 데이터베이스, 사이트 설정, 테마 템플릿은 추적하지 않는다. 이 저장소만으로 편집 환경 전체를 복구할 수 있다고 가정하지 않는다.
- 과거에 `Updated from Publii` 커밋을 사용했다. 최근 커밋은 사용자 지정 메시지이며 `files.publii.json`도 포함한다. 이것만으로 현재의 업로드 수단이 Publii의 GitHub Pages 연결인지, 일반 Git 연결인지, 수동 반영인지 확정할 수 없다. 사용 버전과 로컬 설정도 별도 확인이 필요하다.

## 생성 파일과 관리 파일

| 구분 | 관리 원칙 |
| --- | --- |
| 글의 HTML, `tags/`, `authors/`, `page/` | Publii 원본에서 변경하고 다시 생성한다. 슬러그 변경은 별도 검토한다. |
| `media/`, `assets/` | 글별 참조와 생성 규칙을 함께 확인한다. 중복 바이트만으로 삭제하지 않는다. |
| 사이트맵, 피드, `robots.txt`, `files.publii.json` | 생성·동기화 산출물로 유지한다. 파일 목록이나 체크섬을 수동으로 갱신하지 않는다. |
| `README.md`, `.gitignore`, `.github/MAINTENANCE.md` | 저장소 관리 파일이다. 실제 반영 경로에서 보존되는지 확인한다. |

`.gitignore`는 OS 메타데이터만 제외한다. 게시에 필요한 HTML, 이미지, CSS, JavaScript와 생성 파일은 계속 추적한다. 이미 추적하는 파일은 ignore 규칙을 추가해도 자동으로 추적 해제되지 않는다.

## Publii 재게시와 관리 파일 보존

[Publii 공식 GitHub Pages 안내](https://getpublii.com/docs/host-static-website-github-pages.html)는 초기 README가 동기화 과정에서 제거됨을 설명한다. 조사한 [GitHub Pages 배포 구현](https://github.com/GetPublii/Publii/blob/master/app/back-end/modules/deploy/github-pages.js)의 `buildDeltaTree`도 로컬 출력에 없는 원격 파일을 삭제 대상으로 만든다. 이는 조사 시점의 upstream 구현이며, 운영 중인 버전에서 직접 재현한 결과는 아니다.

따라서 관리 파일이 GitHub에 있다는 이유만으로 다음 동기화에서도 유지된다고 가정하지 않는다. `.gitignore`는 Publii 원격 삭제 방지 목록이 아니다. 로컬 출력 폴더에만 파일을 복사해 두는 방법도 출력 재생성으로 사라질 수 있다.

현재의 게시 방식을 바꾸지 않고 다음 사항부터 확인한다.

1. 사용 중인 Publii 버전, 연결 방식, 대상 저장소와 대상 브랜치를 확인한다. 인증값을 문서나 저장소에 기록하지 않는다.
2. 관리 파일 세 개가 생성 결과에 포함되는지, 또는 수동 Git 반영 과정에서 보존되는지 확인한다. [Tools의 File Manager](https://getpublii.com/docs/tools.html)는 추가 root 파일을 관리하는 공식 경로다. README는 이 경로를 검토할 수 있으나, 숨김 파일과 `.github/` 하위 경로까지 포함되는지는 해당 버전의 출력에서 검증한다.
3. 시험이 필요하면 복제한 편집 프로젝트와 별도 시험 저장소를 사용한다. 이번 정비에서는 운영 Publii 설정이나 연결을 변경하지 않았다.
4. 운영 재게시 전에 글·리소스의 의도한 변경과 관리 파일 보존을 비교한다. 예기치 않은 삭제가 있으면 게시를 중단하고 원인을 확인한다.
5. 게시 후 대표 글, 이미지, 사이트맵, 피드와 관리 파일이 유지되는지 확인한다.

관리 파일을 항상 출력에 포함하도록 설정하거나, 생성물 반영 전에 필요한 관리 파일을 보존하는 절차는 실제 게시 방식을 확인한 뒤 정한다. 자동 복원 Actions나 새로운 배포 파이프라인은 추가하지 않았다.

## 안전한 변경 범위

README·운영 문서의 보완과 불필요한 OS 메타데이터 제거는 작업 브랜치와 PR로 검토한다. 관리 파일이 추가되는 것도 게시 원본에 포함될 수 있으므로 공개해도 되는 정보만 기록한다.

중복·미참조 이미지 제거와 용량 최적화는 먼저 Publii 원본, HTML·CSS·스크립트·피드·사이트맵의 참조, 외부 직접 링크 및 갤러리 동작을 대조한다. 글별 이미지 사본은 같은 바이트라도 각각의 URL이 사용될 수 있다. Git은 동일한 내용의 blob을 공유하므로 중복 경로 삭제량과 Git 저장소의 절감량도 같지 않다.

다음 변경은 별도 설계와 승인 후 진행한다.

- 글·이미지 디렉터리 재구성 및 URL 변경
- Git 기록 재작성과 대규모 콘텐츠 삭제
- 게시 브랜치·배포 방식·Actions 변경
- 라이선스 선택과 콘텐츠 재사용 정책 확정

## 변경 검증

관리 파일만 정비할 때에는 기준 커밋과의 차이가 허용한 관리 파일·OS 메타데이터에 한정되는지 확인한다. HTML·이미지·CSS·JavaScript·글꼴·사이트맵·피드의 경로와 바이트가 같으면 기존 생성 결과에 대한 변경은 없다.

리소스 참조 검사에서는 URL의 query string과 fragment를 분리하고 `srcset`, CSS의 상대 경로, 갤러리 링크, Atom·JSON Feed와 사이트맵의 이미지도 확인한다. 정적 검사만으로 동적 스크립트·외부 링크·Publii 원본의 사용 여부를 모두 판단할 수 없으므로, 미참조 결과는 삭제 허가로 사용하지 않는다.

운영 Pages의 성공 기록은 현재 게시본에 관한 증거다. 작업 브랜치가 실제로 운영 배포되었거나 다음 Publii 재게시에서 유지된다는 증거로 사용하지 않는다.

## 확인이 필요한 기존 항목

- `samsung-mz-vmx2t00/`의 이미지 URL에 `media/posts/25//`가 사용되어 사이트맵에도 반영되어 있다. 점검 시 두 슬래시 URL과 일반 경로 모두 HTTP 200이며 이미지 바이트도 같았다. 경로 표기는 Publii 원본에서 검토한다.
- `klevv-c910-4tb-review/`에는 대상 ID가 없는 `#non-existing-page-with-id-33` 링크가 있다. 원본 글에서 올바른 대상을 확인한 뒤 수정한다.
- `to-do/`는 canonical을 가지지만 사이트맵에는 없다. 의도적인 제외 여부를 확인한다.
- `tags/micorn/`, `add-comment-functoin/` 등의 기존 경로는 철자만 보고 바꾸지 않는다. 외부 링크가 있을 수 있다.
- LICENSE 파일이 없다. 글·직접 제작 이미지·벤치마크 데이터·코드·테마·글꼴·제3자 자료의 적용 범위를 나누어 검토한다.

[Publii 서버 설정 문서](https://getpublii.com/docs/recommended-server-settings.html)는 `files.publii.json`을 사용하는 연결에서 이 파일을 삭제하면 전체 재업로드가 필요할 수 있다고 설명한다. 파일의 존재만으로 불필요하다고 판단하지 않는다.
