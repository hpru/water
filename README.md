<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>جدول ومستوى الماء</title>
<style>
  :root {
      --primary-color: #00796B;
      --secondary-color: #8BC34A;
      --accent-color: #FFC107;
      --background-light: #F9FBE7;
      --background-medium: #DCEDC8;
      --text-dark: #212121;
      --text-light: #fff;
      --card-bg: #fff;
      --past-color: #B71C1C;
      --warning-color: #FF5722;
      --success-color: #4CAF50;
      --info-color: #2196F3;
  }
  
  body {
      font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
      background: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
      margin: 0;
      padding: 10px;
      color: var(--text-dark);
      line-height: 1.6;
  }
  
  .emergency-alert {
      max-width: 900px;
      margin: 20px auto;
      padding: 25px;
      border-radius: 16px;
      background: linear-gradient(135deg, #FFF3E0, #FFECB3);
      border: 3px solid #FF5722;
      color: #D84315;
      font-size: 22px;
      font-weight: bold;
      text-align: center;
      box-shadow: 0 8px 25px rgba(255, 87, 34, 0.3);
      animation: pulse-alert 2s infinite;
      position: relative;
      overflow: hidden;
  }
  
  .emergency-alert::before {
      content: "⚠️ حساس قياس مستوى الماء لا يعمل";
      display: block;
      font-size: 28px;
  }
  
  @keyframes pulse-alert {
      0%, 100% { transform: scale(1); }
      50% { transform: scale(1.02); }
  }
  
  .section-container {
      max-width: 900px;
      margin: 20px auto;
      padding: 20px;
      border-radius: 16px;
      box-shadow: 0 8px 25px rgba(0,0,0,0.1);
      background-color: var(--card-bg);
      transition: transform 0.3s ease, box-shadow 0.3s ease;
  }
  
  .section-container:hover {
      box-shadow: 0 10px 30px rgba(0,0,0,0.15);
      transform: translateY(-2px);
  }
  
  h1, h2 {
      text-align: center;
      margin-bottom: 25px;
      color: var(--primary-color);
      font-weight: 700;
  }

  .tank-container {
      position: relative;
      width: 180px;
      margin: 30px auto;
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 6px 15px rgba(0,0,0,0.2);
  }
  
  .tank-image {
      width: 100%;
      display: block;
      border-radius: 12px;
      filter: brightness(1.05);
  }
  
  .water-level {
      position: absolute;
      bottom: 0;
      width: 100%;
      height: 0%;
      background: linear-gradient(to top, rgba(33,150,243,0.9), rgba(33,150,243,0.6));
      border-radius: 0 0 12px 12px;
      transition: height 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
      z-index: 2;
  }
  
  .water-stats {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      gap: 20px;
      margin: 30px 0;
  }
  
  .stat-card {
      background: linear-gradient(145deg, #ffffff, #f0f0f0);
      padding: 20px;
      border-radius: 12px;
      text-align: center;
      border-left: 5px solid var(--primary-color);
      box-shadow: 0 4px 12px rgba(0,0,0,0.1);
      transition: all 0.3s ease;
  }
  
  .stat-card:hover {
      transform: translateY(-5px);
      box-shadow: 0 8px 20px rgba(0,0,0,0.15);
  }
  
  .stat-value {
      font-size: 1.8em;
      font-weight: 800;
      color: var(--primary-color);
      margin-bottom: 5px;
  }
  
  .stat-label {
      font-size: 0.95em;
      color: #666;
      margin-top: 8px;
      font-weight: 600;
  }
  
  .water-controls {
      display: flex;
      gap: 15px;
      margin-top: 25px;
  }
  
  .water-controls button {
      flex: 1;
      padding: 14px;
      font-size: 16px;
      border: none;
      border-radius: 10px;
      background: linear-gradient(to right, var(--primary-color), #00695C);
      color: white;
      font-weight: bold;
      cursor: pointer;
  }

  .maintenance-box {
      text-align: center;
      padding: 40px 20px;
      font-size: 24px;
      font-weight: bold;
      color: #0277BD;
      background: #E1F5FE;
      border: 2px dashed #03A9F4;
      border-radius: 12px;
  }

  .unauth-box {
      text-align: center;
      padding: 40px 20px;
      font-size: 24px;
      font-weight: bold;
      color: #D84315;
      background: #FFF3E0;
      border: 2px dashed #FF5722;
      border-radius: 12px;
  }

  .person-box {
      text-align: center;
      margin: 20px 0;
      padding: 20px;
      border-radius: 12px;
      background: linear-gradient(135deg, var(--background-medium), #C5E1A5);
      font-size: 22px;
      font-weight: bold;
      box-shadow: 0 5px 15px rgba(139,195,74,0.3);
      border: 2px dashed var(--secondary-color);
  }
  
  .person-name {
      color: var(--primary-color);
  }
  
  .active-indicator {
      display: inline-block;
      width: 10px;
      height: 10px;
      background-color: #4CAF50;
      border-radius: 50%;
      animation: pulse 2s infinite;
      margin-right: 8px;
      vertical-align: middle;
  }
  
  @keyframes pulse {
      0% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(76, 175, 80, 0.7); }
      70% { transform: scale(1); box-shadow: 0 0 0 6px rgba(76, 175, 80, 0); }
      100% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(76, 175, 80, 0); }
  }
  
  .countdown-container {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-bottom: 25px;
  }
  
  .countdown-circle {
      position: relative;
      width: 140px;
      height: 140px;
      border-radius: 50%;
      background: conic-gradient(var(--primary-color) 0%, #e0e0e0 0%);
      display: flex;
      align-items: center;
      justify-content: center;
      margin-bottom: 15px;
      box-shadow: 0 8px 20px rgba(0, 121, 107, 0.3);
  }
  
  #timer-text {
      position: relative;
      font-size: 24px;
      font-weight: bold;
      color: var(--primary-color);
      z-index: 1;
  }
  
  .countdown-label {
      font-size: 16px;
      color: var(--text-dark);
      margin-top: -8px;
      font-weight: bold;
      background: rgba(139,195,74,0.1);
      padding: 5px 15px;
      border-radius: 20px;
  }
  
  table {
      width: 100%;
      border-collapse: separate;
      border-spacing: 0;
      margin: 20px 0;
      font-size: 14px;
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 6px 15px rgba(0,0,0,0.1);
  }
  
  th, td {
      padding: 14px 12px;
      border: 1px solid #E0E0E0;
      text-align: center;
  }
  
  th {
      background: linear-gradient(to bottom, var(--primary-color), #00695C);
      color: var(--text-light);
      font-weight: 700;
  }
  
  tr:nth-child(even) { background-color: #F9F9F9; }
  tr:hover { background-color: #F0F7FF; }
  
  /* ============================================
     تلوين اليوم الحالي بالكامل (دائرة على اليوم)
     ============================================ */
  tr.today-row {
      background: linear-gradient(to right, #FFD54F, #FFC107) !important;
      font-weight: bold;
      color: #4E342E !important;
      border: 3px solid #FF6F00;
      box-shadow: 0 0 20px rgba(255, 193, 7, 0.5);
      border-radius: 12px;
  }
  
  tr.today-row td {
      color: #4E342E !important;
      font-weight: 700;
  }
  
  tr.today-row .detail-btn {
      background: linear-gradient(to bottom, #4E342E, #3E2723);
      color: #FFD54F;
  }
  
  tr.selected {
      background: linear-gradient(to right, var(--accent-color), #FFB300);
      font-weight: bold;
      color: #5D4037;
  }
  
  tr.fill-period {
      background: linear-gradient(to right, #E1F5FE, #B3E5FC);
      color: #01579B;
  }
  
  tr.past {
      color: var(--past-color);
      background-color: #FFEBEE;
      text-decoration: line-through;
  }
  
  tr.emergency {
      background: linear-gradient(to right, #FFF3E0, #FFE082);
      font-weight: bold;
      color: #E65100;
  }
  
  .detail-btn {
      background: linear-gradient(to bottom, var(--primary-color), #00695C);
      color: white;
      border: none;
      padding: 8px 16px;
      border-radius: 8px;
      cursor: pointer;
      font-size: 13px;
      margin-top: 5px;
      font-weight: 600;
  }
  
  #detailsModal {
      display: none;
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(0,0,0,0.7);
      justify-content: center; align-items: center;
      z-index: 1000;
      backdrop-filter: blur(3px);
  }
  
  #detailsModalContent {
      background: white;
      padding: 30px;
      border-radius: 16px;
      width: 500px;
      max-width: 90vw;
      text-align: right;
      position: relative;
  }
  
  #closeModal {
      position: absolute;
      top: 15px; left: 20px;
      cursor: pointer;
      font-size: 28px;
      font-weight: bold;
  }
  
  .modal-row {
      display: flex;
      flex-direction: column;
      margin-bottom: 15px;
      border-bottom: 1px solid #eee;
      padding-bottom: 12px;
  }
  
  .modal-label {
      font-weight: 700;
      color: var(--primary-color);
      margin-bottom: 8px;
  }
  
  .modal-value {
      background: #f9f9f9;
      padding: 10px 15px;
      border-radius: 8px;
      border: 1px solid #e0e0e0;
  }
  
  .add-reminder-btn {
      width: 100%;
      padding: 14px;
      background: linear-gradient(to right, var(--info-color), #1976D2);
      color: white;
      border: none;
      border-radius: 10px;
      font-size: 16px;
      font-weight: bold;
      cursor: pointer;
  }
  
  .new-site-link {
      border: 2px solid var(--warning-color);
      padding: 15px;
      border-radius: 10px;
      background-color: #FFF3E0;
      color: #D84315;
      font-weight: bold;
      text-align: center;
      margin: 20px auto;
      max-width: 900px;
  }
  
  .new-site-link a {
      display: inline-block;
      background: linear-gradient(to right, #0d6efd, #0b5ed7);
      color: #fff;
      padding: 15px 30px;
      border-radius: 12px;
      font-weight: bold;
      text-decoration: none;
      margin-top: 10px;
  }
  
  @media (max-width: 768px) {
      .water-stats { grid-template-columns: repeat(2, 1fr); }
  }
</style>
</head>
<body>

<div class="emergency-alert"></div>

<div class="new-site-link">
  <br><br>
  <a href="https://hpru.github.io/water/" target="_blank">
    اضغط هنا للموقع الجديد: hpru.github.io/water
  </a>
</div>

<div class="section-container" id="waterLevelSection">
  <div id="authorizedWaterContent" style="display: none;" class="advanced-water-display">
      <h2>📊 مستوى الماء الحالي</h2>
      <div class="tank-container">
        <img src="https://i.postimg.cc/fyPGh4kx/Chat-GPT-Image-Oct-19-2025-10-26-24-PM.png" alt="خزان ماء" class="tank-image">
        <div class="water-level" id="waterLevel"></div>
      </div>
      <div class="water-stats">
        <div class="stat-card"><div class="stat-value" id="percentDisplay">0%</div><div class="stat-label">النسبة المئوية</div></div>
        <div class="stat-card"><div class="stat-value" id="litersDisplay">0 لتر</div><div class="stat-label">الحجم الحالي</div></div>
        <div class="stat-card"><div class="stat-value" id="signalStrength">0</div><div class="stat-label">قوة الإشارة</div></div>
        <div class="stat-card"><div class="stat-value" id="distanceDisplay">0 سم</div><div class="stat-label">المسافة</div></div>
        <div class="stat-card"><div class="stat-value" id="lastUpdateTime">--:--:--</div><div class="stat-label">آخر تحديث</div></div>
        <div class="stat-card"><div class="stat-value" id="totalCapacity">0 لتر</div><div class="stat-label">السعة الكلية</div></div>
      </div>
      <div class="water-controls">
        <button onclick="refreshWaterData()">🔄 تحديث البيانات</button>
      </div>
  </div>
  
  <div id="fillingWaterContent" style="display: none;" class="maintenance-box">
      💧 يتم الآن تعبئة الخزان للشخص التالي
  </div>

  <div id="unauthorizedWaterContent" class="unauth-box">
      ⚙️ يتم الان تجهيز الخزان
  </div>
</div>

<div class="section-container">
  <div class="person-box">
    الوضع الحالي: <span id="currentPerson" class="person-name">...</span>
  </div>
  <div class="countdown-container">
    <div class="countdown-circle">
      <span id="timer-text">--:--:--</span>
    </div>
    <div class="countdown-label">الوقت المتبقي</div>
  </div>
</div>

<div class="section-container">
  <table id="scheduleTable">
    <thead>
      <tr>
        <th>اليوم</th>
        <th>التاريخ</th>
        <th>الاسم والوضع</th>
        <th>المدة</th>
        <th>خيارات</th>
      </tr>
    </thead>
    <tbody id="scheduleBody"></tbody>
  </table>
</div>

<div id="detailsModal">
  <div id="detailsModalContent">
    <span id="closeModal">&times;</span>
    <h2>تفاصيل الفترة</h2>
    <div class="modal-row"><span class="modal-label">الاسم / الوضع:</span><span class="modal-value" id="modalPerson"></span></div>
    <div class="modal-row"><span class="modal-label">التاريخ:</span><span class="modal-value" id="modalDate"></span></div>
    <div class="modal-row"><span class="modal-label">وقت البدء:</span><span class="modal-value" id="modalStart"></span></div>
    <div class="modal-row"><span class="modal-label">وقت الانتهاء:</span><span class="modal-value" id="modalEnd"></span></div>
    <div class="modal-row"><span class="modal-label">حالة الفترة:</span><span class="modal-value" id="modalStatus"></span></div>
    <button class="add-reminder-btn" id="addReminderBtn">📅 أضف تنبيه في تقويم جوجل (10 دقائق قبل)</button>
  </div>
</div>

<script>
// ============================================================
//  الأشخاص (جميعهم 12 ساعة)
// ============================================================
const people = [
    "مفرح عمضان", "محمد عمضان", "مفرح جابر", "يحيى بن جابر", "عبدالله محمد جابر",
    "أحمد مفرح", "يحيى مفرح", "جابر يحيى", "علي يحيى", "حسين يحيى", "محمد مفرح",
    "علي جابر", "محمد يحيى", "محمد أحمد", "علي احمد", "ماطر أحمد علي",
    "قاسم جابر", "جابر حسين", "مفرح أحمد", "عبدالرحمن سالم", "جابر أحمد",
    "أحمد بن يحيى", "أحمد شوعان", "محمد جبار", "home"
];

// ============================================================
//  الصلاحيات لعرض مستوى الماء
// ============================================================
const AUTHORIZED_FOR_WATER_LEVEL = ["محمد عمضان", "مفرح جابر", "حسين يحيى", "يحيى بن جابر"];

// ============================================================
//  أيام الطوارئ (ساعة واحدة 8-9 مساءً)
// ============================================================
const emergencyDays = [5, 15, 20, 25, 30];

// ============================================================
//  المتغيرات العامة
// ============================================================
let scheduleTable = [];
let currentSchedule = null;
let nextSchedule = null;
let currentModalData = null;
let currentDay = new Date().getDate();

const TANK_CONFIG = { height: 355, diameter: 370, shape: 'cylindrical' };
let totalTankVolume = (Math.PI * Math.pow((TANK_CONFIG.diameter / 2), 2) * TANK_CONFIG.height) / 1000;

// ============================================================
//  دوال مساعدة
// ============================================================
function getDayName(date) { 
    return ['الأحد', 'الإثنين', 'الثلاثاء', 'الأربعاء', 'الخميس', 'الجمعة', 'السبت'][date.getDay()]; 
}

function formatDateFull(date) {
    return date.toLocaleDateString('ar-EG', { year: 'numeric', month: 'long', day: 'numeric', weekday: 'long' });
}

function formatDateTimeFull(date) {
    return date.toLocaleDateString('ar-EG', { year: 'numeric', month: 'long', day: 'numeric', hour: '2-digit', minute: '2-digit', hour12: true });
}

// ============================================================
//  إنشاء الجدول
// ============================================================
function generateSchedule() {
    const today = new Date();
    const year = today.getFullYear();
    const month = today.getMonth();
    const daysInMonth = new Date(year, month + 1, 0).getDate();
    const tbody = document.getElementById('scheduleBody');
    tbody.innerHTML = '';
    
    let currentPeople = [...people];
    if (daysInMonth === 28) {
        currentPeople = currentPeople.filter(person => person !== "home");
    }
    
    let currentEmergencyDays = [...emergencyDays];
    if (daysInMonth === 30) {
        currentEmergencyDays = currentEmergencyDays.filter(day => day !== 30);
        if (!currentEmergencyDays.includes(29)) currentEmergencyDays.push(29);
    }
    
    scheduleTable = [];
    let personCounter = 0;
    
    for (let i = 0; i < daysInMonth; i++) {
        const date = new Date(year, month, i + 1);
        const isEmergency = currentEmergencyDays.includes(i + 1);
        const isToday = (i + 1 === currentDay);
        
        if (isEmergency) {
            // ============================================
            //  أيام الطوارئ
            // ============================================
            
            // 1. قبل الطوارئ (5:00 - 8:00 مساءً)
            let beforeStart = new Date(year, month, i, 17, 0, 0);
            let beforeEnd = new Date(year, month, i, 20, 0, 0);
            scheduleTable.push({ 
                date, 
                personName: '⏳ لا يوجد سقيا', 
                start: beforeStart, 
                end: beforeEnd, 
                isEmergency: false, 
                isFilling: true,
                isToday: isToday,
                displayDuration: "3 ساعات" 
            });
            
            // 2. الطوارئ (8:00 - 9:00 مساءً)
            let emergencyStart = new Date(year, month, i, 20, 0, 0);
            let emergencyEnd = new Date(year, month, i, 21, 0, 0);
            scheduleTable.push({ 
                date, 
                personName: '🚨 طوارئ (ساعة واحدة)', 
                start: emergencyStart, 
                end: emergencyEnd, 
                isEmergency: true, 
                isFilling: false,
                isToday: isToday,
                displayDuration: "ساعة واحدة" 
            });
            
            // 3. بعد الطوارئ (9:00 مساءً - 5:00 صباحاً)
            let afterStart = new Date(year, month, i, 21, 0, 0);
            let afterEnd = new Date(year, month, i + 1, 5, 0, 0);
            scheduleTable.push({ 
                date, 
                personName: '⏳ لا يوجد سقيا', 
                start: afterStart, 
                end: afterEnd, 
                isEmergency: false, 
                isFilling: true,
                isToday: isToday,
                displayDuration: "8 ساعات" 
            });
            
            // 4. تعبئة الخزان (5:00 صباحاً - 5:00 مساءً)
            let fillStart = new Date(year, month, i + 1, 5, 0, 0);
            let fillEnd = new Date(year, month, i + 1, 17, 0, 0);
            scheduleTable.push({ 
                date, 
                personName: '🟢 تعبئة الخزان', 
                start: fillStart, 
                end: fillEnd, 
                isEmergency: false, 
                isFilling: true,
                isToday: isToday,
                displayDuration: "12 ساعة" 
            });
            
        } else {
            // ============================================
            //  الأيام العادية: 12 ساعة للجميع
            // ============================================
            
            // 1. السقيا (5:00 مساءً - 5:00 صباحاً)
            let nightStart = new Date(year, month, i, 17, 0, 0);
            let nightEnd = new Date(year, month, i + 1, 5, 0, 0);
            const currentPerson = currentPeople[personCounter % currentPeople.length];
            
            scheduleTable.push({ 
                date, 
                personName: `🌙 ${currentPerson}`, 
                start: nightStart, 
                end: nightEnd, 
                isEmergency: false, 
                isFilling: false,
                isToday: isToday,
                displayDuration: "12 ساعة" 
            });
            
            personCounter++;
            
            // 2. تعبئة الخزان (5:00 صباحاً - 5:00 مساءً)
            let fillStart = new Date(year, month, i + 1, 5, 0, 0);
            let fillEnd = new Date(year, month, i + 1, 17, 0, 0);
            
            scheduleTable.push({ 
                date, 
                personName: '🟢 تعبئة الخزان', 
                start: fillStart, 
                end: fillEnd, 
                isEmergency: false, 
                isFilling: true,
                isToday: isToday,
                displayDuration: "12 ساعة" 
            });
        }
    }

    // عرض الجدول
    const now = new Date();

    scheduleTable.forEach((entry, index) => {
        const row = document.createElement('tr');
        const isCurrent = now >= entry.start && now < entry.end;
        
        // ============================================
        //  إضافة class "today-row" لليوم الحالي
        // ============================================
        if (entry.isToday) {
            row.classList.add('today-row');
        }
        
        if (isCurrent) { 
            row.classList.add('selected'); 
            currentSchedule = entry; 
        }
        if (now > entry.end) row.classList.add('past');
        if (entry.isEmergency) row.classList.add('emergency');
        if (entry.isFilling && !entry.personName.includes('لا يوجد سقيا')) {
            row.classList.add('fill-period');
        }
        
        let nameDisplay = entry.personName;
        let durationDisplay = entry.displayDuration;
        
        // إضافة أيقونة اليوم الحالي
        let todayIcon = entry.isToday ? ' 🔵' : '';
        
        row.innerHTML = `
            <td>${getDayName(entry.date)}</td>
            <td>${entry.date.toLocaleDateString('ar-EG', { month: 'long', day: 'numeric' })}${todayIcon}</td>
            <td>${isCurrent ? '<span class="active-indicator"></span>' : ''} ${nameDisplay}</td>
            <td>${durationDisplay}</td>
            <td><button class="detail-btn" onclick="showDetails('${nameDisplay}', '${entry.start.toISOString()}', '${entry.end.toISOString()}')">تفاصيل</button></td>
        `;
        
        tbody.appendChild(row);
    });
    
    updateCurrentSchedule();
}

// ============================================================
//  تحديث الشخص الحالي
// ============================================================
function updateCurrentSchedule() {
    const now = new Date();
    const cs = scheduleTable.find(e => now >= e.start && now < e.end);
    currentSchedule = cs || null;
    
    nextSchedule = null;
    for (let i = 0; i < scheduleTable.length; i++) {
        if (now < scheduleTable[i].start) { 
            nextSchedule = scheduleTable[i]; 
            break; 
        }
    }
    
    if (cs) {
        if (cs.isEmergency) {
            document.getElementById('currentPerson').textContent = '🚨 طوارئ (ساعة واحدة)';
            checkWaterLevelAccess(null, false);
        } else if (cs.isFilling) {
            document.getElementById('currentPerson').textContent = cs.personName;
            checkWaterLevelAccess(null, true);
        } else {
            document.getElementById('currentPerson').textContent = cs.personName.replace('🌙 ', '');
            checkWaterLevelAccess(cs.personName.replace('🌙 ', ''), false);
        }
    } else {
        document.getElementById('currentPerson').textContent = "لا يوجد فترة نشطة";
        checkWaterLevelAccess(null, false);
    }
}

// ============================================================
//  التحكم في عرض مستوى الماء
// ============================================================
function checkWaterLevelAccess(personName, isFillingTime) {
    const authContent = document.getElementById('authorizedWaterContent');
    const fillingContent = document.getElementById('fillingWaterContent');
    const unauthContent = document.getElementById('unauthorizedWaterContent');
    
    if (isFillingTime) {
        authContent.style.display = 'none';
        fillingContent.style.display = 'block';
        unauthContent.style.display = 'none';
    } else if (personName && AUTHORIZED_FOR_WATER_LEVEL.includes(personName.trim())) {
        authContent.style.display = 'block';
        fillingContent.style.display = 'none';
        unauthContent.style.display = 'none';
        refreshWaterData();
    } else {
        authContent.style.display = 'none';
        fillingContent.style.display = 'none';
        unauthContent.style.display = 'block';
    }
}

// ============================================================
//  بيانات الماء
// ============================================================
async function fetchWaterData() {
    try {
        const SCRIPT_URL = 'https://script.google.com/macros/s/AKfycbxppOlRtEYur9rESbp-9VWqm7JYxPe1TvAv4RzQCtlHsimI76xcKH_93AzwCEuhj8AK/exec';
        const response = await fetch(`${SCRIPT_URL}?operation=getLatest&t=${Date.now()}`);
        if (response.ok) {
            const data = await response.json();
            if (data.status === 'success') { 
                updateWaterDisplay(data.data); 
                return; 
            }
        }
        updateWaterDisplay(generateMockData());
    } catch (error) {
        updateWaterDisplay(generateMockData());
    }
}

function generateMockData() {
    const distance = Math.floor(Math.random() * 200) + 100;
    const waterHeight = TANK_CONFIG.height - distance;
    const volume = waterHeight > 0 ? (Math.PI * Math.pow((TANK_CONFIG.diameter / 2), 2) * waterHeight) / 1000 : 0;
    return { level: (volume / totalTankVolume) * 100, distance, strength: 410 };
}

function updateWaterDisplay(data) {
    let pct = Math.min(Math.max(parseFloat(data.level || 0), 0), 100);
    let vol = (pct / 100) * totalTankVolume;
    let dist = TANK_CONFIG.height - (pct / 100) * TANK_CONFIG.height;
    
    document.getElementById('waterLevel').style.height = pct + '%';
    document.getElementById('percentDisplay').textContent = pct.toFixed(1) + '%';
    document.getElementById('litersDisplay').textContent = Math.round(vol).toLocaleString() + ' لتر';
    document.getElementById('signalStrength').textContent = data.strength || '0';
    document.getElementById('distanceDisplay').textContent = dist.toFixed(1) + ' سم';
    document.getElementById('lastUpdateTime').textContent = new Date().toLocaleTimeString('ar-SA');
}

function refreshWaterData() { 
    fetchWaterData(); 
}

// ============================================================
//  تفاصيل الفترة
// ============================================================
function showDetails(name, start, end) {
    const startDate = new Date(start);
    const endDate = new Date(end);
    const now = new Date();
    
    document.getElementById('modalPerson').textContent = name;
    document.getElementById('modalDate').textContent = formatDateFull(startDate);
    document.getElementById('modalStart').textContent = formatDateTimeFull(startDate);
    document.getElementById('modalEnd').textContent = formatDateTimeFull(endDate);
    
    let status = now < startDate ? 'لم تبدأ بعد' : (now >= startDate && now < endDate ? '🟢 نشط الآن' : '✅ انتهت');
    document.getElementById('modalStatus').textContent = status;
    document.getElementById('detailsModal').style.display = 'flex';
    
    currentModalData = { personName: name, startTime: startDate, endTime: endDate };
}

document.getElementById('closeModal').onclick = () => {
    document.getElementById('detailsModal').style.display = 'none';
};

document.getElementById('addReminderBtn').onclick = () => {
    if (!currentModalData) return;
    const formatDateForGoogle = (d) => d.toISOString().replace(/-|:|\.\d+/g, '');
    const gUrl = `https://calendar.google.com/calendar/render?action=TEMPLATE&text=${encodeURIComponent(currentModalData.personName)}&dates=${formatDateForGoogle(currentModalData.startTime)}/${formatDateForGoogle(currentModalData.endTime)}`;
    window.open(gUrl, '_blank');
};

// ============================================================
//  العد التنازلي
// ============================================================
function updateRemainingTime() {
    const now = new Date();
    updateCurrentSchedule();
    let target = currentSchedule ? currentSchedule.end : (nextSchedule ? nextSchedule.start : null);
    
    if (!target) { 
        document.getElementById('timer-text').textContent = "--:--:--"; 
        return; 
    }
    
    const diff = target - now;
    if (diff <= 0) { 
        generateSchedule(); 
        return; 
    }
    
    const hours = Math.floor(diff / 3600000).toString().padStart(2, '0');
    const minutes = Math.floor((diff % 3600000) / 60000).toString().padStart(2, '0');
    const seconds = Math.floor((diff % 60000) / 1000).toString().padStart(2, '0');
    
    document.getElementById('timer-text').textContent = `${hours}:${minutes}:${seconds}`;
    
    let totalPeriodDuration = currentSchedule ? (currentSchedule.end - currentSchedule.start) : 43200000;
    const pct = 100 - (diff / totalPeriodDuration) * 100;
    document.querySelector('.countdown-circle').style.background = 
        `conic-gradient(var(--primary-color) ${Math.min(pct, 100)}%, transparent ${Math.min(pct, 100)}%)`;
}

// ============================================================
//  تشغيل
// ============================================================
window.onload = function() {
    document.getElementById('totalCapacity').textContent = Math.round(totalTankVolume).toLocaleString() + ' لتر';
    generateSchedule();
    setInterval(updateRemainingTime, 1000);
}
</script>
</body>
</html>
