<!DOCTYPE html>
<html lang="fa" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>سنجش‌بار | تحلیل آزمون کنکور</title>
    <style>
        :root {
            --primary: #2563eb;
            --primary-hover: #1d4ed8;
            --bg: #f8fafc;
            --surface: #ffffff;
            --text: #0f172a;
            --text-muted: #64748b;
            --border: #e2e8f0;
            --success: #16a34a;
            --danger: #dc2626;
            --warning: #d97706;
            --radius: 12px;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
        }

        body {
            background-color: var(--bg);
            color: var(--text);
            line-height: 1.5;
            padding: 16px;
            max-width: 800px;
            margin: 0 auto;
        }

        header {
            text-align: center;
            margin-bottom: 24px;
            padding: 16px;
            background: var(--surface);
            border-radius: var(--radius);
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
        }

        h1 {
            font-size: 1.5rem;
            color: var(--primary);
            margin-bottom: 4px;
        }

        .subtitle {
            font-size: 0.875rem;
            color: var(--text-muted);
        }

        .card {
            background: var(--surface);
            border-radius: var(--radius);
            padding: 20px;
            margin-bottom: 20px;
            box-shadow: 0 1px 3px rgba(0,0,0,0.1);
            border: 1px solid var(--border);
        }

        .card-title {
            font-size: 1.1rem;
            font-weight: bold;
            margin-bottom: 16px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .form-group {
            margin-bottom: 16px;
        }

        label {
            display: block;
            font-size: 0.875rem;
            font-weight: 600;
            margin-bottom: 6px;
        }

        input[type="text"], input[type="number"] {
            width: 100%;
            padding: 10px 12px;
            border: 1px solid var(--border);
            border-radius: 8px;
            font-size: 0.95rem;
            outline: none;
            transition: border-color 0.2s;
        }

        input[type="text"]:focus, input[type="number"]:focus {
            border-color: var(--primary);
        }

        .subject-row {
            background: #f1f5f9;
            border-radius: 8px;
            padding: 12px;
            margin-bottom: 12px;
        }

        .subject-title {
            font-weight: bold;
            font-size: 0.95rem;
            margin-bottom: 8px;
            color: #334155;
        }

        .inputs-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 8px;
        }

        .input-box {
            display: flex;
            flex-direction: column;
            gap: 4px;
        }

        .input-box span {
            font-size: 0.75rem;
            color: var(--text-muted);
            text-align: center;
        }

        .input-box input {
            text-align: center;
            padding: 6px;
        }

        .btn {
            display: block;
            width: 100%;
            padding: 12px;
            background: var(--primary);
            color: white;
            border: none;
            border-radius: 8px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            transition: background 0.2s;
        }

        .btn:hover {
            background: var(--primary-hover);
        }

        .btn-danger {
            background: var(--danger);
            width: auto;
            padding: 6px 12px;
            font-size: 0.8rem;
        }

        .chart-container {
            width: 100%;
            overflow-x: auto;
        }

        .bar-chart {
            display: flex;
            align-items: flex-end;
            gap: 12px;
            height: 200px;
            padding: 20px 10px 30px 10px;
            border-bottom: 2px solid var(--border);
            min-width: 100%;
        }

        .bar-wrapper {
            flex: 1;
            display: flex;
            flex-direction: column;
            align-items: center;
            height: 100%;
            justify-content: flex-end;
            min-width: 40px;
        }

        .bar {
            width: 100%;
            max-width: 36px;
            background: var(--primary);
            border-radius: 4px 4px 0 0;
            transition: height 0.3s ease;
            position: relative;
        }

        .bar-value {
            position: absolute;
            top: -20px;
            font-size: 0.75rem;
            font-weight: bold;
            width: 100%;
            text-align: center;
        }

        .bar-label {
            font-size: 0.7rem;
            color: var(--text-muted);
            margin-top: 6px;
            text-align: center;
            white-space: nowrap;
            text-overflow: ellipsis;
            overflow: hidden;
            width: 100%;
        }

        .history-item {
            border: 1px solid var(--border);
            border-radius: 8px;
            padding: 12px;
            margin-bottom: 10px;
        }

        .history-header {
            display: flex;
            justify-content: space-between;
            font-weight: bold;
            margin-bottom: 8px;
            padding-bottom: 6px;
            border-bottom: 1px dashed var(--border);
        }

        .history-details {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(140px, 1fr));
            gap: 8px;
            font-size: 0.85rem;
        }

        select {
            width: 100%;
            padding: 10px;
            border-radius: 8px;
            border: 1px solid var(--border);
            margin-bottom: 16px;
            outline: none;
        }
    </style>
