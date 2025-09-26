# ArquiteturaEC2-AWS

📌 Conceito rápido dos serviços envolvidos

S3 (Simple Storage Service):
Armazenamento de objetos (imagens, arquivos, documentos). Muito usado para hospedar estáticos ou servir como “bucket de entrada” de dados.

EC2 (Elastic Compute Cloud):
Servidor virtual. Você sobe aplicações, bancos de dados ou serviços que precisam de controle total do sistema operacional.

Lambda Function:
Funções serverless. Executa código em resposta a eventos (ex.: upload no S3 dispara uma função para processar imagem). Não precisa de servidor fixo.

EBS (Elastic Block Store):
Volume de disco persistente que você anexa a uma instância EC2 (como se fosse o HD dela).

📌 Um fluxo de arquitetura simples

Um cenário clássico para juntar esses serviços seria:

Usuário faz upload de um arquivo (ex.: imagem ou PDF) em um bucket no S3.

O S3 gera um evento → dispara uma Lambda Function.

A Lambda processa o arquivo (ex.: redimensiona imagem, extrai metadados, gera relatório).

Se for necessário processamento mais pesado ou banco de dados, a Lambda envia para a instância EC2, que tem EBS anexado para armazenamento persistente.

O resultado processado pode ser:

Salvo novamente no S3 (para acesso público/download).

Ou armazenado em disco (EBS) dentro da EC2.
