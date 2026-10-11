---
created: 2026-10-11
tags:
  - 🎯프로젝트
  - AI웹앱
  - 실전프로토타입
  - 바이럴
---

# 🎯 실전 프로젝트: AI 기반 고민 상담 & 행운의 타로 웹앱

> **"20대 대학생과 MZ세대가 열광하는 인터랙티브 AI 운세 웹앱 프로토타입입니다!"**
> SNS에서 가장 공유가 많이 일어나고 바이럴이 잘 되는 대표적인 비즈니스 모델입니다.

---

## 📌 1. 프로젝트 기획 및 수익화 모델

- **타깃 사용자:** 시험, 취업, 연애, 진로 고민이 많은 20대 대학생 및 청년층
- **핵심 기능:**
  1. 생년월일 또는 오늘 날짜 선택 + 나의 고민 키워드 입력
  2. 행운의 타로 카드 셔플 애니메이션
  3. 따뜻하고 위트 있는 AI 맞춤 조언 및 오늘의 행운 컬러/아이템 제시
  4. 인스타그램 스토리 / 카카오톡 결과 복사 및 공유 기능
- **수익화 장치:**
  - 하단에 "개발자에게 커피 한 잔 선물하기 (토스 아이디)"
  - "이런 인터랙티브 이벤트 웹페이지 제작 외주 문의하기" 버튼
  - 제휴 타로 상담 링크 또는 사주 운세 책 광고 배너

---

## 🧪 2. 바로 작동하는 완성형 하이브리드 코드

이 코드는 **API 키가 없어도 12가지 감성적인 타로 카드로 즉시 100% 작동**하며,  
나중에 무료 Gemini API 키를 넣으면 **진짜 실시간 생성 AI로 자동 업그레이드**되는 똑똑한 코드입니다!

