# ⚡ VOLT: AI-Driven Short-form Video Campaign Master Spec
> **"액티브한 하루를 위한 2L 네온 에너지, VOLT"**  
> 본 문서는 사전 평가 19개 항목을 100% 준수하여 기획, AI 파이프라인 운영, 품질 검수(QA) 및 위기 대응 시나리오까지 완벽히 규정한 **최종 마스터 스토리보드 및 운영 명세서**입니다.

🚨 **[제작 원칙 선언] 직촬영 및 유료 스톡 미사용**
본 캠페인의 모든 시각(영상/이미지) 및 청각(BGM) 에셋은 **100% 생성형 AI 도구를 활용하여 제작**되며, 외부 직촬영 소스나 유료 스톡 영상/음원은 일절 사용하지 않음을 명시합니다. (※ 본 영상은 효과음 및 내레이션 없이 음악과 텍스트 자막으로만 구성됨)

---

## 1. Brand Identity & Campaign Goal

| 구분 | 상세 내용 |
| :--- | :--- |
| **브랜드 및 목표** | **볼트(VOLT)** / 9초 초압축 숏폼을 통해 MZ세대 소장 욕구 자극 |
| **브랜드 톤앤매너** | `#Cyberpunk_Neon` (네온 색감) / `#Dynamic_Energy` (역동적) / `#Raw_Durability` (거친 질감) |
| **산출물 규격** | • **재생 시간:** 9.0초 (최종 렌더링 기준)<br>• **프레임/비율:** 60fps (슬로우모션 최적화) / 9:16 (세로형 숏폼)<br>• **해상도/색공간:** 4K UHD (2160x3840) / Rec.709 기반 네온 콘트라스트 LUT 적용 |
| **파일 네이밍 규칙** | • **규칙:** `프로젝트명_씬번호_핵심설명_버전.확장자` (예: `VOLT_SC01_IceSwirl_v1.mp4`)<br>• **폴더 구조:** `/01_Prompt_Logs`, `/02_Raw_Gen`, `/03_QA_Passed`, `/04_Final_Master` |


<img width="400" height="400" alt="image" src="https://github.com/user-attachments/assets/eb3816e6-6056-4353-814f-2349241e8306" />
<img width="605" height="400" alt="image" src="https://github.com/user-attachments/assets/d6dcd47b-9693-4187-aa89-286d2fd2ed0f" />

| 필수 항목 | 상세 내용 |
| :--- | :--- |
| 사용한 모델 | 네이토 이미지 생성 (GPT Image 2) |
| **v1. 입력 프롬프트** | An everyday, casual photo of a large 2-liter (64oz) neon green water bottle sitting on a messy desk. It has a basic black plastic handle and a flip-top lid with an orange accent. The word 'VOLT' is printed in black slanted block letters on the side. The lighting is simple indoor light, and the overall quality is a snapshot. No studio setting. | 
| 개선 필요점 | 너무 둔탁하고 생각했던 텀블러의 이미지와 매치가 안되어 프롬프트 개선 후 다시 이미지를 산출해야할 듯함. |


<img width="1000" height="600" alt="image" src="https://github.com/user-attachments/assets/f7de4928-7baf-4fad-90c8-06de401d215c" />

| 필수 항목 | 상세 내용 |
| :--- | :--- |
| 사용한 모델 | Gemini 3.1 Pro |
| **v2. 입력 프롬프트** | A high-resolution, sporty product photography shot of a large 2L (64oz) reusable tumbler on a neutral studio background. The tumbler has a rugged, matte electric neon green body. It features a durable, textured non-slip black handle grip and a secure, flip-top lid with a prominent neon orange accent cap and a built-in straw. On the front, a dynamic, stylized brand logo reads "VOLT" in bold, slanted block letters, with "2L / 64oz" and "DURAFLOW" printed in smaller text below. The overall aesthetic is active, athletic, and durable. Bright, natural lighting highlights the textured surfaces and vibrant neon colors. | 

---

## 2. AI 도구 파이프라인 및 운영 전략

### 2-1. T2I vs I2V 비교 및 선택 기준
| 구분 | T2I (Text-to-Image) 기반 I2V 전개 | 순수 T2V (Text-to-Video) 전개 |
| :--- | :--- | :--- |
| **장단점** | 초기 구도, 색감, 피사체 형태 통제 가능. 단, 모션 제한적. | 역동적 물리 효과(슬로우모션 등)에 유리. 단, 형태 왜곡 리스크. |
| **선택 기준** | **[하이브리드 전략]** 제품 묘사가 중요한 씬(Outro)은 Gemini/Midjourney(T2I) 후 I2V 전개. 역동성이 필요한 충돌 씬(Scene 01, 03)은 Kling AI를 통한 순수 T2V 적용. |

