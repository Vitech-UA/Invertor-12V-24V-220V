# ⚙️ Інвертор 12 → 220 В з чистою синусоїдою

**Тип:** інвертор з автоматичним зарядним пристроєм  
**Вхідна напруга:** 12 В  
**Максимальна потужність:** 800 Вт  

---

## 🔧 Основні компоненти

### 🧠 EG8010 — генерація PWM / моделювання синуса  
📄 [EG8010 Datasheet](https://www.skytech.ir/DownLoad/File/2558_EG8010.pdf)
- Формує PWM-сигнали для керування ключами MOSFET за синусоїдальною формою.  
- Амплітуда та фаза налаштовуються через STM32.  

---

### 🔩 STM32F103 — керуючий мікроконтролер  
📄 [STM32F103CBT6 Info](https://www.st.com/en/microcontrollers-microprocessors/stm32f103/documentation.html)
- Зчитує дані з **PZEM-004T** (напряження DC, струм DC, потужність).  
- Керує зарядом акумулятора (вмикає/вимикає зарядний пристрій).  
- Перемикає режими: **мережа ↔ інвертор**.  
- Відображає параметри на **ST7789**.  
- Обробляє аварії: **перегрів, перевантаження, низька напруга тощо**.  

---

### ⚡ HCPL-3120 — оптичні драйвери для MOSFET  
📄 [HCPL-3120 Datasheet](https://www.rcscomponents.kiev.ua/datasheets/hcpl3120-000e.pdf?srsltid=AfmBOopO7fEwGVrVkGvopBMEe86slGT6oEsy12IJixGd8quxOpsz6lgK)
- Високошвидкісна гальванічна ізоляція між STM32 / EG8010 і силовою частиною.  
- Точне та швидке керування затворами MOSFET.  
- Підходить для верхніх ключів **H-моста**.  

---

### ⚙️ PZEM-004T — енергомоніторинг  
📄 [PZEM-004T V3.0 Datasheet](https://innovatorsguru.com/wp-content/uploads/2019/06/PZEM-004T-V3.0-Datasheet-User-Manual.pdf)
- Вимірює: **напругу, струм, потужність, енергію (кВт·год)**.  
- Передає дані через **опторозв’язаний UART** до STM32.  
- Використовується для **контролю** та **індикації** параметрів роботи.  

---

### 🖥️ ST7789 — дисплей індикації
📄 [ST7789](http://www.kosmodrom.com.ua/el.php?name=1.3inchIPSScreenModule_ST7789-7PIN)
Відображає:  
- 🔋 Напругу батареї  
- ⚡ Вихідну напругу  
- 🔌 Струм DC / AC  
- 💡 Потужність  
- 🔄 Стан заряду  
- 🚨 Аварійні повідомлення  
- 📊 Інші параметри системи  

---

## 📷 Фото та ілюстрації

### 🔧 Процес зборки й налагодження

| Етап | Фото |
|------|------|
| Збірка модуля | ![1](https://github.com/Vitech-UA/Invertor-12V-24V-220V/blob/main/MEDIA/20250118_205406.jpg) |
| Налагодження | ![2](https://github.com/Vitech-UA/Invertor-12V-24V-220V/blob/main/MEDIA/photo_2_2025-10-14_00-37-51.jpg) |
| Налагодження | ![3](https://github.com/Vitech-UA/Invertor-12V-24V-220V/blob/main/MEDIA/photo_3_2025-10-14_00-37-51.jpg) |
| Налагодження | ![4](https://github.com/Vitech-UA/Invertor-12V-24V-220V/blob/main/MEDIA/photo_4_2025-10-14_00-37-51.jpg) |
| Силова плата | ![5](https://github.com/Vitech-UA/Invertor-12V-24V-220V/blob/main/MEDIA/photo_5_2025-10-14_00-37-51.jpg) |

---

### 📺 Індикація роботи  
![Показометр](https://github.com/Vitech-UA/Invertor-12V-24V-220V/blob/main/MEDIA/%D0%9F%D0%BE%D0%BA%D0%B0%D0%B7%D0%BE%D0%BC%D0%B5%D1%82%D1%80.jpg)

---

### 💀 Ціна помилок при відладці  
![Спалені транзистори](https://github.com/Vitech-UA/Invertor-12V-24V-220V/blob/main/MEDIA/FUCKUP.jpg)

---

## 🛡️ Захисти та безпека

- 🔌 Захист від короткого замикання  
- ⚡ Захист від перевантаження  
- 🔋 Захист від перевищення / заниження DC  
- 🌡️ Термозахист  
- 🔦 Гальванічна ізоляція драйверів (HCPL-3120)

---

## 💾 Репозиторій прошивки STM32

Прошивка контролера STM32 доступна у відкритому доступі:  
👉 **[invertor_controller_code — GitHub Repository](https://github.com/Vitech-UA/invertor_controller_code)**  

**В репозиторії міститься:**  
- Повний вихідний код на **HAL (STM32Cube)**  
- Приклади обробки даних з **PZEM-004T**  
- Керування **EG8010** та **ST7789**

---
