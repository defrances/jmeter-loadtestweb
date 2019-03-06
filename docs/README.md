# Настройки Fiddler

Hide Connect
Включить расшифровку HTTPS


# Подготовка эталонного профиля

    mkdir ~/firefox.profile.loadtestweb ; firefox --profile ~/firefox.profile.loadtestweb -url about:config

about:config

network.http.spdy

Отключить:
network.http.spdy.allow-push
network.http.spdy.enabled
network.http.spdy.enabled.http2
network.http.spdy.enabled.deps
network.http.spdy.websockets



network.proxy.http = localhost
network.proxy.http_port = 8888
network.proxy.ssl = localhost
network.proxy.ssl_port = 8888
network.proxy.type = 1

## Ошибка при установлении защищённого соединения
    При соединении с loadtestweb.info произошла ошибка. SSL получило искажённое сообщение рукопожатия «Приветствие сервера». Код ошибки: SSL_ERROR_RX_MALFORMED_SERVER_HELLO 

    Понизить версию TLS, отключить TLS 1.3, её не поддерживает Fiddler
    security.tls.version.max = 3 (по умолчанию 4)

# Настройка сертификата (обновление)
    firefox -new-instance --profile ~/firefox.profile.loadtestweb -url about:preferences


# Команда для запуска браузера с настроенным профилем
    
    fxtmp=/tmp/firefox.tmp.profile.loadtestweb

    rm -rf $fxtmp && cp -R -f ~/firefox.profile.loadtestweb $fxtmp && firefox -new-instance --profile $fxtmp -url about:config


# Настройка отображаемых в Fiddler колонок

Запустить нажать Ctrl+Q
Набрать команду добавления
https://docs.telerik.com/fiddler/KnowledgeBase/SessionFlags


    cols add @response.server
    @request.Cookie
    @response.Set-Cookie
    X-ClientPort



    https://loadtestweb.info

Настройки Fiddler можно задавать в окне опций:

cert:

    MIIDozCCAougAwIBAgIQAI2jVTl6YxLrkkXVRqi0KTANBgkqhkiG9w0BAQsFADBqMSswKQYDVQQLDCJDcmVhdGVkIGJ5IGh0dHA6Ly93d3cuZmlkZGxlcjIuY29tMRgwFgYDVQQKDA9ET19OT1RfVFJVU1RfQkMxITAfBgNVBAMMGERPX05PVF9UUlVTVF9GaWRkbGVyUm9vdDAeFw0xOTAyMjYwMDAwMDBaFw0yOTAzMDUxMzU3MzZaMGoxKzApBgNVBAsMIkNyZWF0ZWQgYnkgaHR0cDovL3d3dy5maWRkbGVyMi5jb20xGDAWBgNVBAoMD0RPX05PVF9UUlVTVF9CQzEhMB8GA1UEAwwYRE9fTk9UX1RSVVNUX0ZpZGRsZXJSb290MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEArxIyfsxRgDXFw1rE9PydvSXAefbRDyHqe+jnjfdlC+Df2IWTvHbXq+Ddj3EWB+eB5gfzAgM03Hh0Mo1tylA7a2Xzkb/K+KbgjKhVaa/T+/ua2hT+sK7K4JXlztKLMWQJTbwwCT28C6rgbqnAau0AtUbO0e0RHyx4MUYAMtoiLdw0tPyb25ndi9iuYgibFnz4P8AM0rLwUmRssBZh7s1JOrmOF6Td3yt031cIr5CVMWhrinGocgh6reAh/Yr1e3PKw7uprd7wU54pYc4tER5OkFc46t//HSP5IixlmRrUscbTO5y8GLIRoVGhtWUfP7kNeVJNh1eUvxCoNAdaD0ujRwIDAQABo0UwQzASBgNVHRMBAf8ECDAGAQH/AgEAMA4GA1UdDwEB/wQEAwICBDAdBgNVHQ4EFgQUweJpSgySuACpanfuDJIImV8YZH4wDQYJKoZIhvcNAQELBQADggEBAIoJ0LtnqtHICRfV05RGkaQ/1E8njPkDkzapfmZzaPBBHJW5O5Rclb2QrfCctqW/skYRdJyldQl0Rn4IJU15uvXbGbYFNpF2GspZB4G91tgm9y2OPaDLWmSLYlU8ZwrPm8OR8j74oCko8Y/SxQ5nBWP3kdLR69djUIm/pOwn8R6RXVHN/3dOI261mXe+1CDVeffiHhZd3BhzZgH2eqNlNyPXvxcyMeaYy7+TY/Lcys7+8cet8tEJZFBTPAnxgirBn6QuvBZrqt5IQyHEvqW0+Qix8DZGXR3sOeUHFNTfwt5G5KhNpz9YYMMa3AOmT09EM8D/D8DSjZyZ6/M65uXXfBg=

