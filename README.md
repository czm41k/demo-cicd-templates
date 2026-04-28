# Шаблоны CI/CD

## Пример использования

1. Добавить в свой пайплайн строки

```yml
include:
  - project: "demo-evgenii/cicd-templates"
    ref: "main"
    file: "/vault-ci-template.yml"
```

2. В каждой джобе, где нужны секреты из данной интеграции добавлять аттрибуты `extends: [".vault-integration"]` и `secrets`. Например, для получения из Vault переменной с именем `SECRET` по адресу `SECRET_PATH` в `MY-KV` хранилище и его сохранения в переменную пайплайна с именем `MY_SECRET` произведите следующие изменения:

```yml

...
secrets:
    MY_SECRET:
        vault: SECRET_PATH/SECRET@MY-KV
        token: $VAULT_ID_TOKEN
        file: false
...

```
3. В рамках данной джобы файл... TBD