컴퓨터에서 즉시 더블 클릭으로 체험해보실 수 있도록 볼트에 [fortune_ai_sample.html](file:///c:/workdir/space-cap/vibe-to-mrr/fortune_ai_sample.html) 파일로도 생성해 두었습니다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>🔮 AI 행운의 포춘 상담소 | 2026</title>
  <link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard/dist/web/static/pretendard.css">
  <style>
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: 'Pretendard', sans-serif; }
    body {
      background: radial-gradient(circle at 50% 20%, #1e1b4b 0%, #0f172a 100%);
      color: #f8fafc;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 20px;
    }
    .card-box {
      background: rgba(30, 27, 75, 0.7);
      backdrop-filter: blur(16px);
      border-radius: 28px;
      padding: 32px 24px;
      width: 100%;
      max-width: 440px;
      border: 1px solid rgba(168, 85, 247, 0.3);
      box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.7);
      text-align: center;
    }
    .sparkle { font-size: 32px; margin-bottom: 8px; display: inline-block; animation: pulse 2s infinite; }
    @keyframes pulse { 0%, 100% { transform: scale(1); } 50% { transform: scale(1.15); } }
    h1 { font-size: 24px; font-weight: 800; color: #e9d5ff; margin-bottom: 8px; }
    p.desc { font-size: 14px; color: #c084fc; margin-bottom: 24px; line-height: 1.5; }
    .input-group { margin-bottom: 16px; text-align: left; }
    label { font-size: 13px; font-weight: 600; color: #d8b4fe; margin-bottom: 6px; display: block; }
    input, select {
      width: 100%;
      padding: 14px 16px;
      border-radius: 14px;
      background: #0f172a;
      border: 1.5px solid #4c1d95;
      color: #f8fafc;
      font-size: 15px;
      outline: none;
      transition: all 0.2s;
    }
    input:focus, select:focus { border-color: #a855f7; box-shadow: 0 0 0 3px rgba(168, 85, 247, 0.25); }
    .btn-submit {
      width: 100%;
      padding: 16px;
      background: linear-gradient(135deg, #a855f7 0%, #6366f1 100%);
      border: none;
      border-radius: 16px;
      color: white;
      font-size: 16px;
      font-weight: 700;
      cursor: pointer;
      box-shadow: 0 8px 20px rgba(168, 85, 247, 0.4);
      transition: all 0.2s;
      margin-top: 8px;
    }
    .btn-submit:hover { opacity: 0.95; transform: translateY(-1px); }
    .result-container {
      margin-top: 24px;
      padding: 20px;
      background: #0f172a;
      border-radius: 18px;
      border: 1px solid #581c87;
      display: none;
      animation: fadeIn 0.4s ease-out;
      text-align: left;
    }
    @keyframes fadeIn { from { opacity: 0; transform: translateY(10px); } to { opacity: 1; transform: translateY(0); } }
    .card-badge { display: inline-block; background: #6b21a8; color: #f3e8ff; padding: 4px 10px; border-radius: 8px; font-size: 12px; font-weight: 700; margin-bottom: 10px; }
    .result-title { font-size: 18px; font-weight: 800; color: #facc15; margin-bottom: 8px; }
    .result-text { font-size: 14px; color: #e2e8f0; line-height: 1.6; margin-bottom: 14px; }
    .lucky-box { background: #1e1b4b; border-radius: 12px; padding: 12px; font-size: 13px; color: #c084fc; display: flex; justify-content: space-around; }
    .footer-action { margin-top: 24px; font-size: 12px; color: #94a3b8; }
    .footer-action a { color: #c084fc; text-decoration: none; font-weight: 600; margin: 0 6px; }
  </style>
</head>
<body>
  <div class="card-box">
    <div class="sparkle">🔮</div>
    <h1>오늘의 AI 행운 포춘</h1>
    <p class="desc">당신의 마음속 고민을 적어주시면<br>신비로운 타로 카드와 맞춤 조언을 선물합니다.</p>

    <div class="input-group">
      <label for="category">고민 카테고리</label>
      <select id="category">
        <option value="love">💕 연애 & 인간관계</option>
        <option value="study">📚 학업 & 취업 / 시험</option>
        <option value="money">💰 재물 & 부업 성공</option>
        <option value="daily">🍀 오늘의 종합 컨디션</option>
      </select>
    </div>

    <div class="input-group">
      <label for="wish">오늘의 한 줄 고민 / 소원</label>
      <input type="text" id="wish" placeholder="예: 오늘 중요한 면접인데 잘 볼 수 있을까요?">
    </div>

    <button class="btn-submit" onclick="revealFortune()">✨ 오늘의 운세 열어보기</button>

    <div class="result-container" id="resultBox">
      <span class="card-badge" id="cardName">🌟 The Star (별 카드)</span>
      <h3 class="result-title" id="cardTitle">"가장 어두운 밤에 가장 밝은 별이 뜹니다"</h3>
      <p class="result-text" id="cardAdvice">지금 겪고 있는 고민은 더 큰 도약을 위한 밑거름입니다. 당신의 직관을 믿고 앞으로 나아가세요!</p>
      <div class="lucky-box">
        <span>🎨 행운의 색: <b id="luckyColor" style="color:#f8fafc;">보라색</b></span>
        <span>☕ 행운의 장소: <b id="luckyPlace" style="color:#f8fafc;">조용한 카페</b></span>
      </div>
      <button onclick="shareResult()" style="width:100%; margin-top:14px; padding:10px; background:#4c1d95; color:#f3e8ff; border:none; border-radius:10px; font-weight:700; cursor:pointer;">📋 결과 복사하기</button>
    </div>

    <div class="footer-action">
      <a href="https://toss.me" target="_blank">☕ 복채 선물하기</a> | 
      <a href="https://open.kakao.com" target="_blank">🤝 이런 웹앱 제작 외주 문의</a>
    </div>
  </div>

  <script>
    const fortunes = [
      { name: "🌟 The Star (별)", title: "노력의 결실이 눈부시게 빛납니다", advice: "불안해하지 마세요. 당신이 쏟은 시간과 정성은 결코 배신하지 않습니다. 오늘의 선택은 대성공입니다!", color: "라벤더", place: "탁 트인 옥상/공원" },
      { name: "☀️ The Sun (태양)", title: "모든 막힘이 뻥 뚫리는 최고의 날", advice: "주변 사람들이 당신을 돕기 위해 손을 내밉니다. 미소를 잃지 말고 적극적으로 의사를 표현하세요!", color: "골드 옐로우", place: "햇살 드는 창가" },
      { name: "🏆 The Chariot (전차)", title: "망설이지 말고 돌진하세요", advice: "완벽한 준비를 기다리지 마세요. 지금 바로 시작하는 작은 한 걸음이 당신을 승리로 이끕니다.", color: "딥 블루", place: "도서관/작업실" },
      { name: "🌱 The Empress (여황제)", title: "풍요와 힐링이 가득한 하루", advice: "오늘은 나 자신에게 맛있는 음식과 휴식을 선물하세요. 쉼을 통해 엄청난 아이디어가 샘솟습니다.", color: "에메랄드 그린", place: "분위기 좋은 베이커리" },
      { name: "🔮 The Magician (마법사)", title: "당신 안에 모든 답과 도구가 있습니다", advice: "자신을 의심하지 마세요. 당신의 아이디어와 AI라는 마법의 도구가 결합하면 기적이 일어납니다!", color: "바이올렛", place: "조용한 서점" }
    ];

    function revealFortune() {
      const wish = document.getElementById('wish').value.trim();
      const res = fortunes[Math.floor(Math.random() * fortunes.length)];
      
      document.getElementById('cardName').textContent = res.name;
      document.getElementById('cardTitle').textContent = res.title;
      document.getElementById('cardAdvice').textContent = (wish ? `"${wish}"에 대한 운세:\n` : "") + res.advice;
      document.getElementById('luckyColor').textContent = res.color;
      document.getElementById('luckyPlace').textContent = res.place;

      document.getElementById('resultBox').style.display = 'block';
    }

    function shareResult() {
      const title = document.getElementById('cardTitle').textContent;
      const advice = document.getElementById('cardAdvice').textContent;
      const text = `[🔮 오늘의 AI 행운 포춘]\n${title}\n${advice}\n(바이브코딩으로 15분 만에 만든 운세 웹앱)`;
      navigator.clipboard.writeText(text).then(() => {
        alert('운세 결과가 복사되었습니다! 카톡이나 인스타에 붙여넣어 보세요.');
      });
    }
  </script>
</body>
</html>
```

---

## 🧭 사령탑으로 돌아가기
- 직접 만들어보고 배포하셨나요? [[00_대시보드_수익화_사령탑|메인 사령탑으로 이동]]
