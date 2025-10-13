---
sr-due: 2025-11-09
sr-interval: 31
sr-ease: 230
---

#sr-due 
Всё крутится вокруг трёх стадий:
1. Controller сервис (в contoler-plane)
	1. CreateVolume, DeleteVolume (динамическое выделение хранилища)
	2. ControllerPublishVolume (прикрепить к ноде)
	3. ControllerUnpublishVolume
2. Node сервис (на ноде, через kubelet)
	1. NodeStageVolume (подготовить том, например, смонтировать в staging-папку)
	2. NodePublishVolume (подмонтировать в pod sandbox)
	3. NodeUnpublishVolume / NodeUnstageVolume
3. Identity сервис - сообщает версию / состояние драйвера
[[Основные операции CSI]]
[[CSI]]