key:

    MIIEvwIBADANBgkqhkiG9w0BAQEFAASCBKkwggSlAgEAAoIBAQCvEjJ+zFGANcXDWsT0/J29JcB59tEPIep76OeN92UL4N/YhZO8dter4N2PcRYH54HmB/MCAzTceHQyjW3KUDtrZfORv8r4puCMqFVpr9P7+5raFP6wrsrgleXO0osxZAlNvDAJPbwLquBuqcBq7QC1Rs7R7REfLHgxRgAy2iIt3DS0/Jvbmd2L2K5iCJsWfPg/wAzSsvBSZGywFmHuzUk6uY4XpN3fK3TfVwivkJUxaGuKcahyCHqt4CH9ivV7c8rDu6mt3vBTnilhzi0RHk6QVzjq3/8dI/kiLGWZGtSxxtM7nLwYshGhUaG1ZR8/uQ15Uk2HV5S/EKg0B1oPS6NHAgMBAAECggEBAIKZ9qV00o/sjV2Qx0FjemDyWsYhhA/f40cQljzoA6960EJ8U5vSpE2KcH5jhGXdJKBv6a7kqXiXO0fDDdZRSCJ0aeGezFH2W6lSonU3P9LI/doWs3Em1B36dPd3RXNRB0fATa13KmMh1E95vxuFNnQFIKCmU5GH4RoQ+HD3HWxLiuDutm7Tv2op71YHZDdoFjVmBYS9fDsa+RrlBIGnZfuYCCEX0wS/HoBr4jLlDG3CcBzIIa/gGbzPIVyPJ5FvFy/ZmbP+vzYcM7B7ZDptKGdMZB17c7eFJxJqwE5m/rsvTdyFd8uKK2qQ81Z8mh+kt6m/Xlr75rVErZz5cTmufqECgYEA/XDCvrTzQL4Zw2p4yB8qxirofd168fhCOLEuRM4XNUFPdBTKD18RB+McOVFoQRPfLdS/dnrLBDcnWTQ6q526lOvxkoicelpKJN0T7ReeSKQCKGOnxR4q2tiPcd1IsNBu8AEuCky+TKwVshbh1Hu0q0QbVvYqMlIk0luvHsWTFzkCgYEAsNbSc4x+rf1Qso/5gC1Iww4F8l6GWqdMkC+M/uvuLllqas+c8e+yhYkCZuaQzkB1EluUOx5jKm3AuLkkMt2Nbpv/czjHKXJstnv/kEdTChlsM4yCsKz1YGRkZZhSobTNuqNGqBKsUi+jJJTeNgS2Ncqm1xhtmnfWNyryNSJ+Dn8CgYBJ3L8lDV+Hkt+3UCR7TnoM3xx68j2On6fNFfZCHz4sSyh40EZDTJWOEuZ63frgXIZCuSpDwW3BgMF7AfnHYmSqWklBR4czMXVCYRwZkTSUPxhR5RlUHYKn3U2RBcjVnyl10SI15j/f4JdCG+EdKCBzeZnuMjgCCmao2AellDdWIQKBgQCs2d4teaedc9y8HQS4qArWNc/UP1a+J4cr7H658m0GuvnM25BB35S09930LOxf3htQzVkPjD1MDKlzJezfFzYWZr8DpfzuY10l5gBAy6a8WWss2+wmu3jBNn/32jLywuLQyqXWxSHQ16V0rVqinGpqG+KGnucLNJWbqQvEqiljCwKBgQDJvPYcb+24XvNPLEfM48bSeINBdVdgX3xZp2bbocvpJ86G+3Y/9hXmdXcH8GLcHxR0Vw+tjWa+MB3XUJTs1ytheBJHCVZcOIk4hkxyuk1DorkPfrMdOAaxEa+M4v1pT6sbJEXA81Qv6JsoA98m4aaAau+dGJpMRAUXDQj2D6MFcA==

# Подготовка текстов комментариев

Скачать
wikiextractor

Скачать
Дамп wikipedia (небольшой)
http://gensho.ftp.acc.umu.se/mirror/wikimedia.org/dumps/ruwiki/20190220/ruwiki-20190220-pages-articles5.xml-p3398622p4898622.bz2

./WikiExtractor.py -q -o /home/x1337/Project/wikidata --min_text_length 15000 --ignored_tags abbr,b,big --discard_elements gallery,timeline,noinclude '/home/x1337/Загрузки/ruwiki-20190220-pages-articles5.xml-p3398622p4898622.bz2'

Подготовка статей для комментариев

Выгрузить в небольшие json-файлы

    ./WikiExtractor.py -q -o /home/x1337/Project/wikidata/3 --json --min_text_length 300 --bytes 200K --ignored_tags abbr,b,big,ref,div --discard_elements gallery,timeline,noinclude '/home/x1337/Загрузки/ruwiki-20190220-pages-articles5.xml-p3398622p4898622.bz2' 

Сконвертировать из json в csv

cat /home/x1337/Project/wikidata/3/AA/* | jq .text | tr '\\n' '\n' > comments.csv