</head>
<body>

    <header>
        <h1>سنجش‌بار | ثبت و تحلیل آزمون</h1>
        <div class="subtitle">محاسبه دقیق درصد، ثبت مجزای دروس و نمودار پیشرفت (آفلاین)</div>
    </header>

    <!-- ثبت آزمون -->
    <div class="card">
        <div class="card-title">📝 ثبت کارنامه آزمون جدید</div>
        
        <div class="form-group">
            <label>تاریخ آزمون / عنوان آزمون:</label>
            <input type="text" id="examDate" placeholder="مثال: آزمون جامع شماره ۱">
        </div>

        <div id="subjectsContainer"></div>

        <button class="btn" onclick="saveExam()">ثبت و محاسبه آزمون</button>
    </div>

    <!-- نمودار مقایسه‌ای -->
    <div class="card">
        <div class="card-title">
            <span>📊 نمودار ستونی درصدها</span>
            <select id="filterSubject" onchange="renderChart()" style="width: auto; margin:0; padding:4px 8px;">
                <option value="ALL">میانگین کل آزمون‌ها</option>
            </select>
        </div>
        <div class="chart-container">
            <div class="bar-chart" id="barChart"></div>
        </div>
    </div>

    <!-- تاریخچه آزمون‌ها -->
    <div class="card">
        <div class="card-title">
            <span>📜 سوابق آزمون‌ها</span>
            <button class="btn btn-danger" onclick="clearAllData()">حذف همه داده‌ها</button>
        </div>
        <div id="historyList"></div>
    </div>

    <script>
        const subjectsList = [
            "ریاضی (دوازدهم) ۳",
            "ریاضی (یازدهم) ۲",
            "ریاضی (دهم) ۱",
            "زیست‌شناسی (دوازدهم) ۳",
            "زیست‌شناسی (یازدهم) ۲",
            "زیست‌شناسی (دهم) ۱",
            "شیمی (دوازدهم) ۳",
            "شیمی (یازدهم) ۲",
            "شیمی (دهم) ۱",
            "فیزیک (دوازدهم) ۳",
            "فیزیک (یازدهم) ۲",
            "فیزیک (دهم) ۱",
            "زمین‌شناسی"
        ];

        function getHistory() {
            try {
                return JSON.parse(localStorage.getItem('exam_history') || '[]');
            } catch (e) {
                return [];
            }
        }

        function saveHistoryData(history) {
            try {
                localStorage.setItem('exam_history', JSON.stringify(history));
            } catch (e) {}
        }

        function initForm() {
            const container = document.getElementById('subjectsContainer');
            const selectFilter = document.getElementById('filterSubject');
            
            if (!container || !selectFilter) return;
            
            container.innerHTML = '';
            
            subjectsList.forEach((sub, idx) => {
                const row = document.createElement('div');
                row.className = 'subject-row';
                row.innerHTML = `
                    <div class="subject-title">${sub}</div>
                    <div class="inputs-grid">
                        <div class="input-box">
                            <span>درست</span>
                            <input type="number" id="correct_${idx}" min="0" placeholder="0">
                        </div>
                        <div class="input-box">
                            <span>نادرست</span>
                            <input type="number" id="wrong_${idx}" min="0" placeholder="0">
                        </div>
                        <div class="input-box">
                            <span>نزده</span>
                            <input type="number" id="empty_${idx}" min="0" placeholder="0">
                        </div>
                    </div>
                `;
                container.appendChild(row);

                const opt = document.createElement('option');
                opt.value = sub;
                opt.innerText = sub;
                selectFilter.appendChild(opt);
            });

            const dateInput = document.getElementById('examDate');
            if (dateInput) {
                dateInput.value = 'آزمون جدید';
            }
        }

        function calcPercentage(c, w, e) {
            const total = c + w + e;
            if (total === 0) return null;
            const score = ((c * 3) - w) / (total * 3) * 100;
            return Math.round(score * 10) / 10;
        }

        function saveExam() {
            const dateInput = document.getElementById('examDate');
            const dateStr = dateInput ? dateInput.value.trim() : 'آزمون';
            if (!dateStr) {
                alert('لطفا تاریخ یا عنوان آزمون را وارد کنید.');
                return;
            }

            const examData = {
                id: Date.now(),
                date: dateStr,
                subjects: {},
                totalCorrect: 0,
                totalWrong: 0,
                totalEmpty: 0
            };

            let enteredAny = false;

            subjectsList.forEach((sub, idx) => {
                const cEl = document.getElementById(`correct_${idx}`);
                const wEl = document.getElementById(`wrong_${idx}`);
                const eEl = document.getElementById(`empty_${idx}`);

                const c = cEl ? (parseInt(cEl.value) || 0) : 0;
                const w = wEl ? (parseInt(wEl.value) || 0) : 0;
                const e = eEl ? (parseInt(eEl.value) || 0) : 0;

                if (c > 0 || w > 0 || e > 0) {
                    enteredAny = true;
                    const pct = calcPercentage(c, w, e);
                    examData.subjects[sub] = { c, w, e, pct };
                    examData.totalCorrect += c;
                    examData.totalWrong += w;
                    examData.totalEmpty += e;
                }
            });

            if (!enteredAny) {
                alert('لطفاً حداقل اطلاعات یک درس را وارد کنید.');
                return;
            }

            examData.totalPct = calcPercentage(examData.totalCorrect, examData.totalWrong, examData.totalEmpty);

            let history = getHistory();
            history.push(examData);
            saveHistoryData(history);

            subjectsList.forEach((_, idx) => {
                if (document.getElementById(`correct_${idx}`)) document.getElementById(`correct_${idx}`).value = '';
                if (document.getElementById(`wrong_${idx}`)) document.getElementById(`wrong_${idx}`).value = '';
                if (document.getElementById(`empty_${idx}`)) document.getElementById(`empty_${idx}`).value = '';
            });

            renderAll();
            alert('آزمون با موفقیت ثبت شد!');
        }

        function renderChart() {
            const chart = document.getElementById('barChart');
            const filterEl = document.getElementById('filterSubject');
            if (!chart || !filterEl) return;

            const filter = filterEl.value;
            const history = getHistory();

            chart.innerHTML = '';

            if (history.length === 0) {
                chart.innerHTML = '<div style="width:100%; text-align:center; color:var(--text-muted);">هنوز آزمونی ثبت نشده است.</div>';
                return;
            }

            history.forEach((exam) => {
                let pct = 0;
                if (filter === 'ALL') {
                    pct = exam.totalPct || 0;
                } else {
                    pct = (exam.subjects && exam.subjects[filter]) ? exam.subjects[filter].pct : 0;
                }

                const barWrapper = document.createElement('div');
                barWrapper.className = 'bar-wrapper';

                const heightPct = Math.max(0, Math.min(100, pct));

                barWrapper.innerHTML = `
                    <div class="bar" style="height: ${heightPct}%;">
                        <div class="bar-value">${pct}%</div>
                    </div>
                    <div class="bar-label" title="${exam.date}">${exam.date}</div>
                `;

                chart.appendChild(barWrapper);
            });
        }

        function renderHistory() {
            const list = document.getElementById('historyList');
            if (!list) return;

            const history = getHistory();
            list.innerHTML = '';

            if (history.length === 0) {
                list.innerHTML = '<div style="text-align:center; color:var(--text-muted); padding:10px;">سابقه‌ای وجود ندارد.</div>';
                return;
            }

            history.slice().reverse().forEach((exam) => {
                const item = document.createElement('div');
                item.className = 'history-item';

                let detailsHtml = '';
                if (exam.subjects) {
                    for (const [subName, subData] of Object.entries(exam.subjects)) {
                        detailsHtml += `<div><strong>${subName}:</strong> ${subData.pct}% (درست: ${subData.c} | نادرست: ${subData.w})</div>`;
                    }
                }

                item.innerHTML = `
                    <div class="history-header">
                        <span>🗓 ${exam.date}</span>
                        <span>درصد کل: <span style="color:var(--primary);">${exam.totalPct}%</span></span>
                    </div>
                    <div class="history-details">
                        ${detailsHtml}
                    </div>
                `;

                list.appendChild(item);
            });
        }

        function clearAllData() {
            if (confirm('آیا از حذف تمام داده‌های ذخیره‌شده مطمئن هستید؟')) {
                localStorage.removeItem('exam_history');
                renderAll();
            }
        }

        function renderAll() {
            renderChart();
            renderHistory();
        }

        // اجرای مستقیم بدون نیاز به window.onload
        try {
            initForm();
            renderAll();
        } catch (err) {
            console.error(err);
        }
    </script>
</body>
</html>
