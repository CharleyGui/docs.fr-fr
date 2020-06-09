---
title: Activation du flux de transaction
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
ms.openlocfilehash: 5cea72e503087ac2a8f3b6ff2a07c2919ee00630
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597421"
---
# <a name="enabling-transaction-flow"></a>Activation du flux de transaction
Windows Communication Foundation (WCF) offre des options très flexibles pour le contrôle du workflow des transactions. Les paramètres de flux de transaction d'un service peuvent être exprimés à l'aide d'une combinaison d'attributs et de configuration.  
  
## <a name="transaction-flow-settings"></a>Paramètres de flux de transaction  
 Les paramètres de flux de transaction sont générés pour un point de terminaison de service suite à l'intersection des trois valeurs suivantes :  
  
- Attribut <xref:System.ServiceModel.TransactionFlowAttribute> spécifié pour chaque méthode dans le contrat de service.  
  
- Propriété de liaison `TransactionFlow` dans la liaison spécifique.  
  
- Propriété de liaison `TransactionFlowProtocol` dans la liaison spécifique. La propriété de liaison `TransactionFlowProtocol` vous permet de choisir entre deux protocoles de transaction différents que vous pouvez utiliser pour transmettre une transaction. Les sections ci-dessous décrivent brièvement ces deux protocoles.  
  
### <a name="ws-atomictransaction-protocol"></a>Protocole WS-AtomicTransaction  
 Le protocole WS-AtomicTransaction (WS-AT) est utile pour les scénarios où l'interopérabilité avec des piles de protocoles tiers est requise.  
  
### <a name="oletransactions-protocol"></a>Protocole OleTransactions  
 Le protocole OleTransactions est utile pour les scénarios où l'interopérabilité avec les piles de protocoles tiers n'est pas requise et où le responsable du déploiement d'un service sait à l'avance que le service de protocole WS-AT est désactivé localement ou que la topologie du réseau existante ne favorise pas l'utilisation de WS-AT.  
  
 Le tableau ci-dessous indique les différents types de flux de transaction qui peuvent être générés à l'aide de ces différentes combinaisons.  
  
|Liaison<br /><br /> binding|Propriété de liaison TransactionFlow|Protocole de liaison TransactionFlowProtocol|Type de flux de transaction|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Obligatoire|true|WS-AT|La transaction doit être transmise dans le format WS-AT interopérable.|  
|Obligatoire|true|OleTransactions|La transaction doit être transmise au format WCF OleTransactions.|  
|Obligatoire|false|Non applicable|Non applicable parce qu'il s'agit d'une configuration non valide.|  
|Autorisé|true|WS-AT|La transaction peut être transmise dans le format WS-AT interopérable.|  
|Autorisé|true|OleTransactions|La transaction peut être transmise au format WCF OleTransactions.|  
|Autorisé|false|Valeur quelconque|Une transaction n’est pas transmise.|  
|Non autorisé|Valeur quelconque|Valeur quelconque|Une transaction n’est pas transmise.|  
  
 Le tableau ci-dessous résume les résultats de traitement de message.  
  
