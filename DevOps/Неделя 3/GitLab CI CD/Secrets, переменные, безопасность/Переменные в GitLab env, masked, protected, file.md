---
sr-due: 2026-03-04
sr-interval: 128
sr-ease: 250
---

#sr-due 
Где задаются:
- В UI репозитория: `Settings → CI/CD → Variables`
- В .gitlab-ci.yml (не для секретов)
	variables:
	  LOG_LEVEL: debug
	  ENV: prod
- В `job:`-секциях:
	deploy:
  variables:
    ENV: staging

Виды переменных в UI

| Тип           | Что значит                               | Когда использовать                        |
| ------------- | ---------------------------------------- | ----------------------------------------- |
| **Masked**    | Значение скрывается в логах CI (`*****`) | Для токенов, паролей, ключей              |
| **Protected** | Работает **только в protected-ветках**   | Для секретов продакшн (main, release)     |
| **File**      | Значение передаётся как файл             | Для `.pem`, `.json`, `.env`, `kubeconfig` |
| **Plain**     | Обычная env-переменная                   | Для флагов, переменных окружения          |
Пример file переменной:

Variable:  AWS_CREDENTIALS
Type:      File
Value:     <содержимое ~/.aws/credentials>

[[Переменные в GitLab env, masked, protected, file]]
[[Secrets, переменные, безопасность]]