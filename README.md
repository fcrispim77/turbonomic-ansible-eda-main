
## Integração Turbonomic EDA - Jira
## Forked by Fabio Crispim
## Scaleup Consultoria - April 2024
## Ansible Collection: turbonomic_eda

This IBM Turbonomic Ansible Collection provides examples that can be used to automate Turbonomic cloud scaling decisions using Event Driven Ansible (EDA). Users are able to quickly realize the value of Turbonomic Hybrid Cloud optimization decisions by leveraging the flexible and powerful automation capabilities of Event Driven Ansible.


## Adicionado módulo para criação de Tickets no Jira

Ambientes envolvidos:

1. IBM Turbonomic
2. Event Driven Ansible
3. Ansible Controller
4. JIra

## Included in the Collection
- Module to create a webhook workflow within your Turbonomic Instance for use in Automation Policies
- Role for resizing an AWS EC2 instance via the Ansible module amazon.aws.ec2_instance and aws cli
- Role for resizing an Azure Virtual Machine via the Ansible module azure.azcollection.azure_rm_virtualmachine
- Playbooks for Event Driven Ansible to call to execute the roles
- Sample Event Driven Ansible Rulebook

## Prequisite
The following are required on the Event Driven Ansible Rulebook server in order to execute the playbooks and
roles from this collection.

### Install Necessary Ansible Collections

```
ansible-galaxy collection install ansible.eda azure.azcollection amazon.aws
```

### Install Necessary Python Software

```
python3 -m pip install awscli
```

## Installing the Collection

```
ansible-galaxy collection install ibm.turbonomic_eda
```

## Passo a Passo de Configuração da Integração
```
1. Configurando EDA
	1. Acesse o portal web do EDA controller para configurar o Turbonomic EDA
	2. Criar um projeto
		1. Name: Project EDA Turbonomic Jira
		2. SCM URL:  (Apontar para um repositório Git/Bitbucket)
		3. Credentials: (opcional)
		4. Criado projeto, vá para Rulebook activation
	3. Criando Rulebook activation
		1. Nome: Rulebook  EDA Turbonomic Jira
		2. Project: Project EDA Turbonomic Jira
		3. Rulebook: eda_turbonomic.yml
		4. Decision Environment: (a definir)
		5. Salve o novo rulebook e aguarde seu status ficar "RUNNING"
2. Configurar Automation Controller
	1. Acesso o portal web do Automation Controller para configurar a execução dos playbooks
	2. Criar um projeto
		1. Name: Playbooks EDA Turbonomic Jira
		2. Organization: Default
		3. Execution Environment: (a definir)
		4. Source Control Type: Git
		5. Source Control URL:  (Apontar para um repositório Git/Bitbucket)
		6. Credentials: (opcional)
		7. Salve o projeto e aguarde o está de sincronizado
	3. Criar uma template
		1. Name: Playbook Template EDA Turbonomic Jira
		2. Inventory: localhost 
		3. Project: Playbooks EDA Turbonomic Jira
		4. Execution Environment: (a definir)
		5. Playbook: playbook_turbonomic_eda_webhook.yml
		6. Credentials: (Crie credendicais para o Jira e associe aqui)
		7. Salve a template
3. Configurar Turbonomic (Em construção)
4. Testar rulebooks para ações no Bitbucket (Em construção)