---
title: Développement de services de workflow « contrat en premier »
ms.date: 03/30/2017
ms.assetid: e5dbaa7b-005f-4330-848d-58ac4f42f093
ms.openlocfilehash: e46cabd7446fc5f2b0a4b54c6a59230565e72f34
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660665"
---
# <a name="contract-first-workflow-service-development"></a>Développement de services de workflow « contrat en premier »

Fonctionnalités de Windows Workflow Foundation (WF) à compter de .NET Framework 4.5, une meilleure intégration entre les services web et des flux de travail sous la forme du développement de workflow contrat en premier. L'outil de développement de workflow Contrat en premier vous permet de concevoir le contrat dans le code en premier. L'outil génère automatiquement un modèle d'activité dans la boîte à outils pour les opérations du contrat. Cette rubrique fournit une vue d'ensemble de la façon dont les activités et les propriétés d'un service de workflow sont mappées aux attributs d'un contrat de service. Pour obtenir un exemple pas à pas de création d’un service de workflow contrat en premier, consultez [Comment : Créer un service de flux de travail qui utilise un contrat de service existant](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).

## <a name="in-this-topic"></a>Dans cette rubrique

- [Mappage des attributs de contrat de service aux attributs de flux de travail](contract-first-workflow-service-development.md#MappingAttributes)

  - [Attributs de contrat de service](contract-first-workflow-service-development.md#ServiceContract)

  - [Attributs de contrat d’opération](contract-first-workflow-service-development.md#OperationContract)

  - [Attributs de contrat de message](contract-first-workflow-service-development.md#MessageContract)

  - [Attributs de contrat de données](contract-first-workflow-service-development.md#DataContract)

  - [Attributs de contrat d’erreur](contract-first-workflow-service-development.md#FaultContract)

- [Prise en charge supplémentaire et des informations d’implémentation](contract-first-workflow-service-development.md#AdditionalSupport)

  - [Fonctionnalités de contrat de service non pris en charge](contract-first-workflow-service-development.md#UnsupportedFeatures)

  - [Génération d’activités de messagerie configurées](contract-first-workflow-service-development.md#ActivityGeneration)

## <a name="MappingAttributes"></a> Mappage des attributs de contrat de service aux attributs de flux de travail

Les tableaux des sections suivantes spécifient différents attributs et propriétés WCF et comment ils sont mappés aux activités de messagerie et aux propriétés dans un workflow contrat en premier.

- [Attributs de contrat de service](contract-first-workflow-service-development.md#ServiceContract)

- [Attributs de contrat d’opération](contract-first-workflow-service-development.md#OperationContract)

- [Attributs de contrat de message](contract-first-workflow-service-development.md#MessageContract)

- [Attributs de contrat de données](contract-first-workflow-service-development.md#DataContract)

- [Attributs de contrat d’erreur](contract-first-workflow-service-development.md#FaultContract)

### <a name="ServiceContract"></a> Attributs de contrat de service

|Nom de la propriété|Prise en charge|Description|Validation WF|
|-------------------|---------------|-----------------|-------------------|
|CallbackContract|Non|Obtient ou définit le type de contrat de rappel lorsque le contrat est un contrat duplex.|(N/A)|
|ConfigurationName|Non|Obtient ou définit le nom utilisé pour localiser le service dans un fichier de configuration de l'application.|(N/A)|
|HasProtectionLevel|Oui|Obtient une valeur qui indique si un niveau de protection a été assigné au membre.|Receive.ProtectionLevel ne doit pas être Null.|
|Nom|Oui|Obtient ou définit le nom de la \<portType > élément dans Web Services Description Language (WSDL).|Receive.ServiceContractName.LocalName doit correspondre.|
|Espace de noms|Oui|Obtient ou définit l’espace de noms de la \<portType > élément dans Web Services Description Language (WSDL).|Receive.ServiceContractName.NameSpace doit correspondre|
|ProtectionLevel|Oui|Spécifie si la liaison pour le contrat doit prendre en charge la valeur de la propriété ProtectionLevel.|Receive.ProtectionLevel doit correspondre.|
|SessionMode|Non|Obtient ou définit si les sessions sont autorisées, ne sont pas autorisées ou sont requises.|(N/A)|
|TypeId|Non|Lors de l'implémentation dans une classe dérivée, obtient un identificateur unique pour cet attribut. (Hérité de l'attribut.)|(N/A)|

Insérez le corps de la sous-section ici.

### <a name="OperationContract"></a> Attributs de contrat d’opération

|Nom de la propriété|Prise en charge|Description|Validation WF|
|-------------------|---------------|-----------------|-------------------|
|Action|Oui|Obtient ou définit l'action WS-Addressing du message de demande.|Receive.Action doit correspondre.|
|AsyncPattern|Non|Indique qu’une opération est implémentée de façon asynchrone à l’aide d’un Begin\<methodName > et de fin\<methodName > paire de méthodes dans un contrat de service.|(N/A)|
|HasProtectionLevel|Oui|Obtient une valeur qui indique si les messages pour cette opération doivent être chiffrés, signés ou les deux.|Receive.ProtectionLevel ne doit pas être Null.|
|IsInitiating|Non|Obtient ou définit une valeur qui indique si la méthode implémente une opération qui peut initialiser une session sur le serveur (si une telle session existe).|(N/A)|
|IsOneWay|Oui|Obtient ou définit une valeur qui indique si une opération retourne un message de réponse.|(Aucune activité SendReply pour cette méthode Receive ou aucune activité ReceiveReply pour cette méthode Send.)|
|IsTerminating|Non|Obtient ou définit une valeur qui indique si l'opération de service conduit le serveur à fermer la session après l'envoi du message de réponse (le cas échéant).|(N/A)|
|Nom|Oui|Obtient ou définit le nom de l'opération.|Receive.OperationName doit correspondre.|
|ProtectionLevel|Oui|Obtient ou définit une valeur qui spécifie si les messages d'une opération doivent être chiffrés, signés ou les deux.|Receive.ProtectionLevel doit correspondre.|
|ReplyAction|Oui|Obtient ou définit la valeur de l'action SOAP pour le message de réponse de l'opération.|SendReply.Action doit correspondre.|
|TypeId|Non|Lors de l'implémentation dans une classe dérivée, obtient un identificateur unique pour cet attribut. (Hérité de l'attribut.)|(N/A)|

### <a name="MessageContract"></a> Attributs de contrat de message

|Nom de la propriété|Prise en charge|Description|Validation WF|
|-------------------|---------------|-----------------|-------------------|
|HasProtectionLevel|Oui|Obtient une valeur qui indique si un niveau de protection a été assigné au message.|Aucune validation (Receive.Content et SendReply.Content doivent correspondre au type de contrat de message).|
|IsWrapped|Oui|Obtient ou définit une valeur qui spécifie si le corps du message contient un élément wrapper.|Aucune validation (Receive.Content et SendReply.Content doivent correspondre au type de contrat de message).|
|ProtectionLevel|Non|Obtient ou définit une valeur qui spécifie si le message doit être chiffré, signé ou les deux.|(N/A)|
|TypeId|Oui|Lors de l'implémentation dans une classe dérivée, obtient un identificateur unique pour cet attribut. (Hérité de l'attribut.)|Aucune validation (Receive.Content et SendReply.Content doivent correspondre au type de contrat de message).|
|WrapperName|Oui|Obtient ou définit le nom de l'élément wrapper du corps du message.|Aucune validation (Receive.Content et SendReply.Content doivent correspondre au type de contrat de message).|
|WrapperNamespace|Non|Obtient ou définit l'espace de noms de l'élément wrapper du corps du message.|(N/A)|

### <a name="DataContract"></a> Attributs de contrat de données

|Nom de la propriété|Prise en charge|Description|Validation WF|
|-------------------|---------------|-----------------|-------------------|
|IsReference|Non|Obtient ou définit une valeur qui indique s'il faut conserver les données de référence d'objet.|(N/A)|
|Nom|Oui|Obtient ou définit le nom du contrat de données pour le type.|Aucune validation (Receive.Content et SendReply.Content doivent correspondre au type de contrat de message).|
|Espace de noms|Oui|Obtient ou définit l'espace de noms du contrat de données pour le type.|Aucune validation (Receive.Content et SendReply.Content doivent correspondre au type de contrat de message).|
|TypeId|Non|Lors de l'implémentation dans une classe dérivée, obtient un identificateur unique pour cet attribut. (Hérité de l'attribut.)|(N/A)|

### <a name="FaultContract"></a> Attributs de contrat d’erreur

|Nom de la propriété|Prise en charge|Description|Validation WF|
|-------------------|---------------|-----------------|-------------------|
|Action|Oui|Obtient ou définit l'action du message d'erreur SOAP spécifié dans le cadre du contrat d'opération.|SendReply.Action doit correspondre.|
|DetailType|Oui|Obtient le type d'un objet sérialisable qui contient des informations sur l'erreur.|SendReply.Content doit correspondre au type|
|HasProtectionLevel|Non|Obtient une valeur qui indique si un niveau de protection a été assigné au message d'erreur SOAP.|(N/A)|
|Nom|Non|Obtient ou définit le nom du message d'erreur dans WSDL (Web Services Description Language).|(N/A)|
|Espace de noms|Non|Obtient ou définit l'espace de noms de l'erreur SOAP.|(N/A)|
|ProtectionLevel|Non|Spécifie le niveau de protection que l'erreur SOAP requiert de la liaison.|(N/A)|
|TypeId|Non|Lors de l'implémentation dans une classe dérivée, obtient un identificateur unique pour cet attribut. (Hérité de l'attribut.)|(N/A)|

## <a name="AdditionalSupport"></a> Prise en charge supplémentaire et des informations d’implémentation

- [Fonctionnalités de contrat de service non pris en charge](contract-first-workflow-service-development.md#UnsupportedFeatures)

- [Génération d’activités de messagerie configurées](contract-first-workflow-service-development.md#ActivityGeneration)

### <a name="UnsupportedFeatures"></a> Fonctionnalités de contrat de service non pris en charge

- L'utilisation des tâches de bibliothèque parallèle de tâches dans les contrats n'est pas prise en charge.

- L'héritage dans les contrats de service n'est pas pris en charge.

### <a name="ActivityGeneration"></a> Génération d’activités de messagerie configurées

Deux méthodes statiques publiques sont ajoutées aux activités <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply> pour prendre en charge la génération d'activités préconfigurées de message lors de l'utilisation de services de workflow contrat en premier.

- <xref:System.ServiceModel.Activities.Receive.FromOperationDescription%2A?displayProperty=nameWithType>

- <xref:System.ServiceModel.Activities.SendReply.FromOperationDescription%2A?displayProperty=nameWithType>

L'activité générée par ces méthodes doit passer la validation de contrat, et par conséquent ces méthodes sont utilisées en interne dans le cadre de la logique de validation de <xref:System.ServiceModel.Activities.Receive> et <xref:System.ServiceModel.Activities.SendReply>. <xref:System.ServiceModel.Activities.Receive.OperationName%2A>, <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>, <xref:System.ServiceModel.Activities.Receive.Action%2A>, <xref:System.ServiceModel.Activities.Receive.SerializerOption%2A>, <xref:System.ServiceModel.Activities.Receive.ProtectionLevel%2A> et <xref:System.ServiceModel.Activities.Receive.KnownTypes%2A> sont préconfigurées pour correspondre au contrat importé. Dans la page de propriétés de contenu pour les activités dans le Concepteur de flux de travail, le **Message** ou **paramètres** sections sont également préconfiguré de façon à correspondre au contrat.

Erreur WCF contrats sont également traités en retournant un ensemble distinct de configuré <xref:System.ServiceModel.Activities.SendReply> activités pour chacune des erreurs qui s’affichent dans le <xref:System.ServiceModel.Description.OperationDescription.Faults%2A> <xref:System.ServiceModel.Description.FaultDescriptionCollection>.

Pour d’autres parties de <xref:System.ServiceModel.Description.OperationDescription> qui sont pris en charge par les services WF aujourd'hui (par exemple, les comportements de WebGet/WebInvoke ou les comportements d’opération personnalisé), l’API ignore ces valeurs dans le cadre de la génération et la configuration. Aucune exception ne sera levée.
