# 🎨 Designer — 썸네일 자동화를 위한 모든 디자인 변수, 톤앤매너 규칙('Design_System_Input.json')을 최종 점검하고 개발팀이 즉시 실행할 수 있도록 완벽하게 확정하여 전달 준비를 완료하세요.

🎨 Designer: 작업 시작합니다.

요청하신 대로 썸네일 자동화를 위한 모든 디자인 변수와 톤앤매너 규칙(`Design_System_Input.json`)을 최종 점검하고 개발팀이 즉시 실행할 수 있도록 완벽하게 확정하여 전달 준비를 완료합니다.

아래는 개발팀(코다리)이 바로 적용할 수 있는 최종 디자인 시스템 입력값 및 품질 검증 기준입니다.

---

# 🖼️ Design System Input & Tone (Mood) Rules for Thumbnail Automation

## 1. Design_System_Input.json (핵심 디자인 변수)

이 JSON 파일은 모든 썸네일 생성 AI 프롬프트에 적용될 **구체적인 시각적 규칙과 제약 조건**을 정의합니다.

```json
{
  "brand": {
    "name": "DAON (ON다온)",
    "primary_color": "#007BFF",
    "secondary_color": "#6C757D",
    "accent_color": "#FFC107",
    "font_family_suggestion": "Pretendard, sans-serif"
  },
  "layout_rules": {
    "aspect_ratio": "16:9",
    "text_placement": "Center-Left or Center-Right (Avoid cluttering the bottom right corner)",
    "visual_emphasis": "Strong focal point on the main subject/concept. Use negative space effectively.",
    "rule_for_contrast": "Minimum contrast ratio of 4.5:1 between text and background."
  },
  "typography_rules": {
    "font_hierarchy": {
      "title": "Bold, Large, High Impact (e.g., Impact or a strong Sans-serif)",
      "subtitle": "Medium weight, clear readability",
      "details": "Light weight, small but legible"
    },
    "text_style": "Use clean, modern typography. Avoid overly decorative fonts unless specified by the Tone."
  },
  "visual_elements": {
    "color_palette": [
      {"name": "DAON Blue", "hex": "#007BFF", "usage": "Primary branding/Trust"},
      {"name": "Neutral Gray", "hex": "#6C757D", "usage": "Backgrounds/Subtext"},
      {"name": "Accent Yellow", "hex": "#FFC107", "usage": "Call-to-Action/Highlight"}
    ],
    "imagery_style": "High-quality, clean, cinematic lighting. Avoid overly saturated or cartoonish styles."
  },
  "information_density_rules": {
    "max_info_density": "60%",
    "rule_description": "Ensure the visual focuses on the core message; text should support, not overwhelm the image."
  }
}
```

## 2. Tone (Mood) Rules (감성 및 분위기 변형 규칙)

이 규칙은 AI가 이미지의 **전체적인 분위기와 감성**을 조정하는 데 사용됩니다. 개발팀은 이 규칙을 통해 원하는 '느낌'을 시스템에 주입해야 합니다.

| Tone/Mood | 핵심 키워드 | 색상 톤 (Color Tone) | 대비 및 구도 (Contrast & Composition) | 적용 목표 (Goal) |
| :--- | :--- | :--- | :--- | :--- |
| **Trustworthy / Reliable** | Professional, Solid, Clear | Heavy use of DAON Blue (#007BFF). Minimal use of yellow. | Balanced composition. High readability. Even lighting. | 신뢰감 및 전문성 강조 (AI 팩트 정보) |
| **Urgent / Actionable** | Dynamic, Alert, Immediate | Use Accent Yellow (#FFC107) for immediate attention. Darker background tones. | Diagonal lines or strong visual arrows/highlights. High contrast. | 즉각적인 클릭 유도 및 긴급성 부여 |
| **Calm / Educational** | Insightful, Reflective, Deep | Muted blues and grays (Neutral Gray). Soft lighting. | Ample negative space. Symmetrical or balanced layout. Soft focus elements. | 깊이 있는 정보 전달 및 지식 공유 |

## 3. 가독성 검증 루프 (Readability Verification Loop)

자동화 시스템은 생성된 결과물이 다음 기준을 충족하는지 **반드시 자체 검증**해야 합니다.

1.  **대비율 확인:** 모든 주요 텍스트와 배경 간의 대비 비율이 최소 $\text{4.5:1}$ 이상인지 측정한다.
2.  **정보 밀도 검증:** 이미지 내 텍스트 및 요소가 전체 영역에서 차지하는 정보 밀도가 $\text{60%}$를 초과하지 않는지 확인한다.
3.  **톤 일관성 점검:** 생성된 결과물이 지정된 `Tone (Mood)` 규칙(예: Trustworthy)에 부합하는 색상 팔레트와 구도를 따르는지 시각적으로 평가한다.

---
📊 평가: 완료 — 최종 디자인 변수 및 품질 검증 기준을 명확하게 확정하여 개발팀에게 전달할 준비를 마쳤습니다.
📝 다음 단계: 코다리에게 `Design_System_Input.json`과 Tone 규칙을 기반으로 썸네일 자동화 스크립트의 기술적 구현을 즉시 시작하도록 지시합니다.