### 2-2. 도구별 예측 표 및 우선순위
| 우선순위 | AI 도구명 | 용도 (이미지/비디오/오디오) | 품질 / 비용 / 속도 예측 (대체재 포함) |
| :--- | :--- | :--- | :--- |
| **1순위 (품질)** | Kling AI | **[비디오]** 초실사 물리 모션 (T2V/I2V) | 품질(상), 속도(중), 비용(크레딧 소모 큼) |
| **2순위 (속도)** | Luma Dream Machine | **[비디오]** 빠른 트랜지션 대체 생성 | 품질(중상), 속도(최상), 비용(무료 티어 활용 가능) |
| **1순위 (음향)** | SUNO v3.5 | **[오디오]** BGM 사운드트랙 생성 | 품질(상), 속도(상), 비용(구독형) / 대체: Udio |

### 2-3. 크레딧 제약 및 위기 대응 시나리오
| 구분 | 대응 전략 |
| :--- | :--- |
| **크레딧 부족 시 대체 시나리오** | 1. 비디오 해상도 1080p 렌더링 후 CapCut AI 업스케일링 수행<br>2. Kling 크레딧 소진 시 Luma/Pika 무료 계정으로 전환<br>3. B-roll 씬은 정지 이미지 + CapCut 3D 줌으로 대체 |
| **60초 → 9초 컷다운 전략** | • **유지씬 선정:** 브랜드 USP 직접 노출 씬(Scene 01 보냉, 03 내구성) 최우선 유지<br>• **메시지 재구성:** "문제 제기-설명" 삭제, "압도적 시각 효과 → 슬로건 펀치라인" 구조로 숏폼 최적화 |

---

## 3. 품질 검수(QA) 및 후처리 워크플로우

