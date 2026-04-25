# Шаблоны CI/CD

## Пример использования

1. Добавить в свой пайплайн строки

```yml
include:
  - project: "group/vault-template-repo"
    ref: "v1.0.0"
    file: "/vault-ci-template.yml"
```

2. В каждой джобе, где нужны секреты из данной интеграции добавлять аттрибуты `extends: [".vault-integration"]` и `secrets`. Например, для получения из Vault переменной с именем `NEXUS_PASSWORD` и его сохранения в переменную пайплайна с именем `MY_NEXUS_PASSWORD` произведите следующие изменения:

```yml

...
secrets:
    MY_NEXUS_PASSWORD:
        vault: demo/KUBECONFIG@dcd-kv
        token: $VAULT_ID_TOKEN
        file: false
...

```
3. В рамках данной джобы файл 