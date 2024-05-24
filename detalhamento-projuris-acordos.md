# Detalhamento Projuris Acordos

*Criado por Deivid barbosa
*Atualizado em 24/05/2024

## Objetivo

Trataremos de todos os detalhes do Projuris Acordos, que é uma aplicação multi-tenant completamente preparada para lidar
com vários clientes em simultâneo, isolando todos os dados a nível de aplicação e a nível de banco de dados. Toda a
solução possui escalonamento horizontal para garantir a maior disponibilidade e performance para os clientes.

### Tópicos deste artigo:

1. Segurança
2. Browser
3. Notificação de E-mail
4. Arquitetura
5. Escalonamento
6. Criptografia
7. Configuração da Solução
8. Política de Backup
9. Gerenciamento de Logs
10. Infraestrutura como Código
11. Informações Adicionais

## 1. Segurança

As informações desta seção são fornecidas para auxiliar o usuário no processo de planejamento da segurança. No entanto,
não contém a descrição completa de qualquer recurso de segurança ou nível de suporte.

**Entendendo a comunicação com o servidor do Projuris Acordos:** todas as comunicações com o Projuris Acordos são
realizadas através do protocolo HTTPS com certificado SSL (Secure Socket Layer) para garantir a segurança das
informações trafegadas.

**Isolamento dos dados:** os dados dos usuários são isolados de duas formas:

- **Isolamento a nível de aplicação:** através de controle de tenants, em que todos os dados da base são sempre
  relacionados ao tenant do cliente e todas as consultas subsequentes irão filtrar apenas a informação do tenant em
  específico, impossibilitando um cliente visualizar os dados de outro.

- **Isolamento a nível de banco:** através da técnica de Row Level Security, utilizando essa técnica, adicionamos uma
  validação a nível de banco de dados garantindo que toda transação realizada precisa especificar o tenant do cliente e
  caso os registros estejam relacionados a outro tenant, o banco irá invalidar a transação, impossibilitando a interação
  com os dados.

**Criptografia dos Dados:** todos os dados mantidos pelo Projuris Acordos possuem criptografia em repouso (at rest).
Qualquer informação trafegada para/do Projuris Acordos possui criptografia em trânsito garantida pelo protocolo de
segurança TLS (Transport Layer Security).

## 2. Browser

Os browsers suportados pelo Projuris Empresas são:

- Microsoft Edge 90 ou superior;
- Mozilla Firefox 78 ou superior;
- Google Chrome 89 ou superior.

## 3. Notificação de E-mail

O Projuris Acordos irá notificar usuários da aplicação através do domínio @projuris.acordo.app.

## 4. Arquitetura

A seguir uma visão geral ilustrando o esquema proposto para as soluções utilizadas na plataforma Projuris Acordos e como
cada componente se relaciona, utilizando cluster EKS, serviços da AWS, GitOps, monitoramento, e integrações com
sistemas de IA e APIs externas.

#### Descrição dos Componentes:

1. **VPC privada Acordos**:
	- Ambiente isolado onde os componentes da solução estão hospedados.

2. **Cluster EKS**:
	- Hospeda microserviços, configurserver e o AUTH.
	- Utiliza GitOps (ArgoCD) para sincronização de recursos no Kubernetes, mantendo workloads, configurações e redes
	  atualizadas.
	- Obtém imagens do ECR privado, mantidas atualizadas pelo GitOps.
	- Autenticação de usuários é gerenciada pelo AUTH.

3. **Repositórios de Códigos e CI/CD**:
	- GitHub Actions: cria novas imagens de apps e publica novas versões de SPA.
	- Dependabot e CVE Enhanced Scanner: escaneiam por vulnerabilidades em imagens.

4. **Monitoramento e Alertas**:
	- Better Uptime: monitora timeout de serviços.
	- Papertrail App: análise avançada de logs e alertas.
	- CloudWatch: gerenciamento de alarmes, dashboards e logs.

5. **Armazenamento e Backup**:
	- S3: armazenamento de arquivos de aplicações, backups e bases de dados (bkp e dbs).
	- RDS: base de dados relacional com backup incremental.

