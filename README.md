> **참고:** 이 저장소는 Anthropic이 만든 Claude용 스킬(Skills) 구현체를 담고 있습니다. Agent Skills 표준에 대한 정보는 [agentskills.io](http://agentskills.io)를 참고하세요.

# 스킬 (Skills)

스킬은 Claude가 특정 작업을 더 잘 수행하도록 필요할 때 불러와 사용하는 **지침·스크립트·리소스를 담은 폴더**입니다. 스킬을 이용하면 회사 브랜드 가이드에 맞춘 문서 작성, 조직 고유의 업무 절차에 따른 데이터 분석, 개인 업무 자동화 등 특정 작업을 Claude가 일관된 방식으로 반복 수행하도록 가르칠 수 있습니다.

더 자세한 내용은 아래 문서를 참고하세요.

- [스킬이란?](https://support.claude.com/en/articles/12512176-what-are-skills)
- [Claude에서 스킬 사용하기](https://support.claude.com/en/articles/12512180-using-skills-in-claude)
- [나만의 스킬 만들기](https://support.claude.com/en/articles/12512198-creating-custom-skills)
- [Agent Skills로 에이전트를 실전에 대비시키기](https://anthropic.com/engineering/equipping-agents-for-the-real-world-with-agent-skills)

# 이 저장소에 대하여

이 저장소에는 Claude 스킬 시스템으로 무엇을 할 수 있는지 보여주는 예시 스킬들이 들어 있습니다. 예술·음악·디자인 같은 창작 분야부터 웹앱 테스트, MCP 서버 생성 같은 기술 작업, 사내 커뮤니케이션·브랜딩 같은 기업 업무까지 다양합니다.

각 스킬은 독립된 폴더로 구성되어 있으며, 폴더 안의 `SKILL.md` 파일에 Claude가 사용하는 지침과 메타데이터가 들어 있습니다. 자신만의 스킬을 만들 때 아이디어를 얻거나 다양한 작성 패턴을 익히는 용도로 둘러보세요.

이 저장소의 스킬 다수는 오픈소스(Apache 2.0)입니다. 또한 [Claude의 문서 기능](https://www.anthropic.com/news/create-files)을 실제로 구동하는 문서 생성·편집 스킬도 `skills/docx`, `skills/pdf`, `skills/pptx`, `skills/xlsx` 폴더에 포함되어 있습니다. 이 네 가지는 오픈소스가 아닌 **소스 공개(source-available)** 형태이며, 실제 서비스에서 쓰이는 복잡한 스킬의 참고 자료로 개발자에게 공유한 것입니다.

## 면책 조항

이 스킬들은 **시연 및 학습 목적**으로만 제공됩니다. 일부 기능은 Claude에서 실제로 제공되지만, Claude에서 받는 실제 구현과 동작은 이 저장소의 내용과 다를 수 있습니다. 이 스킬들은 패턴과 가능성을 보여주기 위한 것이므로, 중요한 작업에 사용하기 전에 반드시 자신의 환경에서 충분히 테스트하세요.

# 구성

- [./skills](./skills): 창작·디자인, 개발·기술, 기업·커뮤니케이션, 문서 스킬 예시
- [./spec](./spec): Agent Skills 사양(스펙)
- [./template](./template): 스킬 템플릿

# Claude Code, Claude.ai, API에서 사용해 보기

## Claude Code

Claude Code에서 아래 명령어를 실행하면 이 저장소를 플러그인 마켓플레이스로 등록할 수 있습니다.

```
/plugin marketplace add anthropics/skills
```

그다음 원하는 스킬 묶음을 설치합니다.

1. `Browse and install plugins` 선택
2. `anthropic-agent-skills` 선택
3. `document-skills` 또는 `example-skills` 선택
4. `Install now` 선택

또는 아래 명령어로 바로 설치할 수도 있습니다.

```
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

설치 후에는 스킬 이름만 언급하면 사용할 수 있습니다. 예를 들어 `document-skills`를 설치했다면 Claude Code에 "PDF 스킬을 사용해서 path/to/some-file.pdf의 양식 필드를 추출해줘"처럼 요청하면 됩니다.

## Claude.ai

이 예시 스킬들은 Claude.ai 유료 플랜에서 이미 모두 사용할 수 있습니다.

이 저장소의 스킬을 쓰거나 직접 만든 스킬을 업로드하려면 [Claude에서 스킬 사용하기](https://support.claude.com/en/articles/12512180-using-skills-in-claude) 안내를 따르세요.

## Claude API

Claude API를 통해 Anthropic이 미리 만든 스킬을 사용하거나 직접 만든 스킬을 업로드할 수 있습니다. 자세한 내용은 [Skills API 빠른 시작](https://docs.claude.com/en/api/skills-guide#creating-a-skill)을 참고하세요.

# 기본 스킬 만들기

스킬은 만들기 쉽습니다. YAML 머리말(frontmatter)과 지침이 담긴 `SKILL.md` 파일 하나가 들어 있는 폴더면 됩니다. 이 저장소의 **template-skill**을 출발점으로 사용하세요.

```markdown
---
name: my-skill-name
description: 이 스킬이 무엇을 하는지, 언제 사용하는지에 대한 명확한 설명
---

# 내 스킬 이름

[이 스킬이 활성화되었을 때 Claude가 따를 지침을 여기에 작성하세요]

## 예시
- 사용 예시 1
- 사용 예시 2

## 가이드라인
- 가이드라인 1
- 가이드라인 2
```

머리말에 필요한 항목은 두 가지뿐입니다.

- `name` — 스킬의 고유 식별자 (영문 소문자, 공백 대신 하이픈 사용)
- `description` — 스킬이 무엇을 하고 언제 사용하는지에 대한 충분한 설명

그 아래 마크다운 본문에는 Claude가 따를 지침, 예시, 가이드라인을 작성합니다. 자세한 내용은 [나만의 스킬 만들기](https://support.claude.com/en/articles/12512198-creating-custom-skills)를 참고하세요.

# 파트너 스킬

스킬은 Claude가 특정 소프트웨어를 더 잘 다루도록 가르치는 좋은 방법입니다. 파트너사의 훌륭한 예시 스킬이 나오면 이곳에 소개할 예정입니다.

- **Notion** — [Notion Skills for Claude](https://www.notion.so/notiondevs/Notion-Skills-for-Claude-28da4445d27180c7af1df7d8615723d0)
