# 🎨 Designer — 썸네일 자동화를 위한 최종 시각 자료 프롬프트와 입력 규칙을 'Design_System_Input.json' 및 Tone(Mood) 규칙을 기반으로 완벽하게 구체화하여 개발팀에게 전달할 준비를 하라.

🎨 Designer: 작업 시작합니다.

요청하신 썸네일 자동화를 위한 최종 시각 자료 프롬프트와 입력 규칙을 'Design_System_Input.json' 및 Tone(Mood) 규칙을 기반으로 개발팀에게 전달할 수 있도록 완벽하게 구체화하여 정리했습니다. 이 내용은 모든 디자인 시스템의 핵심 변수를 명확히 정의하여, 개발자가 AI 스크립트를 구현하는 데 필요한 모든 제약 조건과 스타일 가이드를 제공합니다.

---

# 🎨 썸네일 자동화 시스템 최종 입력 규칙 및 프롬프트 (개발팀 전달용)

## 1. 디자인 시스템 입력 파일: `Design_System_Input.json` (구조 및 레이아웃 정의)

이 JSON 파일은 모든 썸네일의 기본 구조와 레이아웃 좌표를 정의합니다.

```json
{
  "system_name": "DAON Thumbnail System",
  "base_template": {
    "aspect_ratio": "16:9",
    "safe_zone": {
      "width_percent": 0.8,
      "height_percent": 0.9
    }
  },
  "layout_templates": [
    {
      "template_id": "T_FOCUS_BLUE",
      "style_name": "Trust & Authority (DAON Blue)",
      "color_palette": {
        "background": "#1A237E",       // DAON Deep Blue (신뢰감 강조)
        "primary_text": "#FFFFFF",    // White for high contrast
        "accent_color": "#FFC107",     // Amber/Gold for CTA emphasis
        "secondary_text": "#B0BEC5"    // Light Gray for supporting info
      },
      "layout": {
        "elements": [
          {"type": "TitleBlock", "position": {"x": 50, "y": 50, "width": 800, "height": 150}},
          {"type": "VisualArea", "position": {"x": 0, "y": 200, "width": 1000, "height": 600}, "style": "Overlay"},
          {"type": "CTA_Box", "position": {"x": 50, "y": 850, "width": 700, "height": 100}, "style": "AccentColor"}
        ],
        "typography": {
          "font_primary": "Pretendard Bold", // 고딕 계열, 시각적 임팩트 중시
          "font_secondary": "Pretendard Regular"
        }
      }
    },
    {
      "template_id": "T_LIFESTYLE_LIGHT",
      "style_name": "Light & Insight (Soft Contrast)",
      "color_palette": {
        "background": "#F5F5F5",       // Light Gray Background
        "primary_text": "#212121",    // Near Black for readability
        "accent_color": "#4FC3F7",     // Light Blue Accent
        "secondary_text": "#607D8B"    // Slate Gray
      },
      "layout": {
        "elements": [
          {"type": "TitleBlock", "position": {"x": 50, "y": 50, "width": 800, "height": 150}},
          {"type": "VisualArea", "position": {"x": 0, "y": 200, "width": 1000, "height": 600}, "style": "ContentFocus"},
          {"type": "CTA_Box", "position": {"x": 50, "y": 850, "width": 700, "height": 100}, "style": "AccentColor"}
        ],
        "typography": {
          "font_primary": "Noto Sans KR Bold", // 가독성 및 정보 전달 중시
          "font_secondary": "Noto Sans KR Regular"
        }
      }
    }
  ]
}
```

## 2. 톤(Mood) 규칙 파일: `Tone(Mood).json` (스타일 변형 규칙 정의)

이 파일은 AI가 이미지 생성 시 적용해야 할 감성적/구조적 변형 규칙을 정의합니다.

```json
{
  "mood_rules": [
    {
      "style_name": "Trust & Authority (DAON Blue)",
      "visual_focus": "Professional, Trustworthy, High-Tech",
      "composition_rule": "Strong vertical alignment. Use deep blues and high-contrast white text. Visual elements must appear structured and organized.",
      "image_style": "Cinematic lighting, sharp focus, clean vector lines."
    },
    {
      "style_name": "Light & Insight (Soft Contrast)",
      "visual_focus": "Casual, Insightful, Approachable",
      "composition_rule": "Balanced composition. Use soft gradients and ample negative space. Focus on organic shapes and natural light effects.",
      "image_style": "Soft focus, warm tones, subtle film grain effect."
    }
  ],
  "readability_loop": {
    "metric": "Contrast Ratio > 4.5:1 for text against background",
    "tolerance": "Accent colors must not exceed 20% of the total canvas area to maintain focus on the main message."
  }
}
```

## 3. 최종 지침 및 적용 규칙 요약 (개발자 참고용)

1.  **핵심 원칙:** 모든 디자인은 **신뢰감(Trust)** 또는 **통찰력(Insight)** 중 하나의 명확한 감성 목표를 따라야 합니다.
2.  **컬러 시스템:** `T_FOCUS_BLUE`는 DAON의 핵심 신뢰도를 나타내며, `#1A237E` (Deep Blue)를 기본 배경으로 사용합니다. `T_LIFESTYLE_LIGHT`는 접근성과 통찰력을 위해 밝은 톤을 사용합니다.
3.  **타이포그래피:**
    *   신뢰감 강조 시: **Pretendard Bold** (강한 존재감)
    *   통찰력 강조 시: **Noto Sans KR Bold** (명확하고 읽기 쉬움)
4.  **가독성 검증 루프 적용:** 생성된 이미지에서 텍스트 대비(Contrast Ratio)가 최소 4.5:1을 충족하는지, 그리고 강조 색상(`Accent Color`)이 전체 영역의 20%를 넘지 않는지 자동 검증해야 합니다.

---
📊 평가: 완료 — 요청하신 최종 시각 자료 프롬프트와 입력 규칙이 시스템의 일관성과 개발 요구사항에 맞게 구체화되어 전달되었습니다.
📝 다음 단계: 개발팀(코다리)에게 위 JSON 파일과 지침을 즉시 전달하고, 썸네일 자동화 스크립트 구현 착수를 요청합니다.
