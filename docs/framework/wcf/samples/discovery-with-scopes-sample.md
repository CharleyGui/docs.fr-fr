---
title: Exemple Discovery with Scopes
ms.date: 03/30/2017
ms.assetid: 6a37a754-6b8c-4ebe-bdf2-d4f0520271d5
ms.openlocfilehash: 8ba5618f472fc8a6e1751776060f99103a67a073
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728748"
---
# <a name="discovery-with-scopes-sample"></a>Exemple Discovery with Scopes

Cet exemple montre comment utiliser des portées pour catégoriser des points de terminaison détectables et comment utiliser <xref:System.ServiceModel.Discovery.DiscoveryClient> pour rechercher des points de terminaison de façon asynchrone. Sur le service, cet exemple montre comment personnaliser la découverte pour chaque point de terminaison en ajoutant un comportement de découverte du point de terminaison, et en l'utilisant pour ajouter une portée au point de terminaison et contrôler la fonctionnalité de découverte du point de terminaison. Sur le client, l'exemple passe en revue la façon dont les clients peuvent créer un <xref:System.ServiceModel.Discovery.DiscoveryClient> et ajuster les paramètres de recherche de manière à inclure des portées en les ajoutant à <xref:System.ServiceModel.Discovery.FindCriteria>. Cet exemple montre comment les clients peuvent limiter les réponses en ajoutant un critère d'arrêt.

## <a name="service-features"></a>Fonctionnalités du service

Ce projet présente deux points de terminaison de service qui sont ajoutés à un <xref:System.ServiceModel.ServiceHost>. Un <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> est associé à chaque point de terminaison. Ce comportement est utilisé pour ajouter des portées d'URI pour les deux points de terminaison. Les portées permettent de distinguer chacun de ces points de terminaison afin que les clients puissent affiner la recherche. Pour le deuxième point de terminaison, la fonctionnalité de découverte peut être désactivée en affectant à la propriété <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Enabled%2A> la valeur `false`. De cette façon, les métadonnées de découverte associées à ce point de terminaison ne seront pas envoyées dans le cadre d'un message de découverte.

## <a name="client-features"></a>Fonctionnalités du client

La méthode `FindCalculatorServiceAddress()` montre comment utiliser un <xref:System.ServiceModel.Discovery.DiscoveryClient> et lui passer un <xref:System.ServiceModel.Discovery.FindCriteria> avec deux restrictions. Une portée est ajoutée aux critères et la propriété <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> prend la valeur 1. La portée limite les résultats aux seuls services qui publient la même portée. Affecter 1 à <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> limite les réponses que le <xref:System.ServiceModel.Discovery.DiscoveryClient> attend à un point de terminaison au maximum. L’appel à <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> est une opération synchrone qui bloque le thread jusqu’à ce qu’un délai d’attente soit atteint ou qu’un point de terminaison soit trouvé.

### <a name="to-use-this-sample"></a>Pour utiliser cet exemple

1. Cet exemple utilise des points de terminaison HTTP et pour exécuter cet exemple, des listes de contrôle d'accès (ACL) d'URL appropriées doivent être ajoutées. Pour plus d’informations, consultez [configuration de http et HTTPS](../feature-details/configuring-http-and-https.md). L'exécution de la commande suivante avec un privilège élevé doit ajouter les ACL appropriées. Vous pouvez substituer vos domaine et nom d'utilisateur aux arguments suivants si la commande ne fonctionne pas telle quelle : `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`

2. Générez la solution.

3. Exécutez le fichier exécutable du service à partir du répertoire de build.

4. Exécutez le fichier exécutable du client. Notez que le client est en mesure de trouver le service.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryWithScopes`
