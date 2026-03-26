---
sr-due: 2026-04-08
sr-interval: 53
sr-ease: 190
---

#sr-due 
# DNS пакет — часть IP пакета, который содержит:

IP Header — минимум 20 байт  
UDP Header — 8 байт (для обычного DNS)  
DNS Message — данные DNS запроса или ответа

---

## Из чего состоит DNS Message

| Поле                 | Размер  | Что значит                                                 |
| -------------------- | ------- | ---------------------------------------------------------- |
| ID                   | 2 байта | Идентификатор запроса (для сопоставления запроса и ответа) |
| Flags                | 2 байта | Флаги (QR, Opcode, AA, TC, RD, RA, RCODE и др.)            |
| QDCOUNT (Questions)  | 2 байта | Количество вопросов                                        |
| ANCOUNT (Answers)    | 2 байта | Количество ответов                                         |
| NSCOUNT (Authority)  | 2 байта | Количество authority записей                               |
| ARCOUNT (Additional) | 2 байта | Количество additional записей                              |

---

## Секция вопросов (Question Section)

| Поле   | Размер    | Что значит                                     |
| ------ | --------- | ---------------------------------------------- |
| QNAME  | переменно | Имя (например, "3www6google3com0")             |
| QTYPE  | 2 байта   | Тип запроса (1 = A, 28 = AAAA, 15 = MX и т.д.) |
| QCLASS | 2 байта   | Класс (1 = IN — Internet)                      |

---

## Секция ответов (Answer Section), Authority, Additional

Одинаковая структура для всех ресурсных записей (Resource Record).

| Поле     | Размер    | Что значит                               |
| -------- | --------- | ---------------------------------------- |
| NAME     | переменно | Имя, к которому относится запись         |
| TYPE     | 2 байта   | Тип записи (A, AAAA, MX, CNAME, PTR ...) |
| CLASS    | 2 байта   | Класс (IN)                               |
| TTL      | 4 байта   | Time to Live                             |
| RDLENGTH | 2 байта   | Длина данных                             |
| RDATA    | переменно | Данные (IP, текст, имя и т.д.)           |

---

## Пример флагов в поле Flags (16 бит)

| Биты   | Что значит                                      |
| ------ | ----------------------------------------------- |
| QR     | 1 бит — 0 = Query, 1 = Response                 |
| Opcode | 4 бита — тип запроса (обычно 0 = стандартный)   |
| AA     | 1 бит — Authoritative Answer                    |
| TC     | 1 бит — Truncated (нужен TCP)                   |
| RD     | 1 бит — Recursion Desired                       |
| RA     | 1 бит — Recursion Available                     |
| Z      | 3 бита — зарезервировано                        |
| RCODE  | 4 бита — код ответа (0 = NOERROR, 3 = NXDOMAIN) |

---

## Итоговая вложенность

IP Header  
└─ UDP Header  
└─ DNS Message  
├─ Header (ID, Flags, QDCOUNT, ANCOUNT, NSCOUNT, ARCOUNT)  
├─ Question Section (QDCOUNT записей)  
├─ Answer Section (ANCOUNT записей)  
├─ Authority Section (NSCOUNT записей)  
└─ Additional Section (ARCOUNT записей)

---

## Полезные заметки

- DNS через UDP обычно максимум 512 байт, больше — устанавливается флаг TC и клиент делает повтор через TCP.
- DNS по умолчанию использует порт 53.
- Для DNSSEC могут появляться дополнительные записи в Additional.
- DNS over HTTPS (DoH) и DNS over TLS (DoT) оборачивают DNS Message в HTTPS/TLS.

[[Структура DNS пакета]]
[[Obsidian Vault/Rebrain/Studying/DevOps/Неделя 1/Сети/DNS/DNS|DNS]]
