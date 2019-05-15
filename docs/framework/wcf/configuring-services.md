---
title: Configuration des services WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: e8ac62809b1269ae810f026c003c7611b3ec548c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593329"
---
# <a name="configuring-wcf-services"></a>Configuration des services WCF

Une fois que vous avez conçu et implémenté votre contrat de service, vous êtes prêt à configurer votre service. C'est à ce stade que vous définissez et personnalisez la manière dont votre service est exposé aux clients, notamment l'adresse de son emplacement, l'encodage du transport et du message qu'il utilise pour envoyer et recevoir des messages, et le type de sécurité qu'il nécessite.  
  
 La configuration utilisée dans ce scénario comprend toutes les méthodes, de manière impérative dans le code ou à l'aide d'un fichier de configuration, permettant de définir et de personnaliser les divers aspects d'un service, tels que la spécification de ses adresses de point de terminaison, les transports utilisés et ses méthodes de sécurité. Dans la pratique, écriture de la configuration est des principales parties de la programmation d’applications WCF.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md)  
 En commençant par [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF est fourni avec un nouveau modèle de configuration par défaut qui simplifie les conditions requises de configuration WCF. Si vous ne fournissez pas de toute configuration de WCF pour un service particulier, le runtime configure automatiquement votre service avec les comportements, les liaisons et les points de terminaison par défaut.  
  
 [Configuration des services à l’aide de fichiers de configuration](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 Un service Windows Communication Foundation (WCF) est configurable à l’aide de la technologie de configuration .NET Framework. En règle générale, les éléments XML sont ajoutés au fichier Web.config pour un site Internet Information Services (IIS) qui héberge un service WCF. Les éléments vous permettent de modifier des détails, tels que les adresses de point de terminaison (les adresses réelles qui communiquent avec le service), à partir de chaque ordinateur individuel.  
  
 [Liaisons](../../../docs/framework/wcf/bindings.md)  
 En outre, WCF inclut plusieurs configurations courantes fournies par le système sous la forme de liaisons qui vous permettent de sélectionner rapidement les principales fonctionnalités de base pour la manière dont un client / service communiquent, tels que les transports, sécurité et utilisé des encodages de message.  
  
 [Points de terminaison](../../../docs/framework/wcf/endpoints.md)  
 Toutes les communications avec un service WCF s’effectue via le *points de terminaison* du service. Les points de terminaison contiennent le contrat, les informations de configuration spécifiées dans les liaisons, et les adresses qui indiquent où rechercher le service ou comment obtenir des informations sur le service.  
  
 [Sécurisation de services](../../../docs/framework/wcf/securing-services.md)  
 À l’aide de WCF et qui n’existe des mécanismes de sécurité, vous pouvez implémenter la confidentialité, intégrité, l’authentification et autorisation dans n’importe quel service. Vous pouvez aussi auditer les succès et les défaillances de la sécurité.  
  
 [Création de services interopérables avec le profil WS-I Basic Profile 1.1](../../../docs/framework/wcf/creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Les exigences pour déployer un service interopérable avec les services et les clients sur n’importe quelle autre plateforme ou système d’exploitation sont définies dans la spécification WS-I Basic Profile 1.1.  
  
## <a name="reference"></a>Référence  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Cycle de vie de la programmation de base](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
 [Conception et implémentation de services](../../../docs/framework/wcf/designing-and-implementing-services.md)  
  
 [Hébergement de services](../../../docs/framework/wcf/hosting-services.md)  
  
 [Génération de clients](../../../docs/framework/wcf/building-clients.md)  
  
 [Introduction à l’extensibilité](../../../docs/framework/wcf/introduction-to-extensibility.md)  
  
 [Administration et diagnostics](../../../docs/framework/wcf/diagnostics/index.md)  
  
## <a name="see-also"></a>Voir aussi

- [Programmation WCF de base](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Vue d’ensemble conceptuelle](../../../docs/framework/wcf/conceptual-overview.md)
- [Informations détaillées sur les fonctionnalités de WCF](../../../docs/framework/wcf/feature-details/index.md)
