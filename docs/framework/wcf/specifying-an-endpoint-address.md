---
title: Spécification d'une adresse de point de terminaison
description: En savoir plus sur une adresse de point de terminaison, une partie d’un ServiceEndpoint dans WCF. Toutes les communications avec un service WCF se produisent par le biais de ses points de terminaison.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- endpoints [WCF], addressing
ms.assetid: ac24f5ad-9558-4298-b168-c473c68e819b
ms.openlocfilehash: e1bd9e5a27d1bc86d2d3e04ee82221a27a4e1fa8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245982"
---
# <a name="specifying-an-endpoint-address"></a>Spécification d'une adresse de point de terminaison

Toutes les communications avec un service Windows Communication Foundation (WCF) se produisent par le biais de ses points de terminaison. Chaque <xref:System.ServiceModel.Description.ServiceEndpoint> contient un <xref:System.ServiceModel.Description.ServiceEndpoint.Address%2A>, un <xref:System.ServiceModel.Description.ServiceEndpoint.Binding%2A> et un <xref:System.ServiceModel.Description.ServiceEndpoint.Contract%2A>. Le contrat spécifie quelles opérations sont disponibles. La liaison spécifie comment communiquer avec le service et l’adresse spécifie où rechercher le service. Chaque point de terminaison doit avoir une adresse unique. L’adresse de point de terminaison est représentée par la classe <xref:System.ServiceModel.EndpointAddress>, qui contient un URI (Uniform Resource Identifier) représentant l’adresse du service, un <xref:System.ServiceModel.EndpointAddress.Identity%2A> représentant l’identité de sécurité du service et une collection de <xref:System.ServiceModel.EndpointAddress.Headers%2A> facultative. Les en-têtes facultatifs fournissent des informations d'adressage plus détaillées pour identifier ou interagir avec le point de terminaison. Par exemple, les en-tête peuvent indiquer comment traiter un message entrant, où le point de terminaison doit envoyer un message de réponse ou quelle instance d'un service utiliser pour traiter un message entrant d'un utilisateur particulier lorsque plusieurs instances sont disponibles.

## <a name="definition-of-an-endpoint-address"></a>Définition d'une adresse de point de terminaison

Dans WCF, un <xref:System.ServiceModel.EndpointAddress> modélise une référence de point de terminaison (EPR) telle que définie dans la norme WS-Addressing.

L'URI d'adresse de la plupart des transports se compose de quatre parties. Par exemple, cet URI `http://www.fabrikam.com:322/mathservice.svc/secureEndpoint` possède les quatre parties suivantes :

- Schéma : http:

- Usinage`www.fabrikam.com`

- (Facultatif) Port : 322

- Chemin d’accès : /mathservice.svc/secureEndpoint

Une partie du modèle ERP établit que chaque référence de point de terminaison peut contenir des paramètres de référence qui ajoutent des informations d'identification supplémentaires. Dans WCF, ces paramètres de référence sont modélisés en tant qu’instances de la <xref:System.ServiceModel.Channels.AddressHeader> classe.

L'adresse du point de terminaison pour un service peut être spécifiée de manière impérative en utilisant le code ou de façon déclarative par la configuration. La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service. En général, il est plus pratique de définir des points de terminaison de service à l'aide de la configuration plutôt que du code. Le fait de conserver les informations de liaison et d'adressage hors du code leur permet de changer sans devoir recompiler ou de redéployer l'application. Si aucun point de terminaison n'est spécifié dans le code ou dans la configuration, le runtime ajoute un point de terminaison par défaut sur chaque adresse de base pour chaque contrat implémenté par le service.

