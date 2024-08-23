# Reusing Workflows ♾️

Um Workflow reutilizável é um conjunto de jobs e staps que pode ser compartilhado e executado em vários repositórios. 

- Permite a padronização e evita a duplicação de código, facilitando a manutenção nos pipelines CI/CD.

## Reutilizando workflows do mesmo repositório

### `my-starter-workflow-1.yml`
Este é o workflow principal, que é configurado para ser executado manualmente através do evento `workflow_dispatch`. Dentro desse workflow, há um job que utiliza o workflow reutilizável definido no arquivo `reusable-workflow-1.yml`
```
call-workflow-in-local-repo:
  uses: ./.github/workflows/reusable-workflow-1.yml
```

### `reusable-workflow.yml`
Este é o workflow reutilizável, ele está configurado para ser chamado por outros workflows através do evento `workflow_call`.

## Reutilizando workflows em repositórios diferentes.
◻️ Neste exemplo utilizei o repo [dotnet-webapi](https://github.com/maalcantara/dotnet-webapi).

- **call-workflow-using-release:** 

- **call-workflow-using-branch:**

- **call-workflow-using-sha:**
