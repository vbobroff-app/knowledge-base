
```bash
# Применяем только Contabo модуль, игнорируя Yandex
terraform apply -target="module.vps_contabo_simple" -auto-approve
```


```bash
terraform-vpn-infra/
├── .config/.ya/ya.tfvars              # Центральный файл
├── contabo/
│   ├── main.tf
│   └── variables.tf
└── yandex/
    ├── main.tf
    └── variables.tf
```

```bash
terraform plan -var-file="../.config/ya/.ya.tfvars"
terraform plan -var-file="../.config/cntb/.cntb.tfvars"
```