Il existe deux façons de spécifier des adresses de point de terminaison pour un service dans WCF. Vous pouvez spécifier une adresse absolue pour chaque point de terminaison associé au service ou vous pouvez fournir une adresse de base pour le <xref:System.ServiceModel.ServiceHost> d'un service puis spécifier une adresse pour chaque point de terminaison associé à ce service défini comme relatif à cette adresse de base. Vous pouvez utiliser chacune de ces procédures pour spécifier les adresses de point de terminaison pour un service dans la configuration ou le code. Si vous ne spécifiez pas d'adresse relative, le service utilise l'adresse de base. Vous pouvez également avoir plusieurs adresses de base pour un service, mais une seule adresse de base pour chaque transport est autorisée pour chaque service. Si vous avez plusieurs points de terminaison, chacun configuré avec une liaison différente, leurs adresses doivent être uniques. Les points de terminaison qui utilisent la même liaison mais des contrats différents peuvent utiliser la même adresse.

Lorsque vous hébergez avec les services IIS, vous ne gérez pas l'instance <xref:System.ServiceModel.ServiceHost> vous-même. L'adresse de base est toujours l'adresse spécifiée dans le fichier .svc pour le service lors de l'hébergement dans IIS. Par conséquent, vous devez toujours utiliser des adresses de point de terminaison relatives pour les points de terminaison de service hébergés dans IIS. Fournir une adresse de point de terminaison qualifiée complète peut entraîner des erreurs lors du déploiement du service. Pour plus d’informations, consultez [déploiement d’un service WCF hébergé par Internet Information Services](./feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).

## <a name="defining-endpoint-addresses-in-configuration"></a>Définition des adresses de point de terminaison dans la configuration

Pour définir un point de terminaison dans un fichier de configuration, utilisez l' [\<endpoint>](../configure-apps/file-schema/wcf/endpoint-element.md) élément.

