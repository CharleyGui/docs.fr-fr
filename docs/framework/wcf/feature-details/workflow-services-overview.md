---
title: Présentation des services de workflow
ms.date: 03/30/2017
ms.assetid: e536dda3-e286-441e-99a7-49ddc004b646
ms.openlocfilehash: 7055ea6e6b6d6a5d7bef8d5ff465d2eb0c838bf6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812183"
---
# <a name="workflow-services-overview"></a>Présentation des services de workflow

Les services de workflow sont des services basés sur WCF qui sont implémentés à l’aide de workflows. Les services de workflow sont des flux de travail qui utilisent les activités de messagerie pour envoyer et recevoir des messages Windows Communication Foundation (WCF). .NET Framework 4.5 introduit plusieurs activités de messagerie qui vous permettent d'envoyer et de recevoir des messages à partir d'un workflow. Pour plus d’informations sur les activités de messagerie et la façon dont elles peuvent être utilisées pour implémenter différents modèles d’échange de messages, consultez [activités de messagerie](messaging-activities.md).

## <a name="benefits-of-using-workflow-services"></a>Avantages de l’utilisation des services de workflow

Les applications étant de plus en plus distribuées, les services individuels sont désormais chargés d'appeler d'autres services pour alléger en partie la tâche. Implémenter ces appels en tant qu'opérations asynchrones rend le code plus complexe. La gestion des erreurs ajoute une complexité supplémentaire, sous la forme d'une gestion des exceptions et de la fourniture d'informations de suivi détaillées. Certains services ont souvent une durée d'exécution longue et peuvent consommer de précieuses ressources système à attendre une entrée. En raison de ces problèmes, les applications distribuées sont souvent très complexes, difficiles à écrire et à maintenir. Les workflows constituent une méthode naturelle pour exprimer la coordination de travail asynchrone, notamment les appels aux services externes. Les workflows sont également efficaces pour représenter des processus d'entreprise de longue durée. Ces qualités font du workflow une ressource importante pour la construction de services dans un environnement distribué.

## <a name="implementing-a-workflow-service"></a>Implémentation d’un service de workflow

Lors de l’implémentation d’un service WCF, vous définissez un certain nombre de contrats qui décrivent le service et les données qu’il envoie et reçoit. Les données sont représentées en tant que contrats de données et contrats de message. Les services WCF et les services de workflow utilisent tous des définitions de contrat de données et de contrat de message dans le cadre des descriptions du service. Le service lui-même expose des métadonnées (au format WSDL) pour décrire les opérations du service. Dans WCF, les contrats de service et les contrats d'opération définissent le service et les opérations qu'il prend en charge. Toutefois dans un service de workflow, ces contrats font partie du processus d'entreprise lui-même. Ils sont exposés dans les métadonnées par un processus appelé l'inférence de contrat. Lorsqu'un service de workflow est hébergé à l'aide d'un objet <xref:System.ServiceModel.Activities.WorkflowServiceHost>, la définition du workflow est examinée et un contrat est généré en fonction du jeu d'activités de messagerie qui se trouvent dans le workflow. Plus particulièrement, les activités et les propriétés suivantes sont utilisées pour générer le contrat :

<xref:System.ServiceModel.Activities.Receive> Activité

- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>

- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>

- <xref:System.ServiceModel.Activities.Receive.Action%2A>

<xref:System.ServiceModel.Activities.SendReply> Activité

- <xref:System.ServiceModel.Activities.SendReply.Action%2A>

<xref:System.ServiceModel.Activities.TransactedReceiveScope> Activité

Le résultat final de l’inférence de contrat est une description du service utilisant les mêmes structures de données que les services WCF et les contrats d’opération. Puis ces informations sont utilisées pour exposer WSDL pour le service de workflow.

> [!NOTE]
> [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] ne vous permet pas d'écrire des services de workflow à l'aide d'une définition de contrat existante, sans une prise en charge d'outils supplémentaires. Les contrats du service de workflow sont créés par le processus d'inférence de contrat présenté précédemment. Les contrats de message et les contrats de données sont toutefois entièrement pris en charge.

## <a name="workflow-services-and-msmq-based-bindings"></a>Services de workflow et liaisons basées sur MSMQ

WCF définit deux liaisons <xref:System.ServiceModel.NetMsmqBinding> et <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> basées sur MSMQ.  Les liaisons basées sur MSMQ sont souvent utilisées avec les services de workflow en raison de la longue durée d’exécution de ces services. Les liaisons basées sur MSMQ ont une propriété `ValidityDuration` qui spécifie comment de temps les messages MSMQ peuvent supposer être valides. En raison de la longue durée d'exécution des services de workflow, il est possible que la durée de validité d'un message MSMQ expire avant que le service de workflow puisse le traiter. Il est donc très important d’affecter une valeur appropriée à la durée de validité d’une liaison MSMQ. Cette valeur doit être choisie en fonction du workflow et de sa manière de traiter les messages. Par exemple si vous avez un workflow avec une activité <xref:System.ServiceModel.Activities.Receive> suivie d'une activité personnalisée qui s'exécute pendant 10 minutes, elle-même suivie d'une autre activité <xref:System.ServiceModel.Activities.Receive>, la valeur correcte pour `ValidityDuration` doit être supérieure à 10 minutes.

## <a name="hosting-a-workflow-service"></a>Hébergement d’un service de workflow

Comme les services WCF, les services de workflow doivent être hébergés. Les services WCF utilisent la <xref:System.ServiceModel.ServiceHost> classe pour héberger des services et des services de flux <xref:System.ServiceModel.Activities.WorkflowServiceHost> de travail à utiliser pour héberger des services. Comme les services WCF, les services de workflow peuvent être hébergés de différentes façons, par exemple :

- Dans une application .NET Framework gérée.

- Dans les Services IIS (Internet Information Services).

- dans le service d'activation des processus Windows (WAS, Windows Process Activation Service) ;

- dans un service Windows managé.

Les services de flux de travail hébergés dans une application .NET Frameworke managée ou un service Windows managé créent une instance de la <xref:System.ServiceModel.Activities.WorkflowServiceHost> classe et lui passent une instance du <xref:System.ServiceModel.Activities.WorkflowService> qui contient la définition de workflow dans la <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> propriété. Une définition de workflow contenant des activités de messagerie est exposée en tant que service de workflow.

Pour héberger un service de workflow dans les services IIS ou WAS, placez dans un répertoire virtuel le fichier .xamlx qui contient la définition du service de workflow. Un point de terminaison par défaut (à l’aide <xref:System.ServiceModel.BasicHttpBinding> de) est créé automatiquement pour plus d’informations, consultez [configuration simplifiée](../simplified-configuration.md). Vous pouvez également placer un fichier Web.config dans le répertoire virtuel pour spécifier vos propres points de terminaison. Si votre définition de workflow se trouve dans un assembly, vous pouvez placer un fichier .svc dans le répertoire virtuel et l'assembly de workflow dans le répertoire App_Code. Le fichier .svc doit spécifier la fabrique hôte de service et la classe qui implémente le service de workflow. L'exemple suivant montre comment spécifier la fabrique hôte de service et la classe qui implémente le service de workflow.

```aspx-csharp
<%@ServiceHost Factory="System.ServiceModel.Activities.Activation.WorkflowServiceHostFactory"
Service="EchoService"%>
```
