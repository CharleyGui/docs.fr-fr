---
title: Utilisation de liaisons pour configurer des services et des clients
description: Les liaisons contiennent des informations de configuration utilisées par les clients ou services WFC. Découvrez comment définir des liaisons et comment spécifier une liaison pour un point de terminaison de service.
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 38fa4a928c74f9fff7b67f2479f9304331361fef
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289878"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Utilisation de liaisons pour configurer des services et des clients

Les liaisons sont des objets qui spécifient les détails de communication requis pour se connecter à un point de terminaison. Plus spécifiquement, les liaisons contiennent des informations de configuration utilisées pour créer l’exécution du client ou du service en définissant les caractéristiques des transports, les formats de transmission (encodage de message) et les protocoles à utiliser pour le point de terminaison ou canal client respectif. Pour créer un service de Windows Communication Foundation (WCF) opérationnel, chaque point de terminaison dans le service requiert une liaison. Cette rubrique explique ce que sont les liaisons, comment elles sont définies et comment une liaison particulière est spécifiée pour un point de terminaison.  
  
## <a name="what-a-binding-defines"></a>Ce que définit une liaison  

 Les informations contenues dans une liaison peuvent être basiques ou très complexes. La liaison la plus basique spécifie uniquement le protocole de transport (par exemple HTTP) qui doit être utilisé pour se connecter au point de terminaison. Plus généralement, les informations d'une liaison relatives à la procédure de connexion à un point de terminaison appartiennent à l'une des catégories répertoriées dans le tableau suivant.  
  
 Protocoles  
 Détermine le mécanisme de sécurité utilisé, soit une fonction de messagerie fiable, soit des paramètres de flux de contexte de transaction.  
  
 Transport  
 Détermine le protocole de transport sous-jacent à utiliser (par exemple, TCP ou HTTP).  
  
 Encodage  
 Détermine l'encodage de message, par exemple texte/XML, binaire ou MTOM (Message Transmission Optimization Mechanism), qui détermine la façon dont les messages sont représentés comme flux d'octets sur le câble.  
  
## <a name="system-provided-bindings"></a>Liaisons fournies par le système  

 WCF comprend un ensemble de liaisons fournies par le système qui sont conçues pour couvrir la plupart des scénarios et exigences de l’application. Les classes suivantes représentent quelques exemples de liaisons fournies par le système :  
  
- <xref:System.ServiceModel.BasicHttpBinding> : liaison de protocole HTTP adaptée à la connexion à des services Web conformes à la spécification WS-I Basic Profile 1.1 (par exemple, services basés sur les services Web ASP.NET [ASMX]).  
  
- <xref:System.ServiceModel.WSHttpBinding> : liaison de protocole HTTP adaptée à la connexion à des points de terminaison conformes aux protocoles de spécification des services Web.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: Utilise les technologies d’encodage binaire .NET et de tramage conjointement avec le transport de canal nommé Windows pour se connecter à d’autres points de terminaison WCF sur le même ordinateur.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: Utilise les technologies d’encodage binaire .NET et de tramage conjointement avec le Message Queuing (également appelé MSMQ) pour créer des connexions de message en file d’attente avec d’autres points de terminaison WCF.  
  
 Pour obtenir la liste complète des liaisons fournies par le système, avec des descriptions, consultez [liaisons fournies par le système](system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Liaisons personnalisées  

 Si la collection de liaisons fournie par le système n'a pas la combinaison correcte de fonctionnalités requises par une application de service, vous pouvez créer une liaison <xref:System.ServiceModel.Channels.CustomBinding>. Pour plus d’informations sur les éléments d’une <xref:System.ServiceModel.Channels.CustomBinding> liaison, consultez [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) et [liaisons personnalisées](./extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Utilisation des liaisons  

 L’utilisation des liaisons implique deux étapes simples :  
  
1. Sélectionner ou définir une liaison. La méthode la plus simple consiste à choisir l’une des liaisons fournies par le système et à utiliser ses paramètres par défaut. Vous pouvez également choisir une liaison fournie par le système et réinitialiser ses valeurs de propriété en fonction de vos spécifications. En guise d’alternative, vous pouvez créer une liaison personnalisée et définir chaque propriété selon vos besoins.  
  
2. Créer un point de terminaison qui utilise cette liaison.  
  
## <a name="code-and-configuration"></a>Code et configuration  

 Vous pouvez définir ou configurer des liaisons par le biais de code ou de configuration. Ces deux approches sont indépendantes du type de liaison utilisé, par exemple si vous utilisez une liaison <xref:System.ServiceModel.Channels.CustomBinding> ou fournie par le système. En général, l’utilisation de code permet de bénéficier d’un contrôle total sur la définition d’une liaison lorsque vous compilez. L’utilisation de la configuration, en revanche, permet à un administrateur système ou à l’utilisateur d’un service ou client WCF de modifier les paramètres des liaisons. Cette souplesse est souvent souhaitable car il n’existe aucun moyen de prédire les exigences et les conditions réseau spécifiques dans lesquelles une application WCF doit être déployée. Le fait de séparer les informations de liaison (et d'adressage) du code permet aux administrateurs de modifier les détails de liaison sans avoir à recompiler ou à redéployer l'application. Notez que si la liaison est définie dans du code, elle remplace toute définition basée sur la configuration effectuée dans le fichier de configuration. Pour obtenir des exemples de ces approches, consultez les rubriques suivantes :  
  
- [Comment : héberger un service WCF dans une application managée](how-to-host-a-wcf-service-in-a-managed-application.md) fournit un exemple de création d’une liaison dans le code.  
  
- [Didacticiel : créer un client Windows Communication Foundation](how-to-create-a-wcf-client.md) fournit un exemple de création d’un client à l’aide de la configuration.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble de la création de points de terminaison](endpoint-creation-overview.md)
- [Procédure : spécifier une liaison de service dans la configuration](how-to-specify-a-service-binding-in-configuration.md)
- [Procédure : spécifier une liaison de service dans le code](how-to-specify-a-service-binding-in-code.md)
- [Procédure : spécifier une liaison de client dans la configuration](how-to-specify-a-client-binding-in-configuration.md)
- [Procédure : spécifier une liaison de client dans le code](how-to-specify-a-client-binding-in-code.md)
