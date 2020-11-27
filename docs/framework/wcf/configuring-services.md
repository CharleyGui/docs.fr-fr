---
title: Configuration des services WCF
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [WCF]
ms.assetid: beac771e-f28e-4f84-9ff1-ad9251c726d3
ms.openlocfilehash: a5fe0cabb1a6be7f93bf5f4d753e9bb08a39cea3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253334"
---
# <a name="configuring-wcf-services"></a>Configuration des services WCF

Une fois que vous avez conçu et implémenté votre contrat de service, vous êtes prêt à configurer votre service. C'est à ce stade que vous définissez et personnalisez la manière dont votre service est exposé aux clients, notamment l'adresse de son emplacement, l'encodage du transport et du message qu'il utilise pour envoyer et recevoir des messages, et le type de sécurité qu'il nécessite.  
  
 La configuration utilisée dans ce scénario comprend toutes les méthodes, de manière impérative dans le code ou à l'aide d'un fichier de configuration, permettant de définir et de personnaliser les divers aspects d'un service, tels que la spécification de ses adresses de point de terminaison, les transports utilisés et ses méthodes de sécurité. Dans la pratique, l’écriture de la configuration est une partie importante de la programmation des applications WCF.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Configuration simplifiée](simplified-configuration.md)  
 À partir de .NET Framework 4, WCF est fourni avec un nouveau modèle de configuration par défaut qui simplifie les exigences de configuration WCF. Si vous ne fournissez aucune configuration WCF pour un service particulier, le runtime configure automatiquement votre service avec les points de terminaison, les liaisons et les comportements par défaut.  
  
 [Configuration des services à l'aide de fichiers de configuration](configuring-services-using-configuration-files.md)  
 Un service Windows Communication Foundation (WCF) est configurable à l’aide de la technologie de configuration .NET Framework. Le plus souvent, les éléments XML sont ajoutés au fichier Web.config pour un site Internet Information Services (IIS) qui héberge un service WCF. Les éléments vous permettent de modifier des détails, tels que les adresses de point de terminaison (les adresses réelles qui communiquent avec le service), à partir de chaque ordinateur individuel.  
  
 [Liaisons](bindings.md)  
 En outre, WCF comprend plusieurs configurations courantes fournies par le système sous forme de liaisons qui vous permettent de sélectionner rapidement les fonctionnalités de base pour la communication entre un client et un service, telles que les transports, la sécurité et les encodages de message utilisés.  
  
 [Points de terminaison](endpoints.md)  
 Toutes les communications avec un service WCF se produisent via les *points de terminaison* du service. Les points de terminaison contiennent le contrat, les informations de configuration spécifiées dans les liaisons, et les adresses qui indiquent où rechercher le service ou comment obtenir des informations sur le service.  
  
 [Sécurisation de services](securing-services.md)  
 À l’aide de WCF et des mécanismes de sécurité existants, vous pouvez implémenter la confidentialité, l’intégrité, l’authentification et l’autorisation dans n’importe quel service. Vous pouvez aussi auditer les succès et les défaillances de la sécurité.  
  
 [Création de services pouvant interagir avec le profil Basic Profile 1.1 de WS-I](./creating-ws-i-basic-profile-1-1-interoperable-services.md)  
 Les exigences pour déployer un service interopérable avec les services et les clients sur n’importe quelle autre plateforme ou système d’exploitation sont définies dans la spécification WS-I Basic Profile 1.1.  
  
## <a name="reference"></a>Informations de référence  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
## <a name="related-sections"></a>Sections connexes  

 [Cycle de vie de la programmation de base](basic-programming-lifecycle.md)  
  
 [Conception et implémentation de services](designing-and-implementing-services.md)  
  
 [Hébergement de services](hosting-services.md)  
  
 [Génération de clients](building-clients.md)  
  
 [Introduction à l'extensibilité](introduction-to-extensibility.md)  
  
 [Administration et diagnostics](./diagnostics/index.md)  
  
## <a name="see-also"></a>Voir aussi

- [Programmation WCF de base](basic-wcf-programming.md)
- [Vue d’ensemble conceptuelle](conceptual-overview.md)
- [Détails des fonctionnalités WCF](./feature-details/index.md)
