
---

## 📌 Завдання: Налагодити деплой APK у Firebase через GitLab CI/CD

### 🔧 Поточна ситуація:

* У `.gitlab-ci.yml` вже налаштовано пайплайн з етапами: `test`, `analyze`, `build`, `deploy`
* Пайплайн падає на етапі `deploy-to-firebase` (також падає на етапі analyze але це не критично)
* Групу тестувальників у Firebase App Distribution вже створено
* Коли пайплайн один раз відпрацював, тестувальники отримали лист із посиланням на версію застосунку (тобто це працює, є прецедент)

### 🎯 Очікуваний результат:

> Після успішного Merge Request:

* Проходить збірка релізної APK
* APK деплоїться на Firebase App Distribution
* Тестувальники отримують листа з посиланням на завантаження застосунку (це вже працює)

---

### 🧪 Поточна конфігурація пайплайну:

[посилання](https://gitlab.com/antistresscompanion/antistress-app/-/blob/develop/.gitlab-ci.yml?ref_type=heads)

---

### 📎 Додатково:

* Firebase App ID уже вказаний у змінній `FIREBASE_APP_ID`
* У Firebase вже створено групу `testers`, які мають отримувати доступ
* Потрібно правильно налаштувати авторизацію через **`FIREBASE_TOKEN`** або **service account JSON key** [посилання](https://gitlab.com/antistresscompanion/antistress-app/-/settings/ci_cd#js-cicd-variables-settings)
* Пайплайн має бути стабільним і надійним для майбутніх деплоїв

---

### 🛠 Що треба зробити:

1. Дослідити, чому падає `deploy-to-firebase` [детальніше тут](https://gitlab.com/antistresscompanion/antistress-app/-/jobs/10123759384)
2. Налагодити автентифікацію (через `firebase login:ci` або service account) (опціонально, якщо буде потреба)
3. Перевірити, що білд APK відбувається коректно
4. Налаштувати стабільний деплой у Firebase App Distribution
5. Перевірити, що тестувальники отримують повідомлення про нову збірку

---