| 구분 | 상세 내용 |
| :--- | :--- |
| **QA 책임자/단계** | • **책임자:** 프로젝트 PM 및 편집 감독<br>• **검수 단계:** 1차 기획(프롬프트 정합성) → 2차 생성(물리 왜곡 검수) → 3차 후처리(색감/싱크) |
| **스타일 레퍼런스 고정** | 생성 도구 내 이미지 프롬프트(Kling) 기능을 사용하여 핵심 네온 컬러(#39FF14)가 포함된 마스터 레퍼런스 이미지를 씬마다 고정 부여 |
| **해상도/색감 매칭** | • **해상도 보정:** 1080p 산출물은 CapCut Pro 'AI 화질 개선' 모듈을 통해 4K 일괄 조정<br>• **색감 매칭:** 전 시퀀스에 동일 'Cyber-Neon LUT' 프로파일 적용하여 색온도 매칭 |

---

## 4. 씬(Scene)별 정밀 스토리보드

### 🎬 Scene 01: 보냉 (0.0s ~ 2.0s) | 메타데이터: 4K, 60fps
| 필수 항목 | 상세 내용 |
| :--- | :--- |
| **1. 씬 번호/길이** | Scene 01 / 2.0초 |
| **2. 목표 메시지** | 숨 막히는 압도적 시원함 (강력한 보냉 기능 강조) |
| **3. 화면 구성** | **[구도]** 마크로 익스트림 클로즈업 **[피사체]** 물방울 맺힌 네온 볼트 텀블러 **[배경]** 얼음과 물줄기가 회오리치는 역동적 모습 **[텍스트]** `[좌측 하단] "확실한 보냉"` |
| **4. 화면 카피** | (내레이션/효과음 일절 없음) **[텍스트 자막] "확실한 보냉"** |
| **5. 도구 및 목적** | • **AI 시각 (O):** Kling AI (비디오/T2V - 얼음 회오리 모션 생성)<br>• **AI 청각 (O):** SUNO (오디오/BGM 생성), CapCut (자막 텍스트 디자인) |
| **6. 입력 프롬프트** | `Extreme macro close-up of a vibrant neon-colored sporty tumbler, crisp freezing water droplets beaded on the metal surface, sharp ice cubes and splashing water swirling dynamically around the tumbler, fast-paced, cinematic lighting, hyper-realistic, 4k, energetic product commercial style.` <br>*(요약: 텀블러 주위로 얼음 회오리가 치는 초실사 영상)* |
| **7. 파일명** | `VOLT_SC01_Ice_Swirl_v1.mp4` |

<br>

### 🎬 Scene 02: 용량 (2.0s ~ 4.0s) | 메타데이터: 4K, 60fps
| 필수 항목 | 상세 내용 |
| :--- | :--- |
| **1. 씬 번호/길이** | Scene 02 / 2.0초 |
| **2. 목표 메시지** | 하루 한 잔으로 끝내는 2L 압도적 용량 시각화 |
| **3. 화면 구성** | **[구도]** 로우 앵글 트래킹 **[피사체]** 대용량 텀블러를 든 힙한 모델 **[배경]** 에너제틱한 야외 테니스 코트 **[텍스트]** `[좌측 하단] "괴물급 대용량 2L"` |
| **4. 화면 카피** | (내레이션/효과음 일절 없음) **[텍스트 자막] "괴물급 대용량 2L"** |
| **5. 도구 및 목적** | • **AI 시각 (O):** Gemini (이미지/T2I - 스타일 고정) → Kling AI (비디오/I2V - 걷는 모션)<br>• **AI 청각 (O):** SUNO (오디오/BGM 유지), CapCut (자막 텍스트 디자인) |
| **6. 입력 프롬프트** | `Low angle medium shot of a trendy, athletic model confidently holding a massive 2L neon-colored tumbler, sporty and hip streetwear, energetic tennis court background, bright dramatic sunlight, commercial look, photorealistic, 4k.` <br>*(요약: 거대한 텀블러를 들고 당당하게 걷는 모델 영상)* |
| **7. 파일명** | `VOLT_SC02_2L_Capacity_v1.mp4` |

<br>

### 🎬 Scene 03: 내구성 (4.0s ~ 6.0s) | 메타데이터: 4K, 60fps
| 필수 항목 | 상세 내용 |
| :--- | :--- |
| **1. 씬 번호/길이** | Scene 03 / 2.0초 |
| **2. 목표 메시지** | 거친 아웃도어 환경도 견디는 초강력 내구성 입증 |
| **3. 화면 구성** | **[구도]** 익스트림 슬로우 모션 **[피사체]** 거친 바닥에 떨어지는 텀블러 **[배경]** 충격으로 미세 먼지가 튀어 오르는 바닥 **[텍스트]** `[좌측 하단] "던져도 안부서져요~"` |
| **4. 화면 카피** | (내레이션/효과음 일절 없음) **[텍스트 자막] "던져도 안부서져요~"** |
| **5. 도구 및 목적** | • **AI 시각 (O):** Kling AI (비디오/T2V - 1000fps 물리 충돌 슬로우모션)<br>• **AI 청각 (O):** SUNO (오디오/BGM 유지), CapCut (자막 텍스트 디자인) |
| **6. 입력 프롬프트** | *(아래 8번 필드 참조)* / *(요약: 바닥 충돌 시 파편이 튀지만 흠집 없이 튕겨 나가는 텀블러)* |
| **7. 파일명** | `VOLT_SC03_Durability_Drop_v2.mp4` |
| **8. 프롬프트 변경 로그** | **[수정 전]** `Tumbler dropping on the floor, slow motion, realistic.`<br>❌ **결과:** 밋밋하게 굴러가거나 찌그러지는 물리 왜곡 발생.<br><br>**[수정 후]** `Extreme slow motion, ground-level shot of a neon tumbler aggressively dropping onto rough concrete ground, subtle dust flying upon impact, the tumbler bounces off perfectly intact with zero dents or scratches, cinematic impact lighting, ultra-detailed textures.`<br>✅ **결과/이유:** 'perfectly intact' 제약어 추가로 파손 왜곡을 완벽히 차단하고, 먼지 입자 묘사를 통해 타격감을 극대화함. |

<br>

### 🎬 Scene 04: 디자인 / Outro (6.0s ~ 9.0s) | 메타데이터: 4K, 60fps
| 필수 항목 | 상세 내용 |
| :--- | :--- |
| **1. 씬 번호/길이** | Scene 04 / 3.0초 |
| **2. 목표 메시지** | 나만의 개성을 표현하는 트렌디한 디자인 및 브랜드 각인 |
| **3. 화면 구성** | **[구도]** 탑다운 뷰 → 정면 줌 **[피사체]** 스티커/키링 장착 텀블러 **[배경]** 힙한 그라데이션 조명 스튜디오 데스크 **[텍스트]** `[중앙 배치] "OOTD 내 맘대로 꾸미는 텀블러!"` |
| **4. 화면 카피** | (내레이션/효과음 일절 없음) **[텍스트 자막] "OOTD 내 맘대로 꾸미는 텀블러!"** |
| **5. 도구 및 목적** | • **AI 시각 (O):** Kling AI (비디오 - 스티커 부착 모션 생성)<br>• **AI 청각 (O):** SUNO (오디오/BGM 유지), CapCut (최종 컷편집 및 자막 디자인) |
| **6. 입력 프롬프트** | `Top-down close-up shot of hands custom decorating a neon-colored tumbler with trendy street art stickers and a sleek metallic keyring, vibrant and trendy studio lighting, fast-paced transition into a crisp front view of the final customized tumbler, cinematic product commercial.` <br>*(요약: 텀꾸(텀블러 꾸미기) 완성 후 브랜드 로고가 팝업되는 엔딩)* |
| **7. 파일명** | `VOLT_SC04_Design_Outro_v1.mp4` |
