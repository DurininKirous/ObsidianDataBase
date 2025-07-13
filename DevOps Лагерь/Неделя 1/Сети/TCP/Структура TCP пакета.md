---
sr-due: 2025-07-14
sr-interval: 1
sr-ease: 232
---

#sr-due 
TCP пакет - это часть ip пакета, который содержит:

IP Header - минимум 20 байт
TCP Header - минимум 20 байт
TCP Payload - данные приложения

Из чего состоит TCP Header:

| Поле                   | Размер    | Что значит                                |
| ---------------------- | --------- | ----------------------------------------- |
| Source Port            | 2 байта   | Порт источника                            |
| Destination Port       | 2 байта   | Порт назначения                           |
| Sequence Number        | 4 байта   | Номер первого байта в этом сегменте       |
| Acknowledgement Number | 4 байта   | Следующий байт, который ожидаем принять   |
| Data Offset            | 4 бита    | Длина TCP заголовка (для опций)           |
| Reserved               | 3 бита    | Зарезервировано                           |
| Flags (Control Bits)   | 9 бит     | URG, ACK, PSH, RST, SYN, FIN              |
| Windows Size           | 2 байта   | Размер окна приёма                        |
| Checksum               | 2 байта   | Контрольная сумма на весь TCP сегмент     |
| Urgent Pointer         | 2 байта   | Если URG=1, указывает, где срочные данные |
| Options                | переменно | Например, MSS, SACK, window scale         |

[[Структура TCP пакета]]
[[TCP]]