|Message entrant|Paramètre TransactionFlow|En-tête de transaction|Résultat de traitement du message|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|La transaction correspond au format de protocole prévu|Allowed ou Mandatory|`MustUnderstand` est égal à `true`.|Processus|  
|La transaction ne correspond pas au format de protocole prévu|Obligatoire|`MustUnderstand` est égal à `false`.|Rejet car une transaction est requise|  
|La transaction ne correspond pas au format de protocole prévu|Autorisé|`MustUnderstand` est égal à `false`.|Rejet car l'en-tête n'est pas compris|  
|Transaction utilisant un format de protocole quelconque|Non autorisé|`MustUnderstand` est égal à `false`.|Rejet car l'en-tête n'est pas compris|  
|Aucune transaction|Obligatoire|N/A|Rejet car une transaction est requise|  
|Aucune transaction|Autorisé|N/A|Processus|  
|Aucune transaction|Non autorisé|N/A|Processus|  
  
 Alors que chaque méthode sur un contrat peut avoir des exigences de flux de transaction différentes, le paramètre de protocole de flux de transaction est délimité au niveau de la liaison. Cela signifie que toutes les méthodes qui partagent le même point de terminaison (et par conséquent la même liaison) partagent également la même stratégie qui autorise ou requiert un flux de transaction, ainsi que le même protocole de transaction, le cas échéant.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Activation du flux de transaction au niveau de la méthode  
 Les exigences de flux de transaction ne sont pas toujours les mêmes pour toutes les méthodes dans un contrat de service. Par conséquent, WCF fournit également un mécanisme basé sur les attributs qui permet d’exprimer les préférences de passage de la transaction de chaque méthode. Cela est effectué à l’aide de l’attribut <xref:System.ServiceModel.TransactionFlowAttribute> qui spécifie le niveau dans lequel une opération de service accepte un en-tête de transaction. Vous devez marquer vos méthodes de contrat de service avec cet attribut si vous souhaitez activer le flux de transaction. Cet attribut accepte l'une des valeurs de l'énumération <xref:System.ServiceModel.TransactionFlowOption>, dans laquelle la valeur par défaut est <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>. Si une valeur quelconque à l'exception de <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> est spécifiée, la méthode ne doit pas être unidirectionnelle. Un développeur peut utiliser cet attribut pour spécifier des exigences de flux de transaction ou des contraintes au niveau de la méthode au moment du design.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Activant du flux de transaction au niveau du point de terminaison  
 Outre le paramètre de workflow de transaction au niveau de la méthode <xref:System.ServiceModel.TransactionFlowAttribute> fourni par l’attribut, WCF fournit un paramètre à l’échelle du point de terminaison pour le workflow de transaction afin de permettre aux administrateurs de contrôler le workflow de transaction à un niveau supérieur.  
  
 Cela est effectué à l’aide de <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, qui vous permet d’activer ou de désactiver le flux de transaction entrant dans les paramètres de liaison d’un point de terminaison, ainsi que de spécifier le format de protocole de transaction souhaité pour les transactions entrantes.  
  
 Si le flux de transaction est désactivé pour la liaison, alors qu'une des opérations sur un contrat de service requiert une transaction entrante, une exception de validation est levée au démarrage du service.  
  
 La plupart des liaisons permanentes fournies par WCF contiennent `transactionFlow` les `transactionProtocol` attributs et pour vous permettre de configurer la liaison spécifique pour accepter les transactions entrantes. Pour plus d’informations sur la définition des éléments de configuration, consultez [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) .  
  
 Un administrateur ou un responsable du déploiement peuvent utiliser le flux de transaction au niveau du point de terminaison pour configurer des exigences ou des contraintes de flux de transaction au moment du déploiement, à l’aide du fichier de configuration.  
  
## <a name="security"></a>Sécurité  
 Pour garantir la sécurité et l’intégrité du système, vous devez sécuriser les échanges de messages lorsque vous transmettez des transactions entre des applications. Vous ne devez pas transmettre ni divulguer les détails d’une transaction à toute application qui n’est pas habilitée à participer à cette même transaction.  
  
 Lors de la génération de clients WCF sur des services Web inconnus ou non approuvés par le biais de l’échange de métadonnées, les appels aux opérations sur ces services Web doivent supprimer la transaction actuelle si possible. L'exemple suivant illustre la procédure à suivre pour réaliser cette opération.  
  
```csharp
//client code which has an ambient transaction  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Suppress))  
{  
    // No transaction will flow to this operation  
    untrustedProxy.Operation1(...);  
    scope.Complete();  
}  
//remainder of client code  
```  
  
 De plus, les services doivent être configurés pour accepter les transactions entrantes uniquement à partir de clients qu'ils ont authentifiés et autorisés. Les transactions entrantes doivent être acceptées uniquement si elles proviennent de clients hautement approuvés.  
  
## <a name="policy-assertions"></a>Assertions de stratégie  
 WCF utilise des assertions de stratégie pour contrôler le workflow de transaction. Les assertions de stratégie se trouvent dans le document de stratégie d'un service, lequel est généré en regroupant les contrats, la configuration et les attributs. Le client peut obtenir le document de stratégie du service à l'aide d'une commande HTTP GET ou d'une demande-réponse WS-MetadataExchange. Les clients peuvent alors traiter le document de stratégie pour déterminer quelles opérations sur un contrat de service peuvent prendre en charge ou requérir le flux de transaction.  
  
 Les assertions de stratégie de flux de transaction affectent le flux de transaction en spécifiant les en-têtes SOAP qu’un client doit envoyer à un service pour représenter une transaction. Tous les en-têtes de transaction doivent être marqués avec `MustUnderstand` égal à `true`. Tout message avec un en-tête marqué autrement est rejeté avec une erreur SOAP.  
  
 Une seule assertion de stratégie liée aux transactions peut être présente sur une opération unique. Les documents de stratégie avec plus d’une assertion de transaction sur une opération sont considérés comme non valides et sont rejetés par WCF. De plus, seul un protocole de transaction unique peut être présent au sein de chaque type de port. Les documents de stratégie avec des opérations faisant référence à plusieurs protocoles de transaction à l’intérieur d’un type de port unique sont considérés comme non valides et sont rejetés par l' [outil ServiceModel Metadata Utility (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Les documents de stratégie avec des assertions de transaction présentes sur les messages de sortie ou les messages d’entrée unidirectionnels sont également considérés non valides.