6. **Integrações e IA**:
	- Serviços de IA (GCP, OpenAI, groq, Azure) utilizados para entrega de funcionalidades na plataforma e operação.
	- BigQuery: preparação de dados e execução de jobs para dashboards e BI.

7. **Distribuição e Acesso**:
	- CloudFront: distribuição de conteúdo com cache e suporte a CORS.
	- Route 53: gerenciamento de DNS.
	- API Gateway: autenticação e CORS para APIs.

8. **Suporte e Desenvolvimento**:
	- Suporte ao DEV Acordos com dashboards e monitoramento contínuo.
	- Ingestão de logs distribuídos e análises avançadas para feedback contínuo.

9. **Usuário da Plataforma**:
	- Acessa a aplicação e APIs através da infraestrutura gerenciada, com segurança de acesso garantidas
	  por CloudFront e WAF.

#### Fluxo Principal do usuário na plataforma:

- O usuário acessa a aplicação (SPA) hospedada no S3 privado através do CloudFront.
- CloudFront garante a distribuição com cache e suporte a CORS, validando as requisições com WAF front.
- Requisições do usuário são encaminhadas para o Ingress/Gateway que autentica e valida regras (WAF APIs), antes de
  repassar
  para os serviços no Kubernetes.
- Kubernetes gerencia os microserviços, que por sua vez, interagem com os diversos componentes de armazenamento, backup,
  monitoramento, e serviços de IA.
- Alterações no código são refletidas automaticamente nos recursos Kubernetes através do GitOps (ArgoCD).
- Logs e alertas são continuamente monitorados e analisados, fornecendo suporte ao desenvolvimento e operações.

Essa estrutura garante um ambiente escalável, de alta performance, seguro e eficiente para a gestão de grandes volumes
de negociações, suportado por uma integração contínua e monitoramento proativo.

## 5. Escalonamento

Toda a solução é stateless e preparada para escalar horizontalmente de acordo com a demanda de utilização da aplicação,
garantindo maior resiliência e performance para os clientes. Toda a estratégia de escalonamento é gerenciada pelo
Kubernetes.

## 6. Criptografia

Possuímos criptografia em repouso (at rest) para todos os bancos de dados e para os documentos salvos no Object Storage.
Para as bases de dados, a criptografia é garantida a nível de disco lógico pelo provedor Cloud através de uma chave
AES-256. A criptografia dos documentos é fornecida pelo Object Storage do provedor Cloud e a chave é totalmente
gerenciada internamente pelo serviço utilizando as melhores práticas. Toda a comunicação na rede (in transit) é segura e
garantida pelo protocolo de segurança TLS (Transport Layer Security). Para a transferência de informações, é utilizado o
protocolo HTTPS (Hypertext Transfer Protocol Secure).

## 7. Configuração da Solução

Todas as informações dos ambientes da solução são gerenciadas e protegidas por um serviço gerenciador de configurações
com controle de acessos, versionamento e auditoria.

## 8. Política de Backup

Entendendo a importância de manter os dados seguros e acessíveis, são realizados backups diários de todos os dados
armazenados em nossos sistemas. Os arquivos possuem backups gerenciados pelo provedor de infraestrutura e os bancos de
dados possuem backups completos diarios e incrementais em intervalos de 5 minutos.

## 9. Gerenciamento de Logs

Todos os logs da aplicação são mantidos pelo período máximo de 90 dias na nossa ferramenta de gerenciamento. O acesso
aos logs é exclusivo da Projuris para possíveis conferências e auditorias.

## 10. Infraestrutura como Código

Toda a nossa infraestrutura é definida como código e hospedada no nosso serviço de SCM (Source Control Management), o
que nos permite um controle mais detalhado de todos os elementos existentes.

## 11. Informações Adicionais

Este artigo descreve os detalhes de uso comum da solução. É importante salientar que projetos que possuírem necessidades
específicas poderão demandar alteração de requisitos ou itens adicionais. Para mais informações, entre em contato com o
suporte através do nosso [portal do cliente](https://www.projuris.com.br).