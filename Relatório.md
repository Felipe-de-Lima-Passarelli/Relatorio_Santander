# RELATÓRIO DE IMPLEMENTAÇÃO DE SERVIÇOS AWS

**Data:** 18/11/2025  
**Empresa:** Abstergo Industries  
**Responsável:** Felipe de Lima Passarelli

---

## Introdução

Este relatório apresenta o processo de implementação de ferramentas na empresa Abstergo Industries, realizado por Felipe de Lima Passarelli. O objetivo do projeto foi elencar 3 serviços AWS, com a finalidade de realizar diminuição de custos imediatos.

---

## Descrição do Projeto

O projeto de implementação de ferramentas foi dividido em 3 etapas, cada uma com seus objetivos específicos. A seguir, serão descritas as etapas do projeto:

### Etapa 1: Amazon S3

- **Foco da ferramenta:** Armazenamento de arquivos escalável e econômico
- **Descrição de caso de uso:** Migrar documentos internos da empresa para o S3, liberando espaço em servidores físicos e reduzindo custo com manutenção.

### Etapa 2: AWS Lambda

- **Foco da ferramenta:** Processamento serverless
- **Descrição de caso de uso:** Automatizar a geração de relatórios internos, eliminando a necessidade de servidores dedicados e reduzindo gastos com infraestrutura.

### Etapa 3: AWS Cost Explorer

- **Foco da ferramenta:** Monitoramento e otimização de custos
- **Descrição de caso de uso:** Identificar recursos subutilizados e otimizar os planos de serviço, garantindo redução de custos mensais.

---

## Conclusão

A implementação de ferramentas na empresa Abstergo Industries tem como expectativa a redução de custos, aumento da eficiência operacional e maior agilidade nos processos internos. Recomenda-se a continuidade da utilização das ferramentas implementadas e a busca por novas tecnologias que possam melhorar ainda mais os processos da empresa.

---

## Anexos

- Prints de configuração do S3 e Lambda
- Exemplo de função Lambda utilizada no projeto:

### Lambda Function para Processamento de Arquivos S3

Este é um exemplo de função Lambda em Node.js que processa arquivos enviados para um bucket S3.

```javascript
const AWS = require("aws-sdk");
const s3 = new AWS.S3();

exports.handler = async (event) => {
  console.log("Evento recebido:", JSON.stringify(event, null, 2));

  for (const record of event.Records) {
    const bucket = record.s3.bucket.name;
    const key = record.s3.object.key;

    try {
      const params = { Bucket: bucket, Key: key };
      const data = await s3.getObject(params).promise();
      console.log(`Conteúdo do arquivo ${key}:`, data.Body.toString("utf-8"));

      // Aqui você pode adicionar processamento, como renomear, mover ou gerar relatórios
    } catch (err) {
      console.error("Erro ao processar arquivo:", err);
    }
  }

  return { status: "Processamento concluído" };
};
```

Assinatura do Responsável pelo Projeto: Felipe de Lima Passarelli
