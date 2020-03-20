---
title: Custom Find Criteria
ms.date: 03/30/2017
ms.assetid: b2723929-8829-424d-8015-a37ba2ab4f68
ms.openlocfilehash: 3bafe89f5c114106eece02c41599cf485591c1cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183862"
---
# <a name="custom-find-criteria"></a>Custom Find Criteria
Cet exemple montre comment créer une correspondance de portée personnalisée à l'aide de la logique et comment implémenter un service de découverte personnalisé. Les clients utilisent la fonctionnalité de correspondance de portée personnalisée pour affiner et mieux tirer parti de la fonctionnalité de recherche système de la découverte WCF. Le scénario couvert par cet exemple est le suivant :  
  
1. Un client recherche un service de calculatrice.  
  
2. Pour affiner sa recherche, le client doit utiliser une règle de correspondance de portée personnalisée.  
  
3. D'après cette règle, un service répond au client si son point de terminaison correspond à l'une quelconque des portées spécifiées par le client.  
  
## <a name="demonstrates"></a>Illustre le  
  
- Création d'un service de découverte personnalisé  
  
- Implémentation d'une correspondance de portée personnalisée par algorithme  
  
## <a name="discussion"></a>Discussions  
 Le client est à la recherche de critères d’appariement de type « OR ». Un service répond si les portées de ses points de terminaison correspondent à l'une des portées fournies par le client. Dans ce cas, le client recherche un service de calculatrice dont la portée figure dans la liste suivante :  
  
1. `net.tcp://Microsoft.Samples.Discovery/RedmondLocation`  
  
2. `net.tcp://Microsoft.Samples.Discovery/SeattleLocation`  
  
3. `net.tcp://Microsoft.Samples.Discovery/PortlandLocation`  
  
 Pour cela, le client indique aux services d'utiliser une règle de correspondance de portée personnalisée en passant une correspondance de portée personnalisée par URI. Pour faciliter la mise en correspondance de portée personnalisée, le service doit utiliser un service de découverte personnalisé qui comprend la règle de correspondance de portée personnalisée et implémente la logique associée.  
  
 Dans le projet client, ouvrez le fichier Program.cs. Notez que le champ `ScopeMatchBy` de l'objet `FindCriteria` a pour valeur un URI spécifique. Cet identificateur est envoyé au service. Si le service ne comprend pas cette règle, il ignore la demande de recherche du client.  
  
 Ouvrez le projet de service. L'implémentation du service de découverte personnalisé utilise trois fichiers :  
  
1. **AsyncResult.cs**: C’est la mise `AsyncResult` en œuvre de ce qui est exigé par les méthodes Discovery.  
  
2. **CustomDiscoveryService.cs**: Ce fichier met en œuvre le service de découverte personnalisée. L'implémentation étend la classe <xref:System.ServiceModel.Discovery.DiscoveryService> et substitue les méthodes nécessaires. Notez l'implémentation de la méthode <xref:System.ServiceModel.Discovery.DiscoveryService.OnBeginFind%2A>. Cette méthode vérifie si la règle de correspondance de portée personnalisée a été spécifiée par le client. Il s'agit de l'URI personnalisé que le client a spécifié précédemment. Si la règle personnalisée est spécifiée, le chemin de code qui implémente la logique de correspondance "OU" est suivi.  
  
     Cette logique personnalisée parcourt toutes les portées sur chacun des points de terminaison dont le service dispose. Si l'une des portées du point de terminaison correspond à l'une des portées fournies par le client, le service de découverte ajoute ce point de terminaison à la réponse renvoyée au client.  
  
3. **CustomDiscoveryExtension.cs**: La dernière étape dans la mise en œuvre du service de découverte est de connecter cette mise en œuvre du service de découverte personnalisée à l’hôte du service. La classe d'assistance utilisée ici est la classe `CustomDiscoveryExtension`. Cette classe étend la classe <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension>. L'utilisateur doit substituer la méthode <xref:System.ServiceModel.Discovery.DiscoveryServiceExtension.GetDiscoveryService%2A>. Dans ce cas, la méthode retourne une instance du service de découverte personnalisé créé auparavant. `PublishedEndpoints` est un <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> qui contient tous les points de terminaison d'application qui sont ajoutés à <xref:System.ServiceModel.ServiceHost>. Le service de découverte personnalisé l'utilise pour remplir sa liste interne. Un utilisateur peut aussi ajouter d'autres métadonnées de points de terminaison.  
  
 Enfin, ouvrez Program.cs. Notez que <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> et `CustomDiscoveryExtension` sont tous deux ajoutés à l'hôte. Lorsque cette opération a été effectuée et que l'hôte dispose d'un point de terminaison sur lequel recevoir des messages de découverte, l'application peut utiliser le service de découverte personnalisé.  
  
 Observez que le client peut trouver le service sans connaître son adresse.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Ouvrez la solution qui contient le projet.  
  
2. Créez le projet.  
  
3. Exécutez l'application de service.  
  
4. Exécuter l’application cliente.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\CustomFindCriteria`
