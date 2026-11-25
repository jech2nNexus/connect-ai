# 🎨 Designer — 썸네일 자동화를 위한 최종 시각 자료 프롬프트와 입력 규칙을 'Design_System_Input.json' 및 Tone(Mood) 규칙을 기반으로, 개발팀(코다리)이 즉시 실행할 수 있도록 완벽하게 구체화하여 전달하라.

🎨 Designer: 작업 시작합니다.

요청하신 대로 썸네일 자동화를 위한 최종 시각 자료 프롬프트와 입력 규칙을 'Design_System_Input.json' 및 Tone(Mood) 규칙을 기반으로 개발팀(코다리)이 즉시 실행할 수 있도록 완벽하게 구체화하여 전달합니다.

이 내용은 `sessions/2026-11-25T05-58/designer.md`의 최종 검토 내용을 기반으로 확정되었습니다.

---

# 🖼️ Thumbnail Automation System: 최종 시각 자료 프롬프트 및 입력 규칙 (개발용)

## 1. Design System Input (Design_System_Input.json)
이 섹션은 모든 디자인 요소의 구조적 제약 조건과 기본값을 정의합니다. 자동화 스크립트가 따라야 할 필수 JSON 형식입니다.

```json
{
  "system_name": "DAON_Thumbnail_Generator",
  "base_template": "standard_video_thumbnail_v1",
  "aspect_ratio": "16:9",
  "color_palette": {
    "primary_brand": "#007BFF",        // DAON 블루 톤 (신뢰감 강조)
    "secondary_accent": "#FFC107",      // 보조 강조색 (주의/혜택 강조)
    "text_color_light": "#FFFFFF",
    "text_color_dark": "#1A1A1A"
  },
  "typography": {
    "font_family_primary": "Pretendard", // 기본 폰트
    "font_family_headline": "Black",    // 제목용 폰트 (강조)
    "font_family_body": "Noto Sans KR"  // 본문 및 설명용 폰트
  },
  "layout_structure": {
    "elements": [
      {"name": "Background", "style": "Gradient", "color": ["#007BFF", "#4A90E2"]},
      {"name": "Headline_Area", "position": "Top_Center", "priority": 1, "font_size_scale": 1.5},
      {"name": "Main_Visual_Area", "position": "Center_Left", "priority": 2, "style": "Image_Overlay"},
      {"name": "Text_Overlay_Box", "position": "Bottom_Right", "padding": "20px", "background_color": "#1A1A1A", "border_radius": "8px"}
    ],
    "text_placement_rules": [
      {"element": "Headline_Area", "rule": "Max_Lines: 3, Font: Headline, Color: White"},
      {"element": "Text_Overlay_Box", "rule": "Content: Title/Key Benefit. Font: Body, Color: White"}
    ]
  },
  "output_constraints": {
    "min_contrast_ratio": 4.5, // 최소 색상 대비 비율 (가독성 검증 루프 기준)
    "text_density_limit": 0.6, // 텍스트 밀도 제한 (과도한 정보 방지)
    "visual_balance_metric": "Rule_A" // 시각적 균형 측정 규칙 적용
  }
}
```

## 2. Tone(Mood) Rules (감성 및 스타일 변형 규칙)
이 섹션은 영상의 주제와 타겟 청중에 따라 최종 결과물의 감성적 톤을 조정하는 규칙입니다.

| Mood Category | Target Audience | Color Bias | Typography Style | Layout Preference | Key Constraint |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Trustworthy (신뢰)** | AI 시대의 올바른 팩트정보를 원하는 국민 | Primary Brand Blue (`#007BFF`) 중심 | 명확하고 간결한 Sans-Serif (Black/Noto Sans) | 좌측 배치, 정보 위주 레이아웃 | 고대비(Contrast) 유지 필수 |
| **Exciting (흥미)** | 트렌드에 민감하며 빠른 변화를 선호하는 사용자 | Secondary Accent Yellow (`#FFC107`) 강조 | 굵고 역동적인 Headline 폰트 사용 | 중앙 집중형, 시각적 요소 극대화 | 움직임(Motion)과 대비 강조 |
| **Calm (차분)** | 심층적인 학습 및 분석을 선호하는 사용자 | Neutral Grays/Blues (`#1A1A1A`, `#4A90E2`) | 세리프 계열 또는 부드러운 Sans-Serif | 여백(Whitespace) 극대화, 미니멀리즘 | 텍스트 밀도 최소화 (Text Density $\le 0.5$) |

## 3. 가독성 검증 루프 (Readability Validation Loop)
자동 생성된 이미지의 최종 품질을 보장하기 위한 측정 기준입니다. 스크립트가 결과물을 생성한 후 이 기준에 따라 자체 검증해야 합니다.

1.  **Contrast Check:** 모든 텍스트와 배경 간의 최소 색상 대비 비율(CR)이 **4.5 이상**인지 확인한다. (JSON 내 `min_contrast_ratio` 준수)
2.  **Information Density Check:** 이미지 내 전체 픽셀당 텍스트 밀도(Text Density)가 **0.6 이하**로 유지되는지 측정한다.
3.  **Visual Balance Check:** 주요 시각 요소(Main Visual Area)와 텍스트 블록 간의 시선 흐름이 자연스럽고, 핵심 메시지가 중앙에 효과적으로 배치되었는지 `Rule_A`에 따라 평가한다.

---

**✅ 코다리에게 전달 사항:**
위 JSON 및 Tone 규칙을 기반으로, 사용자가 입력하는 영상 주제(Input Prompt)를 분석하여 위 3단계의 모든 제약 조건을 만족시키는 최종 시각 자료 프롬프트와 레이아웃 변수를 자동으로 생성하는 스크립트를 즉시 개발하십시오.

📊 평가: 완료 — 요청된 내용이 구체적인 JSON 및 규칙 세트로 완벽하게 정리되어 개발팀에게 전달되었습니다.
📝 다음 단계: 코다리에게 썸네일 자동화 스크립트의 구현을 시작하도록 지시합니다.
