---
title: Utilisation de liaisons pour configurer des services et des clients
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], using
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
ms.openlocfilehash: 0f01fefc46cbc2cddaef9b025d59db8e2f734d9f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645125"
---
# <a name="using-bindings-to-configure-services-and-clients"></a>Utilisation de liaisons pour configurer des services et des clients
Les liaisons sont des objets qui spécifient les détails de communication requis pour se connecter à un point de terminaison. Plus spécifiquement, les liaisons contiennent des informations de configuration utilisées pour créer l’exécution du client ou du service en définissant les caractéristiques des transports, les formats de transmission (encodage de message) et les protocoles à utiliser pour le point de terminaison ou canal client respectif. Pour créer un service Windows Communication Foundation (WCF) fonctionnel, chaque point de terminaison dans le service nécessite une liaison. Cette rubrique explique ce que sont les liaisons, comment elles sont définies et comment une liaison particulière est spécifiée pour un point de terminaison.  
  
## <a name="what-a-binding-defines"></a>Ce que définit une liaison  
 Les informations contenues dans une liaison peuvent être basiques ou très complexes. La liaison la plus basique spécifie uniquement le protocole de transport (par exemple HTTP) qui doit être utilisé pour se connecter au point de terminaison. Plus généralement, les informations d'une liaison relatives à la procédure de connexion à un point de terminaison appartiennent à l'une des catégories répertoriées dans le tableau suivant.  
  
 Protocoles  
 Détermine le mécanisme de sécurité utilisé, soit une fonction de messagerie fiable, soit des paramètres de flux de contexte de transaction.  
  
 Transport  
 Détermine le protocole de transport sous-jacent à utiliser (par exemple, TCP ou HTTP).  
  
 Encodage  
 Détermine l'encodage de message, par exemple texte/XML, binaire ou MTOM (Message Transmission Optimization Mechanism), qui détermine la façon dont les messages sont représentés comme flux d'octets sur le câble.  
  
## <a name="system-provided-bindings"></a>Liaisons fournies par le système  
 WCF inclut un ensemble de liaisons fournies par le système qui sont conçues pour couvrir la plupart des scénarios et exigences de l’application. Les classes suivantes représentent quelques exemples de liaisons fournies par le système :  
  
- <xref:System.ServiceModel.BasicHttpBinding>: Un liaison de protocole HTTP adaptée à la connexion aux services Web qui est conforme à la norme WS-I Basic Profile 1.1 spécification (par exemple, les services Web ASP.NET [ASMX]-services basés sur).  
  
- <xref:System.ServiceModel.WSHttpBinding>: Protocoles de spécifications de services de liaison adaptée à la connexion aux points de terminaison qui se conforment au site Web de protocole HTTP.  
  
- <xref:System.ServiceModel.NetNamedPipeBinding>: Utilise l’encodage binaire .NET et de tramage technologies conjointement avec le transport de canal nommé de Windows pour se connecter aux autres points de terminaison WCF sur le même ordinateur.  
  
- <xref:System.ServiceModel.NetMsmqBinding>: Utilise l’encodage binaire .NET et tramage technologies conjointement avec le Message Queuing (également appelé MSMQ) pour créer des connexions de message en file d’attente avec d’autres points de terminaison WCF.  
  
 Pour obtenir la liste complète des liaisons fournies par le système, avec leurs descriptions, consultez [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## <a name="custom-bindings"></a>Liaisons personnalisées  
 Si la collection de liaisons fournie par le système n'a pas la combinaison correcte de fonctionnalités requises par une application de service, vous pouvez créer une liaison <xref:System.ServiceModel.Channels.CustomBinding>. Pour plus d’informations sur les éléments d’un <xref:System.ServiceModel.Channels.CustomBinding> liaison, consultez [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) et [liaisons personnalisées](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="using-bindings"></a>Utilisation des liaisons  
 L’utilisation des liaisons implique deux étapes simples :  
  
1. Sélectionner ou définir une liaison. La méthode la plus simple consiste à choisir l’une des liaisons fournies par le système et à utiliser ses paramètres par défaut. Vous pouvez également choisir une liaison fournie par le système et réinitialiser ses valeurs de propriété en fonction de vos spécifications. En guise d’alternative, vous pouvez créer une liaison personnalisée et définir chaque propriété selon vos besoins.  
  
2. Créer un point de terminaison qui utilise cette liaison.  
  
## <a name="code-and-configuration"></a>Code et configuration  
 Vous pouvez définir ou configurer des liaisons par le biais de code ou de configuration. Ces deux approches sont indépendantes du type de liaison utilisé, par exemple si vous utilisez une liaison <xref:System.ServiceModel.Channels.CustomBinding> ou fournie par le système. En général, l’utilisation de code permet de bénéficier d’un contrôle total sur la définition d’une liaison lorsque vous compilez. À l’aide de la configuration, en revanche, permet à un administrateur système ou l’utilisateur d’un service WCF ou le client pour modifier les paramètres des liaisons. Cette souplesse est souvent souhaitable car il n’existe aucun moyen de prévoir l’exigences spécifiques du matériel et des conditions dans lesquelles une application WCF doit être déployée réseau. Le fait de séparer les informations de liaison (et d'adressage) du code permet aux administrateurs de modifier les détails de liaison sans avoir à recompiler ou à redéployer l'application. Notez que si la liaison est définie dans du code, elle remplace toute définition basée sur la configuration effectuée dans le fichier de configuration. Pour obtenir des exemples de ces approches, consultez les rubriques suivantes :  
  
- [Guide pratique pour Héberger un Service WCF dans une Application gérée](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) fournit un exemple de création d’une liaison dans le code.  
  
- [Tutoriel : Créer un client Windows Communication Foundation](../../../docs/framework/wcf/how-to-create-a-wcf-client.md) fournit un exemple de création d’un client à l’aide de configuration.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la création de points de terminaison](../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Guide pratique pour Spécifier une liaison de Service dans la Configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)
- [Guide pratique pour Spécifier une liaison de Service dans le Code](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)
- [Guide pratique pour Spécifier une liaison Client dans la Configuration](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)
- [Guide pratique pour Spécifier une liaison Client dans le Code](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)
