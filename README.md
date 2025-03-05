# Desafio VExpenses
## Relatórios do Projeto

- [Relatório sobre o código inicial](https://docs.google.com/document/d/1ztwLi9uMWa4cirQU_gdqo8JHo58nElLvsx9_UsKnibI/edit?usp=sharing)
- [Relatório sobre o código modificado](https://docs.google.com/document/d/1iW6BNfFUo-S3i9bNFNkN2bg9u_KO6VSOFgxc0NbjMDQ/edit?usp=sharing)
## Pré-requisitos para executar o projeto

Antes de começar, certifique-se de ter os seguintes itens instalados:

- [Terraform](https://www.terraform.io/downloads.html)
- [Git](https://git-scm.com/downloads)

## Passo a Passo

### 1. Clonar o Repositório

Primeiro, clone o repositório do projeto para o seu ambiente local:

```sh
git clone <https://github.com/GabryelCardoso/Desafio-VExpenses.git>
cd <Desafio-VExpenses>
```

### 2. Inicializar o Terraform

Inicialize o Terraform no diretório do projeto:

```sh
terraform init
```

### 3. Baixar as Dependências

O comando `terraform init` já baixa todas as dependências necessárias. Caso precise atualizar as dependências, utilize:

```sh
terraform get
```

### 4. Configurar a AWS

Antes de configurar, certifique-se de ter o AWS CLI instalado. Você pode baixar e instalar o AWS CLI a partir do [site oficial](https://aws.amazon.com/cli/).

Configure suas credenciais da AWS para que o Terraform possa provisionar recursos na AWS:

```sh
aws configure
```

Você será solicitado a inserir suas credenciais da AWS, incluindo:

- AWS Access Key ID
- AWS Secret Access Key
- Default region name (por exemplo, us-east-1)
- Default output format (por exemplo, json)

### 5. Alterar a variável `local_ip`

Abra o arquivo `main.tf` e altere o valor default da variável `local_ip` para o endereço IPv4 da sua máquina local. O arquivo deve ficar parecido com o exemplo abaixo:

```hcl
variable "local_ip" {
    description = "IP local da sua máquina"
    type        = string
    default     = "ipv4_local"  # Substitua pelo seu endereço IPv4
}
```

Certifique-se de salvar o arquivo após fazer a alteração.
### 5. Planejar a Infraestrutura

Gere e revise o plano de execução da infraestrutura:

```sh
terraform plan
```

### 6. Aplicar o Plano

Aplique o plano para provisionar a infraestrutura:

```sh
terraform apply
```

### 7. Destruir a Infraestrutura

Para destruir a infraestrutura provisionada, utilize:

```sh
terraform destroy
```


## Conclusão

O objetivo do código `main.tf` é definir e provisionar a infraestrutura necessária para o projeto utilizando o Terraform. Ele especifica os recursos da AWS que serão criados, que são: vpc, sub-rede, gateway de internet, tabela de rotas, associação da tabela de rotas, grupo de segurança e uma instância EC2 com um servidor NGINX automatizado.
