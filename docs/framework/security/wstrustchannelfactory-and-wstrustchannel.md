---
title: WSTrustChannelFactory et WSTrustChannel
ms.date: 03/30/2017
ms.assetid: 96cec467-e963-4132-b18b-7d0b3a2e979f
author: BrucePerlerMS
ms.openlocfilehash: e00f3ae25a50c2fb3f34f4c04d02cde574b3da17
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044916"
---
# <a name="wstrustchannelfactory-and-wstrustchannel"></a>WSTrustChannelFactory et WSTrustChannel
Si vous êtes familiarisé avec Windows Communication Foundation (WCF), vous savez probablement que les clients WCF prennent déjà en charge la fédération. En configurant un client WCF avec une liaison <xref:System.ServiceModel.WSFederationHttpBinding> ou une liaison personnalisée similaire, vous pouvez utiliser l’authentification fédérée auprès d’un service.

 WCF obtient le jeton qui est émis par le service d’émission de jeton de sécurité (STS) en arrière-plan et utilise ce jeton pour s’authentifier auprès du service. La principale limitation de cette approche est que vous n’avez pas de visibilité sur les communications entre le client et le serveur. WCF génère automatiquement le jeton de sécurité de demande (RST) à envoyer au STS sur la base des paramètres du jeton émis sur la liaison. Cela signifie que le client ne peut pas modifier les paramètres RST d’une demande à l’autre, inspecter la réponse de jeton de sécurité de demande (RSTR) pour obtenir des informations telles que les revendications d’affichage ou mettre en cache le jeton pour une utilisation ultérieure.

 Le client WCF est approprié pour les scénarios de fédération de base. Toutefois, l’un des principaux scénarios que Windows Identity Foundation (WIF) prend en charge nécessite un contrôle du RST à un niveau que WCF n’autorise pas facilement. C’est pourquoi WIF offre des fonctionnalités supplémentaires qui vous aident à mieux contrôler les communications avec le STS.

 WIF prend en charge les scénarios de fédération suivants :

- Utilisation d’un client WCF sans dépendance à WIF pour l’authentification auprès d’un service fédéré

- Activation de WIF sur un client WCF pour insérer un élément ActAs ou OnBehalfOf dans le RST pour le STS

