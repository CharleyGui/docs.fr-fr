---
title: Service de routage
ms.date: 03/30/2017
ms.assetid: ca7c216a-5141-4132-8193-102c181d2eba
ms.openlocfilehash: 3119f32d57cff01b81e4a8f4a3f3a571013300ea
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662784"
---
# <a name="routing-service"></a>Service de routage

Le service de routage est un intermédiaire SOAP générique qui agit en tant que routeur de messages. La fonctionnalité principale du service de routage est la possibilité de router des messages en fonction du contenu des messages ; un message peut ainsi être envoyé à un point de terminaison client en fonction d'une valeur située à l'intérieur du message, soit dans l'en-tête, soit dans le corps du message.

Le <xref:System.ServiceModel.Routing.RoutingService> est implémenté comme un service Windows Communication Foundation (WCF) dans le <xref:System.ServiceModel.Routing> espace de noms. Le service de routage expose un ou plusieurs points de terminaison de service qui reçoivent des messages, puis routent chaque message vers un ou plusieurs points de terminaison client en fonction du contenu du message. Le service offre les fonctionnalités suivantes :

- Routage basé sur le contenu

  - Agrégation de service

  - Contrôle des versions du service

  - Routage par priorité

  - Configuration dynamique

- Pontage de protocoles

- Traitement SOAP

- Gestion avancée des erreurs

- Points de terminaison de sauvegarde

Bien qu'il soit possible de créer un service intermédiaire répondant à un ou plusieurs de ces objectifs, une telle implémentation est souvent liée à un scénario ou à une solution spécifique et ne peut pas être appliquée facilement à de nouvelles applications.

Le Service de routage fournit un intermédiaire SOAP générique, configurable de manière dynamique et connectable qui est compatible avec les modèles de Service WCF et de canal et vous permet d’effectuer un routage basé sur le contenu des messages SOAP.

