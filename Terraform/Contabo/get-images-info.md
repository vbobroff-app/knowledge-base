
### **Contabo API**
[First auth](https://api.contabo.com/#tag/Secrets-Audits/operation/retrieveSecretAuditsList)

```bash
sudo apt update && sudo apt install -y jq
sudo apt install -y uuid-runtime
```

```bash
export CONTABO_CLIENT_ID="your_client_id"
export CONTABO_CLIENT_SECRET="your_client_secret"
export CONTABO_API_USER="your_api_user"
export CONTABO_API_PASSWORD='DScd5B34Hy!iR46'
```


```bash
# Теперь получите токен
TOKEN=$(curl -s -X POST "https://auth.contabo.com/auth/realms/contabo/protocol/openid-connect/token" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  --data-urlencode "client_id=$CLIENT_ID" \
  --data-urlencode "client_secret=$CLIENT_SECRET" \
  --data-urlencode "username=$API_USER" \
  --data-urlencode "password=$API_PASSWORD" \
  --data-urlencode "grant_type=password" | jq -r '.access_token')

echo "Token: $TOKEN"
```

```bash
curl -X GET "https://api.contabo.com/v1/compute/images" \
> -H "x-request-id: $(uuidgen)" \
> -H "Authorization: Bearer $TOKEN" \
> -H "Content-Type: application/json"
```


# Полная таблица Linux образов Contabo

| ОС | Характеристика | Версия | Размер (MB) | Формат | image_id |
|----|----------------|---------|-------------|---------|----------|
| **debian-13** | Debian 13 (trixie) | 13 | 322 | qcow2 | `0a3f4b06-a104-4917-bc85-11eba40cb6de` |
| **fedora-42** | Fedora 42 | 42 | 509 | qcow2 | `f4752284-c311-4ee9-8e76-f818eac08f44` |
| **fedora-41** | Fedora 41 | 41 | 471 | qcow2 | `9b509bd0-7a81-4142-9fba-66c0cc451cb8` |
| **rockylinux-8-plesk** | Rocky Linux 8 with Plesk | 8-plesk | 2000 | qcow2 | `75d9e3bf-439b-4dc5-a10e-0450e9f853ad` |
| **ubuntu-22.04-cpanel** | Ubuntu 22.04 with cPanel | 22.04-cpanel | 712 | qcow2 | `7a8bffde-6721-44c0-ac03-c10796f455f8` |
| **rockylinux-9-cpanel** | Rocky Linux 9 with cPanel | 9-cpanel | 2506 | qcow2 | `768a7a22-a9a0-4bb8-911f-6d4a876919b9` |

## 🏆 Рекомендации по выбору:

### **Лучший для общего использования: Debian 13**
- ✅ **Стабильность**: Debian известен надежностью
- ✅ **Размер**: 322MB - быстрая загрузка
- ✅ **Поддержка**: Долгосрочная поддержка
- ✅ **Сообщество**: Отличная документация

### **Для веб-хостинга: Ubuntu 22.04 с cPanel**
- ✅ **Панель управления**: Встроенный cPanel
- ✅ **Поддержка**: LTS версия Ubuntu
- ✅ **Экосистема**: Широкая поддержка приложений

### **Для enterprise: Rocky Linux 9 с cPanel**
- ✅ **Совместимость**: Совместим с RHEL
- ✅ **Стабильность**: Enterprise-класс
- ✅ **Панель**: cPanel для управления

### **Для разработки: Fedora 42**
- ✅ **Свежие пакеты**: Последние версии ПО
- ✅ **Инновации**: Новые технологии
- ✅ **Сообщество**: Активная разработка
