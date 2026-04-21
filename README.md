# fafafwfaww

Этот репозиторий собирает [`fokkonaut/F-DDrace`](https://github.com/fokkonaut/F-DDrace) с ветки `F-DDrace` под ваш хостинг:

- `Debian GNU/Linux 13 (trixie)`
- `linux arm64`
- Docker-контейнер

Сборка идет через GitHub Actions и использует `Debian trixie` arm64-контейнер через QEMU, чтобы бинарник совпадал с архитектурой хостинга.

## Что получается

После успешной сборки workflow создает prerelease с архивом вида `fddrace-<version>-linux-arm64.tar.xz`, внутри которого есть:

- `teeworlds_srv`
- `data/`
- `storage.cfg`
- `license.txt`
- `BUILD-INFO.txt`

## Как использовать

1. Запушить изменения в `main` или вручную запустить workflow `Build F-DDrace ARM64`.
2. Открыть раздел `Releases` в репозитории.
3. Скачать архив `fddrace-<version>-linux-arm64.tar.xz` и файл `.sha256`.
4. Распаковать архив в `/home/container` на хостинге.
5. Если нужно, дать права на запуск: `chmod +x teeworlds_srv`.
6. В startup-команде хостинга использовать `./teeworlds_srv`.

## Что делает workflow

- забирает `F-DDrace` вместе с submodules;
- собирает серверный релиз без клиента;
- проверяет, что бинарник запускается;
- упаковывает готовую сборку в архив для `linux arm64`.
