# devops-jenkins

🔧 Pipeline CI/CD com **Jenkins** rodando em container Docker.

## Stack

- **Jenkins LTS** — servidor de automação
- **Docker Compose** — orquestra o container do Jenkins
- **Groovy** — linguagem do `Jenkinsfile`

## Arquivos

| Arquivo | Descrição |
|---|---|
| `docker-compose.yml` | Sobe o Jenkins LTS com volume persistente |
| `Jenkinsfile` | Pipeline declarativo (checkout, build, test, deploy) |

## Como executar

```bash
# Subir o Jenkins
docker compose up -d

# Acessar a interface
# → http://localhost:8080

# Pegar a senha inicial
docker exec jenkins cat /var/jenkins_home/secrets/initialAdminPassword
```

Após o setup inicial:

1. Instale os plugins recomendados
2. Crie um usuário admin
3. Crie uma nova **Pipeline** apontando para este repositório
4. Use o `Jenkinsfile` da raiz como definição

## Pipeline (Jenkinsfile)

O pipeline declarativo executa os estágios:

1. **Checkout** — clone do repositório
2. **Build** — compilação / build da imagem Docker
3. **Test** — execução de testes automatizados
4. **Deploy** — push para registry ou deploy

## Comparação com GitHub Actions

Este repositório complementa o `devops-testing` (que usa GitHub Actions) demonstrando o **mesmo conceito de CI/CD** com uma ferramenta auto-hospedada — útil quando a empresa exige que o build não saia da rede interna.

## Autor

**Henrique Sattolo** — [github.com/henriquesattolo](https://github.com/henriquesattolo)
