# Memoria

**SSD와 저장장치 기술을 중심으로, 직접 측정하고 살펴본 내용을 기록하는 개인 기술 블로그입니다.** 소비자용·엔터프라이즈 SSD 리뷰, NAND Flash와 컨트롤러 분석, 벤치마크 방법론을 다루며 Homelab과 하드웨어에 관한 경험도 함께 기록합니다.

블로그 읽기: **[freshflash4096.github.io](https://freshflash4096.github.io/)**

## 주요 내용

- **SSD 리뷰** — NAND 기반 SATA·NVMe SSD부터 Intel Optane, Samsung Z-SSD 등 다양한 저장장치의 구성과 동작을 살펴봅니다.
- **벤치마크와 측정 방법** — Pre-Conditioning, Steady State, 읽기·쓰기 혼합 부하, SLC 캐시 회복, 지연 시간과 일관성을 비교합니다. 측정 조건과 해석의 한계는 각 글을 기준으로 확인해 주세요.
- **저장장치 기술과 하드웨어** — NAND Flash, 컨트롤러, 인터페이스, 메모리·스토리지 기술 및 관련 소식을 정리합니다.
- **Homelab 기록** — NAS, 서버, 네트워크 장비와 개인 실험 환경에 관한 경험을 공유합니다.

[Review](https://freshflash4096.github.io/tags/benchmark/) · [벤치마크 방법론](https://freshflash4096.github.io/refresh-ssd-benchmark-method/) · [Homelab](https://freshflash4096.github.io/tags/homelab/) · [블로그 소개](https://freshflash4096.github.io/about-this-blog/)

## 이 저장소의 역할

이 저장소는 [Publii](https://getpublii.com/)로 작성한 블로그의 **정적 웹사이트 배포 결과물**을 보관합니다. GitHub Pages는 `main` 브랜치의 루트(`/`)를 게시합니다.

저장소에는 생성된 HTML, 스타일, 스크립트와 게시용 이미지가 들어 있습니다. Publii의 편집용 데이터베이스·사이트 설정·테마 원본을 포함한 전체 편집 프로젝트나 원시 벤치마크 데이터 모음을 제공하는 저장소는 아닙니다. 글의 내용과 그래프를 읽으려면 공식 웹사이트를 이용해 주세요.

## 저장소 구조

| 경로 | 역할 |
| --- | --- |
| `index.html` | 블로그 첫 화면 |
| `<글 슬러그>/index.html` | 개별 글과 고정 페이지. 기존 경로가 글의 URL을 구성합니다. |
| `tags/`, `authors/`, `page/` | 태그·작성자 목록 및 페이지 나누기 |
| `assets/` | 게시용 CSS, JavaScript, 글꼴, SVG |
| `media/posts/` | 글별 이미지와 갤러리·썸네일 |
| `media/website/` | 사이트 공통 이미지 |
| `sitemap.xml`, `sitemap.xsl`, `robots.txt` | 검색엔진과 사이트맵 관련 파일 |
| `feed.xml`, `feed.json` | Atom 피드와 JSON Feed |
| `404.html` | 오류 페이지 |
| `files.publii.json` | Publii가 생성한 파일 목록과 동기화용 값. 수동으로 편집하지 않습니다. |
| `.github/MAINTENANCE.md` | 저장소 관리와 재게시 시 주의 사항 |

## 작성과 게시

글과 리소스는 Publii의 편집 프로젝트에서 관리하고, 생성된 결과를 이 저장소에 반영하는 구조입니다. 생성된 HTML을 직접 수정하면 다음 생성·게시 때 변경이 사라질 수 있습니다. 글의 슬러그와 `media/` 경로는 기존 링크를 유지하기 위해 보존합니다.

**README와 같은 관리 파일도 재게시 과정에서 삭제될 수 있습니다.** Publii의 GitHub Pages 동기화는 출력에 없는 원격 파일을 제거할 수 있으며, `.gitignore`만으로 이를 막을 수는 없습니다. 현재 사용 중인 반영 방식에서 관리 파일이 보존되는지 확인한 뒤 재게시해야 합니다. 자세한 절차와 확인되지 않은 항목은 [운영 문서](.github/MAINTENANCE.md)에 정리했습니다.

## 저작권과 재사용

이 저장소에는 전체 파일에 공통으로 적용하는 라이선스를 지정하지 않았습니다. 저장소 공개 자체가 글·사진·그래프·측정 데이터의 자유로운 재사용을 허락한다는 뜻은 아닙니다.

직접 작성한 콘텐츠와 별도로, 인용 이미지·제품 자료·테마·글꼴·외부 코드 등에는 각 권리자의 권리와 이용 조건이 적용될 수 있습니다. 각 글의 출처와 개별 표시를 확인해 주세요. 소스코드와 글·이미지·벤치마크 데이터에 대한 통합 라이선스는 임의로 부여하지 않습니다.

## 문의

내용에 관한 문의와 재사용 요청은 [블로그 소개 페이지](https://freshflash4096.github.io/about-this-blog/)에 안내된 이메일 **[freshflash4096@gmail.com](mailto:freshflash4096@gmail.com)**로 연락해 주세요. 오류를 알려 주실 때에는 해당 글의 URL과 확인한 내용을 함께 보내 주시면 도움이 됩니다.
