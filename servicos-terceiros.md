# Documento de serviços de terceiros utilizados na plataforma Projuris Acordos

**Data:** 20/05/2024
**Responsável:** Deivid Barbosa

## Introdução

Este documento detalha os serviços de terceiros integrados em nossa plataforma SAAS. As integrações descritas aqui são
essenciais para o funcionamento e a oferta de funcionalidades da plataforma. Este material serve como apoio para a
equipe de Segurança da Informação.

## Serviços de Terceiros

1. **Enriquecimento de Dados de Pessoa**
	- **Assertiva Soluções**
		- **Descrição:** Serviço de enriquecimento de dados pessoais (nome, emails, telefones), fornecendo informações
		  adicionais e relevantes
		  para a base de dados dos usuários.
		- **Integração:** Realizada através de APIs.
	- **NovaVida**
		- **Descrição:** Similar à Assertiva, a NovaVida também oferece enriquecimento de dados pessoais (nome, emails,
		  telefones), garantindo a
		  atualização e a precisão das informações.
		- **Integração:** Realizada através de APIs.

2. **Enriquecimento de Processo**
	- **Jusbrasil**
		- **Descrição:** Fornece informações e documentos relacionados a processos jurídicos, os dados são obtidos
		  diretamente dos tribunais e disponibilizados via API.
		- **Integração:** Realizada através de APIs da Jusbrasil.
	- **Codillo**
		- **Descrição:** Fornece informações e documentos relacionados a processos jurídicos, os dados são obtidos
		  diretamente dos tribunais e disponibilizados via API.
		- **Integração:** Realizada através de APIs da Codilo.

3. **Confecção de Minuta**
	- **Google Docs API**
		- **Descrição:** Utilizamos a API do Google Docs para a confecção de minutas de acordos.
		- **Integração:** As solicitações são realizadas diretamente pela API do Google Docs. O usuário pode acessar
		  diretamente o documento utilizando o endereço da própria ferramenta do Google.

4. **Assinatura de Minuta**
	- **Lacuna software**
		- **Descrição:** Integração para assinatura digital de minutas de documentos, garantindo a validade legal.
		- **Integração:** Realizada atravez de APIs.

5. **Discador**
	- **Code7**
		- **Descrição:** Utilizamos o serviço de discagem da Code7 nas comunicações telefônicas
		  de nossos clientes. A integração permite que as ligações sejam realizadas diretamente via navegador.
		- **Integração:** As solicitações são realizadas diretamente com a API da Code7, quando tudo foi resolvido via
		  APIs, entregamos a ligação para o usuário em seu navegador. A conexão é feita diretamente com o servidor da
		  Code7 a partir do navegador do usuário.
6. **Envio de SMS**
	- **Facilita móvel**
		- **Descrição:** Utilizamos o serviço de envio de SMS da faclita móvel para comunicações com nossos clientes.
		- **Integração:** As solicitações são realizadas diretamente com a API da facilita.
7. **Envio de E-mail**
	- **SendGrid**
		- **Descrição:** Utilizamos o serviço de envio de e-mails da SendGrid para comunicações com nossos clientes.
		- **Integração:** As solicitações são realizadas diretamente com a API da SendGrid.
8. **Armazenamento de Documentos**
	- **Amazon S3**
		- **Descrição:** Utilizamos o serviço de armazenamento de documentos da Amazon S3 para guardar os documentos
		  gerados na plataforma, assim como anexos que são compartilhados nas disputas e enriquecidos dos tribunais.
		- **Integração:** As solicitações são realizadas diretamente com a API da Amazon S3.
9. **Envio de WhatsApp**
	- **Gupshup**
		- **Descrição:** Utilizamos o serviço de envio de mensagens via WhatsApp da Gupshup para comunicações com nossos
		  clientes. O Gupshup é um BSP (Provedor de Soluções de Negócios do facebook busciness -
		  ref: https://faq.whatsapp.com/695500918177858/?helpref=hc_fnav&locale=pt_BR)
		- **Integração:** As solicitações são realizadas diretamente com a API da Gupshup.
10. **AWS**
	- **Descrição:** Utilizamos os serviços da AWS para hospedagem de nossa aplicação, banco de dados e armazenamento de
	  arquivos.
		- **Integração:** Todas as solicitações são realizadas diretamente com a API e SDK da AWS.

11. **OpenAI**
	- **Descrição:** Utilizamos o serviços de IA da OpenAI para aprimorar a experiência do usuário e a eficiência da
	  plataforma. Estes serviços são utilizados em módulos opcionais de respostas automáticas e extração de dados de
	  documentos.
		- **Integração:** As solicitações são realizadas diretamente com a API da OpenAI.

## Proteção de dados

Contamos com o apoio do time de proteção de dados da Softplan, que mantém de forma sistemica o portal de LGPD de todas
as ofertas do grupo. Eles podem apoiar em qualquer dúvida ou necessidade de informações adicionais relacionadas à
proteção de dados.
Favor manter o email protecaodedados@softplan.com.br em cópia em qualquer solicitação. Além de manter o histórico das
comunicações, eles podem e vão nos apoiar com muito mais profundidade nos temas que forem necessários desdobra-los.

## Nossas considerações
As integrações são fundamentais para o funcionamento de nossa plataforma. Cada serviço foi escolhido
com base em critérios de qualidade e segurança, para que possamos garantir que estamos oferecendo uma solução completa e
confiável aos nossos clientes.

Para qualquer dúvida ou necessidade de informações adicionais, favor entrar em contato.



