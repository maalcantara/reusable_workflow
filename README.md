# Reusing Workflows ♾️

Um Workflow reutilizável é um conjunto de jobs e staps que pode ser compartilhado e executado em vários repositórios. 

- Permite a padronização e evita a duplicação de código, facilitando a manutenção nos pipelines CI/CD.

⚠️ **Importante:** ao utillizar um workflow reutilizável, criar um `Job` separado para ele.

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
◻️ Neste exemplo utilizei o repositório [dotnet-webapi](https://github.com/maalcantara/dotnet-webapi).

```
{owner}/{repo}/.github/workflows/{filename}@{ref}
```
#### O {ref} pode ser:

- **Release Tag:** usar uma tag de versão específica do repositório. Ex: `uses: maalcantara/reusable_workflow/.github/workflows/setup-dotnet-sdk.yml@v1.0.0`

- **Branch name:** usar a branch específica. Ex: `uses: maalcantara/reusable_workflow/.github/workflows/setup-dotnet-sdk.yml@main`

- **Commit SHA:** usar o hash de um commit específico. Ex `uses: maalcantara/reusable_workflow/.github/workflows/setup-dotnet-sdk.yml@8151835`

## Workflows
| Pipeline yml       | Resumo          | Repositórios que o utilizam|
|-------------------|-----------------|-------------------|
| [my-starter-workflow-1](https://github.com/maalcantara/reusable_workflow/blob/main/.github/workflows/my-starter-workflow-1.yml) | Apenas teste, reutiliza a pipeline abaixo.| |
| [reusable-workflow-1](https://github.com/maalcantara/reusable_workflow/blob/main/.github/workflows/reusable-workflow-1.yml) | Apenas teste, comando `echo "I am a Reusable Workflow One".| |
| [setup-dotnet-sdk](https://github.com/maalcantara/reusable_workflow/blob/main/.github/workflows/setup-dotnet-sdk.yml) | Instala o SDK do .NET Core, e precisa de um imput especificando qual versão do dotnet para instalar.| [DevOps_Challenge](https://github.com/maalcantara/DevOps_Challenge/tree/reusable-workflows), [dotnet-webapi](https://github.com/maalcantara/dotnet-webapi)|