> [!NOTE]
> Le service de routage ne prend pas actuellement en charge le routage de services WCF REST.  Pour router des appels REST, envisagez d’utiliser <xref:System.Web.Routing> ou [Application Request Routing](https://go.microsoft.com/fwlink/?LinkId=164589).

## <a name="content-based-routing"></a>Routage basé sur le contenu

Le routage basé sur le contenu est la possibilité de router un message en fonction d'une ou plusieurs valeurs contenues dans le message. Le service de routage examine chaque message et le route vers le point de terminaison de destination en fonction du contenu du message et de la logique de routage que vous créez. Le routage basé sur le contenu fournit la base de l'agrégation de service, du contrôle des versions de service et du routage par priorité.

Pour implémenter le routage basé sur le contenu, le service de routage s'appuie sur les implémentations <xref:System.ServiceModel.Dispatcher.MessageFilter> utilisées pour établir une correspondance avec les valeurs spécifiques contenues dans les messages à router. Si un **MessageFilter** correspond à un message, le message est routé vers le point de terminaison de destination associé à la **MessageFilter**.  Les filtres de message sont regroupés dans des tables de filtres (<xref:System.ServiceModel.Routing.Configuration.FilterTableCollection>) pour construire une logique de routage complexe. Par exemple, une table de filtres peut contenir cinq filtres de message s'excluant mutuellement, qui orientent le routage des messages vers un seul des cinq points de terminaison de destination.

Le service de routage vous permet de configurer la logique utilisée pour effectuer un routage basé sur le contenu, ainsi que de mettre à jour la logique de routage de manière dynamique, au moment de l'exécution.

En regroupant des filtres de message dans des tables de filtres, vous pouvez construire une logique de routage permettant de gérer plusieurs scénarios de routage, tels que les suivants :

- Agrégation de service

- Contrôle des versions du service

- Routage par priorité

- Configuration dynamique

Pour plus d’informations sur les filtres de messages et tables de filtres, consultez [Introduction routage](../../../../docs/framework/wcf/feature-details/routing-introduction.md) et [filtres de Message](../../../../docs/framework/wcf/feature-details/message-filters.md).

### <a name="service-aggregation"></a>Agrégation de service

En utilisant le routage basé sur le contenu, vous pouvez exposer un point de terminaison qui reçoit des messages provenant d'applications clientes externes, puis router chaque message vers le point de terminaison interne approprié en fonction d'une valeur contenue dans le message. Cela permet d'offrir un point de terminaison spécifique à diverses applications principales, et également d'offrir aux clients un point de terminaison d'application tout en développant votre application en une variété de services.

### <a name="service-versioning"></a>Contrôle des versions du service

Lors de la migration vers une nouvelle version de votre solution, vous aurez peut-être besoin de maintenir l'ancienne version en parallèle pour servir des clients existants. Cela demande souvent que les clients qui se connectent à la version plus récente utilisent une adresse différente pour communiquer avec la solution. Le service de routage vous permet d'exposer un seul point de terminaison de service qui sert aux deux versions de votre solution, en routant les messages vers la solution appropriée en fonction d'informations spécifiques à la version contenues dans le message. Pour obtenir un exemple d’une telle implémentation consultez [How To : Service de contrôle de version](../../../../docs/framework/wcf/feature-details/how-to-service-versioning.md).

### <a name="priority-routing"></a>Routage par priorité

Lorsque vous fournissez un service à plusieurs clients, vous pouvez avoir un contrat de niveau de service (SLA) avec certains partenaires exigeant que toutes les données de ces partenaires soient traitées séparément de celles des autres clients. En utilisant un filtre qui recherche les informations spécifiques au client contenues dans le message, vous pouvez router facilement des messages de partenaires spécifiques vers un point de terminaison qui a été créé pour répondre aux exigences du contrat SLA.

## <a name="dynamic-configuration"></a>Configuration Dynamique

Pour prendre en charge des systèmes fondamentaux, où les messages doivent être traités sans interruption de service, il est essentiel de pouvoir modifier la configuration des composants dans le système au moment de l'exécution. Pour prendre en charge ce besoin, le service de routage fournit une implémentation <xref:System.ServiceModel.IExtension%601>, l'objet <xref:System.ServiceModel.Routing.RoutingExtension>, qui permet une mise à jour dynamique de la configuration du service de routage au moment de l'exécution.

Pour plus d’informations sur la configuration dynamique du Service de routage, consultez [Introduction routage](../../../../docs/framework/wcf/feature-details/routing-introduction.md).

## <a name="protocol-bridging"></a>Pontage de protocoles

L'une des difficultés dans les scénarios intermédiaires est que les points de terminaison internes peuvent avoir besoin d'une version du transport ou SOAP différentes de celle du point de terminaison sur lequel les messages sont reçus. Pour prendre en charge ce scénario, le service de routage peut lier des protocoles, notamment le traitement de messages SOAP avec le <xref:System.ServiceModel.Channels.MessageVersion> requis par le ou les points de terminaison de destination. Un protocole peut ainsi être utilisé pour la communication interne, tandis qu'un autre peut être utilisé pour la communication externe.

Pour prendre en charge le routage de messages entre des points de terminaison avec des transports différents, le service de routage utilise des liaisons fournies par le système qui permettent au service de lier des protocoles hétérogènes. Ce pontage s'effectue automatiquement lorsque le point de terminaison de service exposé par le service de routage utilise un autre protocole que les points de terminaison clients vers lesquels les messages sont routés.

## <a name="soap-processing"></a>Traitement SOAP

Un besoin de routage courant est la possibilité de router des messages entre des points de terminaison ayant des spécifications SOAP différentes. Pour prendre en charge cette exigence, le Service de routage fournit un <xref:System.ServiceModel.Routing.SoapProcessingBehavior> qui crée automatiquement un nouveau **MessageVersion** qui répond aux exigences du point de terminaison de destination avant que le message est acheminé vers elle. Ce comportement crée également un **MessageVersion** pour n’importe quel message de réponse avant de le renvoyer à l’application cliente demandeuse, pour vous assurer que le **MessageVersion** de la réponse correspond à celle de la demande d’origine.

Pour plus d’informations sur le traitement SOAP, consultez [Introduction routage](../../../../docs/framework/wcf/feature-details/routing-introduction.md).

## <a name="error-handling"></a>Gestion des erreurs

Dans un système composé de services distribués reposant sur des communications réseau, il est important de s'assurer que les communications dans votre système résistent aux pannes réseau temporaires.  Le service de routage implémente une gestion des erreurs qui permet de gérer de nombreux scénarios de défaillance de communication risquant de provoquer une interruption de service.

Si le service de routage rencontre une exception <xref:System.ServiceModel.CommunicationException> en essayant d'envoyer un message, la gestion des erreurs intervient.  Ces exceptions indiquent en général qu'un problème s'est produit lors de la tentative de communication avec le point de terminaison client défini ; il peut s'agir d'une exception <xref:System.ServiceModel.EndpointNotFoundException>, <xref:System.ServiceModel.ServerTooBusyException> ou <xref:System.ServiceModel.CommunicationObjectFaultedException>.  Le code de gestion des erreurs intercepte également et tentez de nouvelle tentative d’envoi quand un **TimeoutException** se produit, qui est une autre exception courante non dérivée de **CommunicationException**.

Pour plus d’informations sur la gestion des erreurs, consultez [Introduction routage](../../../../docs/framework/wcf/feature-details/routing-introduction.md).

## <a name="backup-endpoints"></a>Points de terminaison de sauvegarde

En plus des points de terminaison clients de destination associés à chaque définition de filtre dans la table de filtres, vous pouvez également créer une liste de points de terminaison de sauvegarde, vers lesquels le message sera routé en cas d'échec de transmission. Si une erreur se produit et qu'une liste de sauvegarde est définie pour l'entrée de filtre, le service de routage essaie d'envoyer le message au premier point de terminaison défini dans la liste. Si cette tentative de transmission échoue, le service essaie le point de terminaison suivant et continue ce processus jusqu'à ce que la tentative de transmission réussisse, retourne une erreur non liée à la transmission ou que tous les points de terminaison de la liste de sauvegarde aient retourné une erreur de transmission.

Pour plus d’informations sur les points de terminaison de sauvegarde, consultez [Introduction routage](../../../../docs/framework/wcf/feature-details/routing-introduction.md) et [filtres de Message](../../../../docs/framework/wcf/feature-details/message-filters.md).

## <a name="streaming"></a>Diffusion en continu

Le service de routage peut diffuser en continu les messages si vous définissez la liaison qui prend en charge la diffusion en continu.  Toutefois, dans certains cas, les messages doivent être mis en mémoire tampon :

- Multidiffusion (mise en mémoire tampon pour créer des copies de message supplémentaires)

- Basculement (mise en mémoire tampon si le message doit être envoyé à une sauvegarde)

- System.ServiceModel.Routing.RoutingConfiguration.RouteOnHeadersOnly a la valeur false (mise en mémoire tampon pour présenter la table MessageFilterTable avec un MessageBuffer afin que les filtres puissent analyser le corps)

- Configuration dynamique

## <a name="see-also"></a>Voir aussi

- [Introduction au routage](../../../../docs/framework/wcf/feature-details/routing-introduction.md)
- [Contrats de routage](../../../../docs/framework/wcf/feature-details/routing-contracts.md)
- [Filtres de message](../../../../docs/framework/wcf/feature-details/message-filters.md)
