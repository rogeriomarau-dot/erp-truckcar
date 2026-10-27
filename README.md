# ERP Truckcar

Sistema de gestão financeira da Truckcar Centro Automotivo (Portão/RS), desenvolvido por Finance Gestão Pro.

- **Hospedagem:** Firebase Hosting (projeto `erp-truckcar`)
- **Banco de dados:** Cloud Firestore, região `southamerica-east1` (São Paulo)
- **Login:** Firebase Authentication (e-mail e senha)
- **Permissões:** tela "Usuários e permissões" do ERP + regras do servidor em `firestore.rules`

## Estrutura

```
public/index.html        o ERP (tela, regras de negócio e conexão com o Firebase)
firestore.rules          regras de segurança do banco (quem lê e grava o quê)
firestore.indexes.json   índices do banco (vazio por enquanto)
firebase.json            configuração da hospedagem
.firebaserc              aponta para o projeto erp-truckcar
```

## Publicar (deploy)

Pré-requisito, uma vez só no computador: Node.js LTS (nodejs.org) e a ferramenta do Firebase.

```
npm install -g firebase-tools
firebase login
```

Depois, dentro da pasta do projeto:

```
firebase deploy
```

Isso publica o site e as regras de segurança. Endereço: https://erp-truckcar.web.app

Para publicar só uma parte: `firebase deploy --only hosting` ou `firebase deploy --only firestore:rules`.

## Primeiro acesso

1. Abra o endereço do ERP e toque em **Primeiro acesso: criar administrador**.
2. Informe nome, e-mail e senha. Essa conta vira a administradora do sistema.
3. A opção de primeiro acesso some depois disso: os demais usuários são criados pelo administrador em **Administração › Usuários e permissões**.

## Migração dos dados

Com o administrador logado: **Configurações › Carregar backup** e escolha o arquivo de backup (.html) gerado pelo ERP anterior.

## Backup

O plano gratuito do Firebase não tem backup automático. Use o botão **Backup** do topo do ERP pelo menos uma vez por semana e guarde o arquivo.