[!code-xml[S_UEHelloWorld#5](./snippets/specifying-an-endpoint-address/serviceapp2.config#5)]

Lorsque la <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> méthode est appelée (autrement dit, lorsque l’application d’hébergement tente de démarrer le service), le système recherche un [\<service>](../configure-apps/file-schema/wcf/service.md) élément avec un attribut de nom qui spécifie «UE. Samples. HelloService». Si l' [\<service>](../configure-apps/file-schema/wcf/service.md) élément est trouvé, le système charge la classe spécifiée et crée des points de terminaison à l’aide des définitions de point de terminaison fournies dans le fichier de configuration. Ce mécanisme vous permet de charger et de démarrer un service avec deux lignes de code tout en laissant la liaison et les informations d’adressage hors de votre code. L'avantage de cette approche est que ces modifications peuvent être apportées sans devoir recompiler ou redéployer l'application.

Les en-têtes facultatifs sont déclarés dans un [\<headers>](../configure-apps/file-schema/wcf/headers-element.md) . Voici un exemple des éléments utilisés pour spécifier des points de terminaison pour un service dans un fichier de configuration qui fait la distinction entre deux en-têtes : les clients « or » de `http://tempuri1.org/` et les clients « standard » de `http://tempuri2.org/` . Le client qui appelle ce service doit disposer de la appropriée [\<headers>](../configure-apps/file-schema/wcf/headers-element.md) dans son fichier de configuration.

[!code-xml[S_UEHelloWorld#1](./snippets/specifying-an-endpoint-address/serviceapp.config#1)]

Les en-tête peuvent également être définis sur les messages individuels au lieu de tous les messages sur un point de terminaison (comme montré précédemment). Pour cela, vous devez utiliser <xref:System.ServiceModel.OperationContextScope> pour créer un nouveau contexte dans une application cliente afin d'ajouter un en-tête personnalisé au message sortant, comme illustré dans l'exemple suivant.

[!code-csharp[OperationContextScope#4](../../../samples/snippets/csharp/VS_Snippets_CFX/operationcontextscope/cs/client.cs#4)]
[!code-vb[OperationContextScope#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/operationcontextscope/vb/client.vb#4)]

## <a name="endpoint-address-in-metadata"></a>Adresse de point de terminaison dans les métadonnées

Une adresse de point de terminaison est représentée dans WSDL (Web Services Description Language) comme un élément `EndpointReference` (EPR) WS-Addressing dans l'élément `wsdl:port` du point de terminaison correspondant. L'EPR contient l'adresse du point de terminaison ainsi que toutes les propriétés d'adresse. Notez que l'EPR à l'intérieur de `wsdl:port` remplace `soap:Address` comme dans l'exemple suivant.

## <a name="defining-endpoint-addresses-in-code"></a>Définition d'adresses de point de terminaison dans le code

Une adresse de point de terminaison peut être créée dans le code avec la classe <xref:System.ServiceModel.EndpointAddress>. L’URI spécifié pour l’adresse de point de terminaison peut être un chemin d’accès qualifié complet ou un chemin d’accès qui est relatif à l’adresse de base du service. L'exemple de code suivant illustre la création d'une nouvelle instance de la classe <xref:System.ServiceModel.EndpointAddress> et son ajout à l'instance <xref:System.ServiceModel.ServiceHost> qui héberge le service.

L'exemple suivant montre comment spécifier l'adresse de point de terminaison complète dans le code.

[!code-csharp[S_UEHelloWorld#2](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#2)]

L'exemple suivant montre comment ajouter une adresse relative ("MyService") à l'adresse de base de l'hôte de service.

[!code-csharp[S_UEHelloWorld#3](../../../samples/snippets/csharp/VS_Snippets_CFX/s_uehelloworld/cs/snippet.cs#3)]

> [!NOTE]
> Les propriétés de <xref:System.ServiceModel.Description.ServiceDescription> dans l'application de service ne doivent pas être modifiées à l'issue de la méthode <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> sur <xref:System.ServiceModel.ServiceHostBase>. Certains membres, tels que la propriété <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> et les méthodes `AddServiceEndpoint` sur <xref:System.ServiceModel.ServiceHostBase> et <xref:System.ServiceModel.ServiceHost>, lèvent une exception s'ils sont modifiés au-delà de ce point. D'autres membres peuvent être modifiés, mais le résultat n'est pas défini.
>
> De la même façon, sur le client les valeurs <xref:System.ServiceModel.Description.ServiceEndpoint> ne doivent pas être modifiées après l'appel à <xref:System.ServiceModel.Channels.CommunicationObject.OnOpening%2A> sur <xref:System.ServiceModel.ChannelFactory>. La propriété <xref:System.ServiceModel.ChannelFactory.Credentials%2A> lève une exception si elle est modifiée au-delà de ce point. Les autres valeurs de description du client peuvent être modifiées sans erreur, mais le résultat n'est pas défini.
>
> Aussi bien pour le service que le client, il est recommandé de modifier la description avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>.

## <a name="using-default-endpoints"></a>Utilisation des points de terminaison par défaut

Si aucun point de terminaison n'est spécifié dans le code ou dans la configuration, le runtime fournit les points de terminaison par défaut en ajoutant un point de terminaison par défaut sur chaque adresse de base pour chaque contrat de service implémenté par le service. L'adresse de base peut être spécifiée dans le code ou dans la configuration, et les points de terminaison par défaut sont ajoutés lors de l'appel de <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> sur le <xref:System.ServiceModel.ServiceHost>.

Si des points de terminaison sont fournis explicitement, les points de terminaison par défaut peuvent toujours être ajoutés en appelant <xref:System.ServiceModel.ServiceHostBase.AddDefaultEndpoints%2A> sur le <xref:System.ServiceModel.ServiceHost> avant d'appeler <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A>. Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](simplified-configuration.md) et [Configuration simplifiée pour les services WCF](./samples/simplified-configuration-for-wcf-services.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.EndpointAddress>
- [Identité du service et authentification](./feature-details/service-identity-and-authentication.md)
- [Vue d'ensemble de la création de points de terminaison](endpoint-creation-overview.md)
- [Hosting](./feature-details/hosting.md)
