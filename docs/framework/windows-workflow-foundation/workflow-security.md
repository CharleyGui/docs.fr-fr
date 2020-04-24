---
title: Sécurité de workflow
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], workflow security
ms.assetid: d712a566-f435-44c0-b8c0-49298e84b114
ms.openlocfilehash: 2a9b26f8da7616480f69a6c4580b8d351833c9ee
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646314"
---
# <a name="workflow-security"></a>Sécurité de workflow
Windows Workflow Foundation (WF) est intégré à plusieurs technologies différentes, telles que Microsoft SQL Server et Windows Communication Foundation (WCF). L'interaction avec ces technologies peut poser des problèmes de sécurité dans votre workflow si elle est effectuée de façon incorrecte.

## <a name="persistence-security-concerns"></a>Problèmes de sécurité de la persistance

1. Les flux de travail qui utilisent une activité <xref:System.Activities.Statements.Delay> et la persistance doivent être réactivés par un service. Windows AppFabric utilise le service de gestion de flux de travail (WMS) pour réactiver les flux de travail dont les minuteurs ont expiré. WMS crée un <xref:System.ServiceModel.WorkflowServiceHost> pour héberger le flux de travail réactivé. Si le service WMS est arrêté, les workflows persistants ne seront pas réactivés à l'expiration de leurs minuteurs.

2. L'accès à l'instanciation durable doit être protégé contre les entités malveillantes externes au domaine d'application. En outre, les développeurs doivent veiller à ce qu'il soit impossible d'exécuter du code malveillant dans le même domaine d'application que celui du code d'instanciation durable.

3. L'instanciation durable ne doit pas être exécutée avec des autorisations élevées (administrateur).

4. Les données traitées en dehors du domaine d'application doivent être protégées.

5. Les applications qui requièrent l'isolation de sécurité ne doivent pas partager la même instance d'abstraction de schéma. De telles applications doivent utiliser des fournisseurs de magasins différents, ou enregistrer les fournisseurs configurés pour utiliser des instanciations différentes du magasin.

## <a name="sql-server-security-concerns"></a>Problèmes de sécurité SQL Server

- Lors de l'utilisation d'un grand nombre d'activités enfants, d'emplacements, de signets, d'extensions hôtes ou d'étendues, ou de signets avec des charges utiles très importantes, la mémoire peut être épuisée ou des quantités inutiles d'espace de base de données peuvent être allouées pendant la persistance. Cette situation peut être atténuée en utilisant la sécurité aux niveaux objet et base de données.

- Lors de l'utilisation de <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, le magasin d'instances doit être sécurisé.

- Les données sensibles dans le magasin d'instances doivent être chiffrées. Pour plus d’informations, consultez [SQL Server Encryption](/sql/relational-databases/security/encryption/sql-server-encryption)

- Étant donné que la chaîne de connexion à une base de données est souvent incluse dans un fichier de configuration, la sécurité au niveau fenêtre (ACL) doit être utilisée pour vérifier que le fichier de configuration (Web.Config généralement) est sécurisé, et que les informations de connexion et de mot de passe ne sont pas incluses dans la chaîne de connexion. L'authentification Windows doit être utilisée entre la base de données et le serveur Web à la place.

## <a name="considerations-for-workflowservicehost"></a>Considérations sur WorkflowServiceHost

- Les paramètres de la Windows Communication Foundation (WCF) utilisés dans les flux de travail doivent être sécurisés. Pour plus d’informations, voir [WCF Security Overview](../wcf/feature-details/security-overview.md).

- L'autorisation au niveau hôte peut être implémentée à l'aide de <xref:System.ServiceModel.ServiceAuthorizationManager>. Voir [comment : Créer un gestionnaire d’autorisation personnalisée pour un service](../wcf/extending/how-to-create-a-custom-authorization-manager-for-a-service.md) pour plus de détails.

- Le ServiceSecurityContext pour le message entrant est également disponible dans le workflow en accédant à OperationContext.

## <a name="wf-security-pack-ctp"></a>WF Security Pack CTP
 Le Microsoft WF Security Pack aperçu de la technologie communautaire (CTP) 1 est un ensemble d’activités et leur mise en œuvre basée sur [Windows Workflow Foundation](index.md) dans [.NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w0x726c2(v=vs.100)) (WF 4) et [Windows Identity Foundation (WIF)](https://docs.microsoft.com/previous-versions/dotnet/framework/security/index). Microsoft WF Security Pack CTP 1 contient les deux activités et leurs concepteurs qui expliquent comment vérifier facilement plusieurs scénarios liés à la sécurité en utilisant un workflow, notamment :

1. Emprunter l'identité d'un client dans le workflow

2. Autorisation dans-le workflow, telle que PrincipalPermission et validation des revendications

3. Messagerie authentifiée en utilisant les ClientCredentials spécifiés dans le workflow, tels que le nom d'utilisateur/mot de passe ou un jeton extrait d'un service d'émission de jeton de sécurité (STS)

4. Transfert d'un jeton de sécurité client vers un service principal (délégation basée sur les revendications) à l'aide de WS-Trust ActAs

Pour plus d’informations et pour télécharger le WF Security Pack CTP, voir: [WF Security Pack CTP](https://archive.codeplex.com/?p=wf)
