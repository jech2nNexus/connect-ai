# 🎨 Designer — 썸네일 자동화 시스템 구축이라는 현재 가장 필요한 목표 달성을 위해, 개발팀(코다리)이 즉시 실행할 수 있도록 최종 시각 자료 프롬프트와 입력 규칙을 명확하게 정리하여 전달할 준비를 하라.

🎨 Designer: 작업 시작합니다.

요청하신 대로 썸네일 자동화 시스템 구축을 위해 개발팀(코다리)이 즉시 실행할 수 있도록 최종 시각 자료 프롬프트와 입력 규칙을 명확하게 정리하여 전달하겠습니다. 기존 메모리에서 확정된 모든 디자인 시스템 입력값과 톤(Mood) 기반 변형 규칙을 통합하여 최종 산출물을 준비합니다.

다음은 개발팀에게 전달될 **최종 디자인 시스템 및 자동화 규칙**입니다.

---

## 🖼️ 썸네일 자동화 시스템 최종 요구사항 (개발자용)

이 문서는 `Design_System_Input.json`과 `Tone(Mood)` 규칙을 기반으로 하며, AI가 이미지 변형을 수행할 때 따라야 할 모든 구체적인 입력값과 제약 조건을 정의합니다.

### 1. 디자인 시스템 입력 (`Design_System_Input.json` 구조)

이 JSON 파일은 자동화 스크립트의 핵심 입력 변수로 사용됩니다.

```json
{
  "brand_color": {
    "primary": "#3b82f6",   // DAON 브랜드 메인 블루 (Primary)
    "secondary": "#1e40af", // DAON 서브 블루 (Secondary)
    "accent": "#f59e0b",     // 강조 색상 (Accent)
    "background_dark": "#111827", // 어두운 배경
    "text_light": "#ffffff"  // 밝은 텍스트
  },
  "typography": {
    "font_heading": "Pretendard Bold", // 제목용 폰트 (굵게, 시각적 임팩트)
    "font_body": "Pretendard Regular", // 본문 및 설명용 폰트 (가독성 최우선)
    "line_height_ratio": 1.35     // 줄 간격 비율 (높은 가독성을 위해)
  },
  "layout_structure": {
    "aspect_ratio": "16:9",       // 표준 유튜브 썸네일 비율
    "text_placement": {
      "main_title": {"position": "top-left", "font_size_scale": 1.5, "color": "#ffffff"},
      "secondary_text": {"position": "bottom-right", "font_size_scale": 0.8, "color": "#fef3c7"}
    },
    "element_spacing": {
      "padding_from_edge": 15,     // 이미지 가장자리에서 픽셀 여백
      "text_margin_to_edge": 20    // 텍스트와 이미지 경계 간 마진
    }
  },
  "visual_style": {
    "texture_overlay": "Subtle Noise/Grain", // 미세한 노이즈 또는 그레인 오버레이 적용 (톤 조절용)
    "color_contrast_target": 0.75, // 목표 색상 대비율 (0.0 ~ 1.0, 0.75 권장)
    "saturation_level": 1.1      // 채도 조정 (약간 높여 생동감 부여)
  }
}
```

### 2. 톤 및 무드 변형 규칙 (`Tone(Mood)` 기반 변형 로직)

AI가 이미지의 최종 결과물을 생성할 때 적용해야 할 감성적, 스타일적 지침입니다. 이 규칙은 **가독성 검증 루프**를 통과하도록 설계되었습니다.

| Mood Category | Description | Key Visual Directives (AI 지시사항) | Color/Style Constraints |
| :--- | :--- | :--- | :--- |
| **A. Fact-Based (팩트 기반)** | 정보 전달의 정확성과 명료성이 최우선. | "최소한의 시각적 장식을 사용하고, 텍스트와 핵심 데이터에만 집중하라. 복잡한 배경은 배제한다." | 고대비(Contrast)를 최대화하여 텍스트 가독성 100% 보장. 채도 낮게 유지 (Saturation < 1.0). |
| **B. Engaging & Energetic (몰입 및 활력)** | 시청자의 즉각적인 클릭을 유도하는 역동적인 느낌. | "강렬한 색상 대비(Accent Color 사용)와 역동적인 구도를 활용하라. 시선이 중앙의 핵심 요소로 집중되도록 흐름을 설계하라." | Accent Color(`f59e0b`)를 주요 강조 요소로 사용. 채도 높임 (Saturation > 1.2). |
| **C. Calm & Trustworthy (차분함 및 신뢰)** | 전문성과 깊이를 전달하는 안정적인 느낌. | "부드러운 그라데이션과 낮은 채도의 색상 팔레트를 사용하여 깊이감을 부여하라. 그림자(Shadow)는 미묘하게만 사용한다." | Primary/Secondary Color의 부드러운 그라데이션 적용. 명암 대비를 낮춤 (Contrast < 0.8). |

### 3. 가독성 검증 루프 (Validation Loop)

자동화 시스템이 생성한 결과물을 자체적으로 평가하는 단계입니다.

1.  **대비율 측정:** 최종 이미지 내 모든 텍스트 영역의 평균 대비율($C_{avg}$)을 측정한다.
    *   **Pass Condition:** $C_{avg} \ge 0.75$ (최소 요구치)
2.  **포화도 검증:** 전체 이미지의 평균 채도($S_{avg}$)를 측정한다.
    *   **Pass Condition:** $S_{avg}$는 `Tone(Mood)`에 따라 허용 범위 내에서 변동해야 함 (A: 낮게, B: 높게, C: 중간).
3.  **구조 일치 검증:** 텍스트 배치(`Layout_Structure`)가 설정된 좌표와 `%` 오차 범위($\pm5\%$) 내에 있는지 확인한다.

---

이 최종 규칙을 코다리에게 전달하면 개발팀은 이 명세에 맞춰 썸네일 자동화 스크립트의 구현 및 테스트를 즉시 시작할 수 있습니다.

📊 평가: 완료 — 요청된 목표(최종 시각 자료 프롬프트와 입력 규칙 정리)가 구체적인 형식으로 산출됨
📝 다음 단계: 개발팀에게 최종 요구사항을 전달하고, 코다리에게 스크립트 구현 착수를 지시