- Utilisation de WIF seul pour obtenir un jeton du STS et permettre à un client WCF de s’authentifier avec ce jeton. Pour plus d’informations, consultez l’exemple [ClaimsAwareWebService](https://go.microsoft.com/fwlink/?LinkID=248406).

 Le premier scénario est explicite : Les clients WCF existants continuent de fonctionner avec les parties de confiance WIF et émission. Cette rubrique explique les deux autres scénarios.

## <a name="enhancing-an-existing-wcf-client-with-actas--onbehalfof"></a>Amélioration d’un client WCF existant avec ActAs/OnBehalfOf
Dans un scénario de délégation d’identité standard, un client appelle un service de niveau intermédiaire, lequel appelle un service principal. Le service de niveau intermédiaire agit en tant que client ou pour le compte du client.

> [!TIP]
> Quelle est la différence entre ActAs et OnBehalfOf ?
>
> Du point de vue du protocole WS-Trust :
>
> 1. Un élément RST ActAs indique que le demandeur souhaite obtenir un jeton qui contient les revendications sur deux entités distinctes : le demandeur, et une entité externe représentée par le jeton situé dans l’élément ActAs.
> 2. Un élément RST OnBehalfOf indique que le demandeur souhaite obtenir un jeton qui contient les revendications sur une seule entité : l’entité externe représentée par le jeton situé dans l’élément OnBehalfOf.
>
> La fonctionnalité ActAs est généralement utilisée dans les scénarios qui nécessitent une délégation composite, c’est-à-dire où le destinataire final du jeton émis peut inspecter la chaîne de délégation entière et voir non seulement le client, mais tous les intermédiaires. Ce destinataire peut ainsi effectuer un contrôle d’accès, l’audit et d’autres activités associées en fonction de la chaîne de délégation d’identité entière. La fonctionnalité ActAs est couramment utilisée dans les systèmes multiniveaux pour authentifier et passer des informations sur les identités entre les niveaux sans devoir passer ces informations à la couche logique application/métier.
>
> La fonctionnalité OnBehalfOf est utilisée dans les scénarios où seule l’identité du client d’origine est importante. Elle est identique à la fonctionnalité d’emprunt d’identité disponible dans Windows. Quand OnBehalfOf est utilisé, le destinataire final du jeton émis peut uniquement voir les revendications sur le client d’origine, car les informations sur les intermédiaires ne sont pas conservées. La fonctionnalité OnBehalfOf est souvent utilisée dans un modèle proxy où le client ne peut pas accéder au STS directement et, à la place, communique par le biais d’une passerelle proxy. La passerelle proxy authentifie l’appelant et place les informations sur l’appelant dans l’élément OnBehalfOf du message RST qu’elle envoie ensuite au STS pour le traitement. Le jeton résultant contient uniquement des revendications relatives au client du proxy, ce qui rend le proxy complètement transparent pour le destinataire du jeton émis. Notez que WIF ne permet pas l’utilisation de \<wsse:SecurityTokenReference> ou \<wsa:EndpointReferences> comme enfant de \<wst:OnBehalfOf>. La spécification WS-Trust permet d’identifier le demandeur d’origine (au nom de qui le proxy agit) selon trois méthodes. Ces règles sont les suivantes :
>
> - Référence à un jeton de sécurité. Il s’agit d’une référence à un jeton dans le message ou, éventuellement, récupéré hors bande.
> - Référence à un point de terminaison. Cette référence est utilisée comme clé pour la recherche de données hors bande.
> - Jeton de sécurité. Identifie le demandeur d’origine directement.
>
> WIF prend uniquement en charge les jetons de sécurité, chiffrés ou non chiffrés, utilisés comme éléments enfants directs de \<wst:OnBehalfOf>.

 Ces informations sont transmises à un émetteur WS-Trust à l’aide des éléments de jeton ActAs et OnBehalfOf du RST.

 WCF expose un point d’extensibilité sur la liaison qui permet aux éléments XML arbitraires d’être ajoutés au RST. Toutefois, étant donné que le point d’extensibilité est joint à la liaison, les scénarios qui nécessitent que le contenu RST varie d’un appel à l’autre doivent recréer le client pour chaque appel, ce qui diminue les performances. WIF utilise des méthodes d’extension sur la classe `ChannelFactory` pour permettre aux développeurs de joindre des jetons obtenus hors bande au RST. L’exemple de code suivant montre comment utiliser un jeton représentant le client (par exemple, un jeton X.509, de nom d’utilisateur ou SAML) et le joindre au RST envoyé à l’émetteur.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelActingAs<IHelloService>(clientSamlToken);
serviceChannel.Hello("Hi!");
```

 WIF offre les avantages suivants :

- Le RST peut être modifié au niveau de chaque canal. Les services de niveau intermédiaire n’ont donc pas besoin de recréer la fabrique de canaux pour chaque client, ce qui améliore les performances.

- Pour les clients WCF existants, cela permet de mettre à niveau facilement les services de niveau intermédiaire WCF existants pour proposer une sémantique de délégation d’identité.

 Toutefois, ce scénario n’offre pas non plus de visibilité sur les communications entre le client et le STS. Nous examinerons cela dans le troisième scénario.

## <a name="communicating-directly-with-an-issuer-and-using-the-issued-token-to-authenticate"></a>Communication directe avec un émetteur et utilisation du jeton émis pour l’authentification
Dans certains scénarios avancés, l’amélioration d’un client WCF n’est pas une option suffisante. Les développeurs qui utilisent uniquement WCF choisissent généralement des contrats de type Entrée de message/Sortie de message et gèrent manuellement l’analyse côté client de la réponse de l’émetteur.

WIF introduit les classes <xref:System.ServiceModel.Security.WSTrustChannelFactory> et <xref:System.ServiceModel.Security.WSTrustChannel> pour permettre au client de communiquer directement avec un émetteur WS-Trust. Les classes <xref:System.ServiceModel.Security.WSTrustChannelFactory> et <xref:System.ServiceModel.Security.WSTrustChannel> permettent la transmission d’objets RST et RSTR fortement typés entre le client et l’émetteur, comme cela est montré dans l’exemple de code suivant.

```csharp
WSTrustChannelFactory trustChannelFactory = new WSTrustChannelFactory(stsBinding, stsAddress);
WSTrustChannel channel = (WSTrustChannel) trustChannelFactory.CreateChannel();
RequestSecurityToken rst = new RequestSecurityToken(RequestTypes.Issue);
rst.AppliesTo = new EndpointAddress(serviceAddress);
RequestSecurityTokenResponse rstr = null;
SecurityToken token = channel.Issue(rst, out rstr);
```

Notez que le paramètre `out` sur la méthode <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A> autorise l’accès à la réponse RSTR pour l’inspection côté client.

Jusqu’à présent, vous n’avez vu que l’obtention d’un jeton. Le jeton retourné à partir de l’objet <xref:System.ServiceModel.Security.WSTrustChannel> est un `GenericXmlSecurityToken` qui contient toutes les informations nécessaires pour l’authentification auprès d’une partie de confiance. L’exemple de code suivant montre comment utiliser ce jeton.

```csharp
IHelloService serviceChannel = channelFactory.CreateChannelWithIssuedToken<IHelloService>( token );
serviceChannel.Hello("Hi!");
```

La méthode d’extension <xref:System.ServiceModel.ChannelFactory%601.CreateChannelWithIssuedToken%2A> sur l’objet `ChannelFactory` indique à WIF que vous avez obtenu un jeton hors bande et qu’il doit arrêter l’appel WCF standard à l’émetteur et utiliser à la place le jeton obtenu pour s’authentifier auprès de la partie de confiance. Cela présente les avantages suivants :

- Cela vous permet de contrôler entièrement le processus d’émission de jeton.

- Cela permet la prise en charge des scénarios ActAs/OnBehalfOf en définissant directement ces propriétés sur le RST sortant.

- Cela permet de prendre des décisions d’approbation côté client de façon dynamique en fonction du contenu de la réponse RSTR.

- Cela vous permet de mettre en cache et de réutiliser le jeton retourné par la méthode <xref:System.ServiceModel.Security.WSTrustChannel.Issue%2A>.

- <xref:System.ServiceModel.Security.WSTrustChannelFactory> et <xref:System.ServiceModel.Security.WSTrustChannel> permettent de contrôler la sémantique de mise en cache, de gestion des erreurs et de récupération de canal d’après les bonnes pratiques WCF.

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités WIF](wif-features.md)
