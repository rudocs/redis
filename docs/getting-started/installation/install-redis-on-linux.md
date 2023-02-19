# Установка Redis в Linux

Как установить Redis в Linux

---

Большинство основных дистрибутивов Linux предоставляют пакеты для Redis.

## Установка в Ubuntu/Debian

Вы можете установить последние стабильные версии Redis из официального APT репозитория `packages.redis.io`.

``` markdown title="Prerequisites"
Если вы используете очень минимальный дистрибутив (например, контейнер Docker), вам может потребоваться сначала установить `lsb-release`:
```

<div class="result" markdown>
``` bash
sudo apt install lsb-release
```
</div>

Добавьте репозиторий в индекс <code>apt</code>, обновите его, а затем установите:

``` bash
curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg

echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list

sudo apt-get update
sudo apt-get install redis
```

## Установка из Snapcraft

[Магазин Snapcraft](https://snapcraft.io/store) предоставляет [пакеты Redis](https://snapcraft.io/redis), которые можно установить на платформах, поддерживающих snap.
Snap поддерживается и доступен в большинстве основных дистрибутивах Linux.

Для установки через snap выполните:

``` bash
sudo snap install redis
```

Если в вашем Linux сейчас не установлен snap, установите его, следуя инструкциям, описанным в разделе [Установка snapd](https://snapcraft.io/docs/installing-snapd).
