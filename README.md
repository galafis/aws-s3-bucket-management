# 🪣 AWS S3 Bucket Management

[![AWS](https://img.shields.io/badge/AWS-S3-orange?logo=amazon-aws)](https://aws.amazon.com/s3/)
[![DIO](https://img.shields.io/badge/DIO-AWS%20Cloud%20Foundations-blue)](https://web.dio.me)
[![Python](https://img.shields.io/badge/Python-3.8%2B-green?logo=python)](https://python.org)

Projeto prático do curso **AWS Cloud Foundations** (DIO/TQI) — Criando e gerenciando buckets no Amazon S3 com versionamento, upload de arquivos e configurações de acesso.

## 📋 Sobre o Projeto

Este repositório documenta o laboratório prático de criação e gerenciamento de buckets no **Amazon Simple Storage Service (S3)**, cobrindo desde a criação do bucket até configurações avançadas como versionamento e políticas de acesso.

## 🎯 Objetivos

- Criar um bucket S3 com nome único globalmente
- Fazer upload de arquivos e pastas via console AWS
- Habilitar versionamento para controle de histórico de arquivos
- Configurar permissões e políticas de acesso
- Utilizar Git Bash para interações via linha de comando

## 🏗️ Arquitetura

```
AWS Account
└── Amazon S3
    └── Bucket (nome único global)
        ├── Objetos/Arquivos
        ├── Versionamento (enabled)
        ├── Políticas de bucket
        └── ACLs de acesso
```

## 🚀 Funcionalidades Demonstradas

### 1. Criação do Bucket
- Nome globalmente único
- Seleção de região AWS
- Configuração de bloqueio de acesso público

### 2. Upload de Arquivos
- Upload via console web da AWS
- Upload de múltiplos arquivos e pastas
- Configuração de metadados

### 3. Versionamento
- Habilitação do versionamento no bucket
- Recuperação de versões anteriores
- Gerenciamento de versões deletadas

### 4. Controle de Acesso
- Políticas de bucket (Bucket Policies)
- ACLs (Access Control Lists)
- Configuração de acesso público/privado

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Descrição |
|---|---|
| Amazon S3 | Armazenamento de objetos na nuvem |
| AWS Console | Interface web de gerenciamento |
| Git Bash | Terminal para operações via CLI |
| AWS CLI | Linha de comando da AWS |

## 📁 Estrutura do Repositório

```
aws-s3-bucket-management/
├── README.md
├── scripts/
│   ├── create_bucket.sh
│   ├── upload_files.sh
│   └── enable_versioning.sh
├── policies/
│   └── bucket_policy.json
└── docs/
    └── tutorial.md
```

## 📖 Como Usar

### Pré-requisitos
- Conta AWS ativa
- AWS CLI configurado
- Git Bash instalado

### Criando um Bucket via AWS CLI

```bash
# Criar bucket
aws s3 mb s3://meu-bucket-unico-123 --region us-east-1

# Listar buckets
aws s3 ls

# Habilitar versionamento
aws s3api put-bucket-versioning \
  --bucket meu-bucket-unico-123 \
  --versioning-configuration Status=Enabled

# Upload de arquivo
aws s3 cp arquivo.txt s3://meu-bucket-unico-123/

# Upload de pasta inteira
aws s3 sync ./pasta/ s3://meu-bucket-unico-123/pasta/
```

### Política de Bucket (Exemplo)

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "PublicReadGetObject",
      "Effect": "Allow",
      "Principal": "*",
      "Action": "s3:GetObject",
      "Resource": "arn:aws:s3:::meu-bucket-unico-123/*"
    }
  ]
}
```

## 📚 Conceitos Aprendidos

- **S3** aceita qualquer tipo de arquivo (não apenas PNG ou texto)
- Nomes de bucket são **globalmente únicos** — não é possível criar dois buckets com o mesmo nome
- O **versionamento** permite recuperar arquivos modificados ou deletados
- Upload pode ser feito via **console web**, **AWS CLI** ou **SDKs**
- **Políticas de bucket** controlam quem pode acessar os objetos

## 🏆 Certificação

Este projeto faz parte do bootcamp **TQI - Modernização com GenAI** na plataforma DIO, contribuindo para a formação em **AWS Cloud Foundations**.

## 👨‍💻 Autor

**Gabriel Galafis**
- GitHub: [@galafis](https://github.com/galafis)
- LinkedIn: [gabriel-galafis](https://linkedin.com/in/gabriel-galafis)

---

*Desenvolvido como parte da Formação AWS Cloud Foundations — DIO/TQI 2025*
