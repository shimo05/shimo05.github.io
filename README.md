# shimo05.github.io
<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Рабочее расписание БНТУ</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Arial, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            padding: 20px;
            min-height: 100vh;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
            overflow: hidden;
        }
        
        .header {
            background: linear-gradient(135deg, #1e9600 0%, #2ecc71 100%);
            color: white;
            padding: 30px;
            text-align: center;
        }
        
        .header h1 {
            font-size: 28px;
            margin-bottom: 10px;
            font-weight: 700;
        }
        
        .header p {
            font-size: 16px;
            opacity: 0.9;
        }
        
        .tabs {
            display: flex;
            background: #f8f9fa;
            border-bottom: 2px solid #dee2e6;
        }
        
        .tab {
            flex: 1;
            padding: 20px;
            text-align: center;
            cursor: pointer;
            font-weight: 600;
            color: #6c757d;
            transition: all 0.3s;
            border-bottom: 3px solid transparent;
        }
        
        .tab:hover {
            background: #e9ecef;
        }
        
        .tab.active {
            color: #1e9600;
            border-bottom-color: #1e9600;
            background: white;
        }
        
        .week-content {
            display: none;
            padding: 30px;
        }
        
        .week-content.active {
            display: block;
        }
        
        .schedule-table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
        }
        
        .schedule-table th {
            background: linear-gradient(135deg, #1e9600 0%, #2ecc71 100%);
            color: white;
            padding: 15px;
            text-align: left;
            font-weight: 600;
            font-size: 14px;
        }
        
        .schedule-table td {
            padding: 15px;
            border-bottom: 1px solid #e9ecef;
            vertical-align: top;
        }
        
        .schedule-table tr:hover {
            background: #f8f9fa;
        }
        
        .day-header {
            background: #f8f9fa;
            font-weight: 700;
            color: #1e9600;
            font-size: 16px;
        }
        
        .time {
            font-weight: 700;
            color: #495057;
            white-space: nowrap;
        }
        
        .subject {
            color: #212529;
            font-weight: 600;
            margin-bottom: 5px;
        }
        
        .teacher {
            color: #6c757d;
            font-size: 14px;
            margin-bottom: 3px;
        }
        
        .location {
            color: #1e9600;
            font-size: 13px;
            font-weight: 600;
        }
        
        .empty-cell {
            color: #adb5bd;
            font-style: italic;
            text-align: center;
        }
        
        .free-day {
            background: #d4edda;
            color: #155724;
            font-weight: 600;
            text-align: center;
            font-size: 16px;
            padding: 20px !important;
        }
        
        .optional {
            opacity: 0.35;
            background: #f8f9fa;
        }
        
        .optional .subject,
        .optional .teacher,
        .optional .location,
        .optional .time {
            color: #adb5bd;
        }
        
        .note {
            background: #fff3cd;
            border-left: 4px solid #ffc107;
            padding: 15px;
            margin: 20px 0;
            border-radius: 4px;
        }
        
        .note-title {
            font-weight: 700;
            color: #856404;
            margin-bottom: 8px;
        }
        
        .note-text {
            color: #856404;
            font-size: 14px;
            line-height: 1.6;
        }
        
        @media (max-width: 768px) {
            body {
                padding: 10px;
            }
            
            .header h1 {
                font-size: 22px;
            }
            
            .tab {
                padding: 15px 10px;
                font-size: 14px;
            }
            
            .week-content {
                padding: 15px;
            }
            
            .schedule-table {
                font-size: 13px;
            }
            
            .schedule-table th,
            .schedule-table td {
                padding: 10px 8px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>📚 Рабочее расписание БНТУ</h1>
            <p>Оптимизированное расписание | Только обязательные пары</p>
        </div>
        
        <div class="tabs">
            <div class="tab active" onclick="switchWeek(1)">1-я неделя (Нечетная)</div>
            <div class="tab" onclick="switchWeek(2)">2-я неделя (Четная)</div>
        </div>
        
        <div id="week1" class="week-content active">
            <div class="note">
                <div class="note-title">💡 Ключевые моменты первой недели:</div>
                <div class="note-text">
                    • Понедельник загружен (4 пары подряд)<br>
                    • Среда: свободен до 15:40 — работай утром!<br>
                    • Четверг: полностью свободен — рабочий день<br>
                    • Пятница: приходи только к 17:45
                </div>
            </div>
            
            <table class="schedule-table">
                <thead>
                    <tr>
                        <th style="width: 15%">Время</th>
                        <th style="width: 40%">Дисциплина</th>
                        <th style="width: 30%">Преподаватель</th>
                        <th style="width: 15%">Место</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td colspan="4" class="day-header">Понедельник</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">12:00</td>
                        <td class="subject">Физическая культура</td>
                        <td class="teacher">ст.пр. Гурман А. И., пр. Клундук В. В.</td>
                        <td class="location">—</td>
                    </tr>
                    <tr>
                        <td class="time">13:55</td>
                        <td class="subject">(лекционное занятие) Материаловедение</td>
                        <td class="teacher">проф. Голубцова Е. С.</td>
                        <td class="location">9 / 204</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">15:40</td>
                        <td class="subject">(лекционное занятие) Основы психологии и педагогики</td>
                        <td class="teacher">—</td>
                        <td class="location">9 / 324</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">17:45</td>
                        <td class="subject">(лекционное занятие) Коррупция и ее общественная опасность</td>
                        <td class="teacher">ст.пр. Климко М. К.</td>
                        <td class="location">9 / 306</td>
                    </tr>
                    
                    <tr>
                        <td colspan="4" class="day-header">Вторник</td>
                    </tr>
                    <tr>
                        <td class="time">11:40</td>
                        <td class="subject">(лекционное занятие) Основы организации торговли</td>
                        <td class="teacher">ст.пр. Косякова И. М.</td>
                        <td class="location">18 / 108</td>
                    </tr>
                    <tr>
                        <td class="time">13:55</td>
                        <td class="subject">(лекционное занятие) Нормирование точности и технические измерения</td>
                        <td class="teacher">доц. Давыдова Е. А.</td>
                        <td class="location">17 / 516</td>
                    </tr>
                    <tr>
                        <td class="time">15:40</td>
                        <td class="subject">(практическое занятие) английский язык И П / Ревенко, 1/2 группы</td>
                        <td class="teacher">ст.пр. Дерман И. Н.</td>
                        <td class="location">18 / 301, 302</td>
                    </tr>
                    <tr>
                        <td class="time">17:45</td>
                        <td class="subject">(практическое занятие) Основы духовно-нравственной культуры и патриотизма</td>
                        <td class="teacher"></td>
                        <td class="location">6 / 217</td>
                    </tr>
                    
                    <tr>
                        <td colspan="4" class="day-header">Среда</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">12:00</td>
                        <td class="subject">(практическое занятие) Инженерная графика</td>
                        <td class="teacher">ст.пр. Боровская Т. В.</td>
                        <td class="location">8 / 424</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">13:55</td>
                        <td class="subject">(лекционное занятие) Физика</td>
                        <td class="teacher">зав.каф. Есман А. К.</td>
                        <td class="location">11 / 412</td>
                    </tr>
                    <tr>
                        <td class="time">15:40</td>
                        <td class="subject">(лабораторное занятие) Материаловедение / Нормирование точности, 1/2 группы</td>
                        <td class="teacher">проф. Голубцова Е. С.</td>
                        <td class="location">9 / 105, 17 / 511</td>
                    </tr>
                    <tr>
                        <td class="time">17:45</td>
                        <td class="subject">(практическое занятие) английский язык И П / Ревенко, 1/2 группы</td>
                        <td class="teacher">ст.пр. Дерман И. Н.</td>
                        <td class="location">18 / 303, 309</td>
                    </tr>
                    
                    <tr>
                        <td colspan="4" class="day-header">Четверг</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">12:00</td>
                        <td class="subject">(практическое занятие) Основы управления интеллектуальной собственностью</td>
                        <td class="teacher">доц. Акименко К. В.</td>
                        <td class="location">8 / 525</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">13:55</td>
                        <td class="subject">Физическая культура</td>
                        <td class="teacher">ст.пр. Гурман А. И., пр. Клундук В. В.</td>
                        <td class="location">—</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">15:40</td>
                        <td class="subject">(лекционное занятие) Философия</td>
                        <td class="teacher">доц. Булыго Е. К.</td>
                        <td class="location">9 / 324</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">17:45</td>
                        <td class="subject">(лекционное занятие) Основы управления интеллектуальной собственностью</td>
                        <td class="teacher">доц. Акименко К. В.</td>
                        <td class="location">9 / 324</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">19:30</td>
                        <td class="subject">(лекционное занятие) Коррупция и ее общественная опасность</td>
                        <td class="teacher">доц. Акименко К. В.</td>
                        <td class="location">9 / 324</td>
                    </tr>
                    <tr>
                        <td colspan="4" class="free-day">🎉 Все пары необязательные — полностью свободен!</td>
                    </tr>
                    
                    <tr>
                        <td colspan="4" class="day-header">Пятница</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">12:00</td>
                        <td class="subject">(практическое занятие) Инженерная графика</td>
                        <td class="teacher">ст.пр. Боровская Т. В.</td>
                        <td class="location">8 / 522</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">13:55</td>
                        <td class="subject">(лекционное занятие) Математика</td>
                        <td class="teacher">ст.пр. Бань Л. В.</td>
                        <td class="location">8 / 702</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">15:40</td>
                        <td class="subject">(лекционное занятие) История белорусской государственности</td>
                        <td class="teacher">—</td>
                        <td class="location">8 / 4П</td>
                    </tr>
                    <tr>
                        <td class="time">17:45</td>
                        <td class="subject">(лекционное занятие) Делопроизводство</td>
                        <td class="teacher">ст.пр. Стригельская И. В.</td>
                        <td class="location">8 / 509</td>
                    </tr>
                    
                    <tr>
                        <td colspan="4" class="day-header">Суббота</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">09:55</td>
                        <td class="subject">(практическое занятие) Основы психологии и педагогики</td>
                        <td class="teacher">—</td>
                        <td class="location">6 / 221</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">12:00</td>
                        <td class="subject">(практическое занятие) Физика</td>
                        <td class="teacher">Юрченко Н. Э.</td>
                        <td class="location">11 / 412</td>
                    </tr>
                    <tr>
                        <td colspan="4" class="free-day">🏖 Все пары необязательные — выходной!</td>
                    </tr>
                </tbody>
            </table>
        </div>
        
        <div id="week2" class="week-content">
            <div class="note">
                <div class="note-title">💡 Ключевые моменты второй недели:</div>
                <div class="note-text">
                    • Понедельник: полностью свободен — рабочий день!<br>
                    • Среда: свободен до 15:40 — работай утром!<br>
                    • Четверг: полностью свободен — рабочий день<br>
                    • Пятница: приходи только к 17:45<br>
                    • Суббота: полностью свободна!
                </div>
            </div>
            
            <table class="schedule-table">
                <thead>
                    <tr>
                        <th style="width: 15%">Время</th>
                        <th style="width: 40%">Дисциплина</th>
                        <th style="width: 30%">Преподаватель</th>
                        <th style="width: 15%">Место</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td colspan="4" class="day-header">Понедельник</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">12:00</td>
                        <td class="subject">Физическая культура</td>
                        <td class="teacher">ст.пр. Гурман А. И., пр. Клундук В. В.</td>
                        <td class="location">—</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">13:55</td>
                        <td class="subject">(лекционное занятие) Математика</td>
                        <td class="teacher">ст.пр. Бань Л. В.</td>
                        <td class="location">8 / 525</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">15:40</td>
                        <td class="subject">(практическое занятие) Математика</td>
                        <td class="teacher">ст.пр. Бань Л. В.</td>
                        <td class="location">8 / 525</td>
                    </tr>
                    <tr>
                        <td colspan="4" class="free-day">🎉 Все пары необязательные — полностью свободен!</td>
                    </tr>
                    
                    <tr>
                        <td colspan="4" class="day-header">Вторник</td>
                    </tr>
                    <tr>
                        <td class="time">11:40</td>
                        <td class="subject">(лекционное занятие) Основы организации торговли</td>
                        <td class="teacher">ст.пр. Косякова И. М.</td>
                        <td class="location">18 / 108</td>
                    </tr>
                    <tr>
                        <td class="time">13:55</td>
                        <td class="subject">(практическое занятие) Основы организации торговли</td>
                        <td class="teacher">ст.пр. Косякова И. М.</td>
                        <td class="location">18 / 319</td>
                    </tr>
                    <tr>
                        <td class="time">15:40</td>
                        <td class="subject">(практическое занятие) английский язык И П / Ревенко, 1/2 группы</td>
                        <td class="teacher">ст.пр. Дерман И. Н.</td>
                        <td class="location">18 / 301, 302</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">17:45</td>
                        <td class="subject">(ОИЗ) Физика</td>
                        <td class="teacher">зав.каф. Есман А. К.</td>
                        <td class="location">6 / 217</td>
                    </tr>
                    
                    <tr>
                        <td colspan="4" class="day-header">Среда</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">12:00</td>
                        <td class="subject">(практическое занятие) Инженерная графика</td>
                        <td class="teacher">ст.пр. Боровская Т. В.</td>
                        <td class="location">8 / 522</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">13:55</td>
                        <td class="subject">(лекционное занятие) Физика</td>
                        <td class="teacher">зав.каф. Есман А. К.</td>
                        <td class="location">11 / 412</td>
                    </tr>
                    <tr>
                        <td class="time">15:40</td>
                        <td class="subject">(лабораторное занятие) Материаловедение / Нормирование точности, 1/2 группы</td>
                        <td class="teacher">проф. Голубцова Е. С.</td>
                        <td class="location">9 / 105, 17 / 511</td>
                    </tr>
                    <tr>
                        <td colspan="4" class="day-header">Четверг</td>
                    </tr>
                    <tr>
                        <td colspan="4" class="free-day">🎉 Полностью свободен — рабочий день!</td>
                    </tr>
                    
                    <tr>
                        <td colspan="4" class="day-header">Пятница</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">12:00</td>
                        <td class="subject">(практическое занятие) Инженерная графика</td>
                        <td class="teacher">ст.пр. Боровская Т. В.</td>
                        <td class="location">8 / 522</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">13:55</td>
                        <td class="subject">(лекционное занятие) Математика</td>
                        <td class="teacher">ст.пр. Бань Л. В.</td>
                        <td class="location">8 / 702</td>
                    </tr>
                    <tr class="optional">
                        <td class="time">15:40</td>
                        <td class="subject">(лекционное занятие) История белорусской государственности</td>
                        <td class="teacher">—</td>
                        <td class="location">8 / 4П</td>
                    </tr>
                    <tr>
                        <td class="time">17:45</td>
                        <td class="subject">(практическое занятие) Нормирование точности и технические измерения</td>
                        <td class="teacher">доц. Давыдова Е. А.</td>
                        <td class="location">8 / 509</td>
                    </tr>
                    
                    <tr>
                        <td colspan="4" class="day-header">Суббота</td>
                    </tr>
                    <tr>
                        <td colspan="4" class="free-day">🏖 Выходной</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </div>
    
    <script>
        function switchWeek(weekNumber) {
            // Remove active class from all tabs and content
            document.querySelectorAll('.tab').forEach(tab => tab.classList.remove('active'));
            document.querySelectorAll('.week-content').forEach(content => content.classList.remove('active'));
            
            // Add active class to selected tab and content
            document.querySelectorAll('.tab')[weekNumber - 1].classList.add('active');
            document.getElementById('week' + weekNumber).classList.add('active');
        }
    </script>
</body>
</html>
