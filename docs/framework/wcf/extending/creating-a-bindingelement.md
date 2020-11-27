---
title: Création d’un élément de liaison
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: 285bed029cf8487b37757de6a56075abe448f3ce
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257865"
---
# <a name="creating-a-bindingelement"></a>Création d’un élément de liaison

Les liaisons et les éléments de liaison (objets qui étendent <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> et <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType> , respectivement) sont l’endroit où le modèle d’application Windows Communication Foundation (WCF) est associé aux fabriques de canaux et aux écouteurs de canal. Sans liaisons, l’utilisation de canaux personnalisés requiert la programmation au niveau du canal, comme décrit dans la rubrique programmation du [Service Channel-Level](service-channel-level-programming.md) et programmation du [Channel-Level client](client-channel-level-programming.md). Cette rubrique décrit la configuration minimale requise pour activer l’utilisation de votre canal dans WCF, le développement d’un <xref:System.ServiceModel.Channels.BindingElement> pour votre canal et activer l’utilisation à partir de l’application, comme décrit à l’étape 4 du [développement de canaux](developing-channels.md).  
  
## <a name="overview"></a>Vue d'ensemble  

 La création <xref:System.ServiceModel.Channels.BindingElement> d’un pour votre canal permet aux développeurs de l’utiliser dans une application WCF. <xref:System.ServiceModel.Channels.BindingElement> les objets peuvent être utilisés à partir de la <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> classe pour connecter une application WCF à votre canal sans avoir besoin des informations de type précises de votre canal.  
  
 Une fois qu’un <xref:System.ServiceModel.Channels.BindingElement> a été créé, vous pouvez activer davantage de fonctionnalités en fonction de vos besoins en suivant les étapes de développement de canal restantes décrites dans [développement de canaux](developing-channels.md).  
  
## <a name="adding-a-binding-element"></a>Ajout d'un élément de liaison  

 Pour implémenter un élément <xref:System.ServiceModel.Channels.BindingElement>personnalisé, écrivez une classe qui hérite de <xref:System.ServiceModel.Channels.BindingElement>. Par exemple, si vous avez développé un canal `ChunkingChannel` capable de fragmenter de grands messages en plusieurs segments, puis de les recomposer en fin de traitement, vous pouvez utiliser ce canal sur n'importe quelle liaison en implémentant un élément <xref:System.ServiceModel.Channels.BindingElement> et en configurant la liaison de sorte à ce qu'elle puisse utiliser ce dernier. Un canal `ChunkingChannel` est utilisé à titre d’exemple dans cette rubrique afin d’illustrer les exigences à l’implémentation d’un élément de liaison.  
  
 L'élément `ChunkingBindingElement` est chargé de créer la fabrication `ChunkingChannelFactory` et l'écouteur `ChunkingChannelListener`. Cet élément se substitue aux implémentations <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> et <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> et s'assure que le paramètre de type correspond à <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (il s'agit de la seule forme de canal prise en charge par notre exemple de canal `ChunkingChannel`) et que les autres éléments de liaison dans la liaison prennent effectivement en charge cette forme de canal.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> vérifie au préalable que la forme de canal demandée peut être construite, puis récupère une liste d'actions de message à fragmenter. Cette méthode crée ensuite une fabrication `ChunkingChannelFactory` en lui passant la fabrication de canal interne. Remarque : si vous créez un élément de liaison de transport, cet élément est le dernier dans la pile de liaison. Vous devez, par conséquent, créer un écouteur de canal ou une fabrication de canal.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> utilise une implémentation similaire pour créer `ChunkingChannelListener` et lui passer l'écouteur de canal interne.  
  
 En guise d’autre exemple d’utilisation d’un canal de transport, l’exemple [transport : UDP](../samples/transport-udp.md) fournit la substitution suivante.  
  
 Dans notre exemple, l'élément de liaison est `UdpTransportBindingElement`, lequel dérive de <xref:System.ServiceModel.Channels.TransportBindingElement>. Dans le code ci-dessous se rapportant à notre exemple, les méthodes suivantes sont substituées pour générer les fabrications associées au canal.  
  
```csharp  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Il contient également des membres permettant de cloner `BindingElement` et de retourner notre schéma (soap.udp).  
  
#### <a name="protocol-binding-elements"></a>Protocole d’éléments de liaison  

 Les nouveaux éléments de liaison peuvent remplacer ou augmenter tout élément de liaison inclus en ajoutant de nouveaux transports, encodages ou protocoles de niveau supérieur. Pour créer un nouvel élément de liaison de protocole, commencez par étendre la classe <xref:System.ServiceModel.Channels.BindingElement>. Au minimum, vous devez implémenter <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> et implémenter à l' `ChannelProtectionRequirements` aide de <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType> . Cette opération retourne <xref:System.ServiceModel.Security.ChannelProtectionRequirements> pour l’élément de liaison défini.  Pour plus d’informations, consultez <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> doit retourner une nouvelle copie de cet élément de liaison. Dans le cadre de nos meilleures pratiques, nous vous recommandons d’implémenter, en tant que créateur de cet élément de liaison, la méthode <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> à l’aide d’un constructeur de copie qui appelle le constructeur de copie de base, puis clone tous les champs supplémentaires figurant dans cette classe.  
  
#### <a name="transport-binding-elements"></a>Éléments de liaison de transport  

 Pour créer un nouvel élément de liaison de transport, étendez l’interface <xref:System.ServiceModel.Channels.TransportBindingElement>. Vous devez ensuite implémenter au minimum la méthode <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> et la propriété <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> doit retourner une nouvelle copie de cet élément de liaison.  Dans le cadre de nos meilleures pratiques, nous vous recommandons d’implémenter, en tant que créateur de cet élément de liaison, la méthode de clonage à l’aide d’un constructeur de copie qui appelle le constructeur de copie de base, puis clone tous les champs supplémentaires figurant dans cette classe.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> : la propriété <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> retourne le modèle URI correspondant au protocole de transport représenté par l'élément de liaison. Par exemple, le <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> et le <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> renvoient « http » et « net. TCP » à partir de leurs propriétés respectives <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> .  
  
#### <a name="encoding-binding-elements"></a>Éléments de liaison d’encodage  

 Pour créer un nouvel élément de liaison d'encodage, commencez par étendre la classe <xref:System.ServiceModel.Channels.BindingElement> et implémenter la classe <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>. Vous devez ensuite implémenter au minimum les méthodes <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> ainsi que la propriété <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType>.  
  
- <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Retourne une nouvelle copie de cet élément de liaison. Dans le cadre de nos meilleures pratiques, nous vous recommandons d’implémenter, en tant que créateur de cet élément de liaison, la méthode <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> à l’aide d’un constructeur de copie qui appelle le constructeur de copie de base, puis clone tous les champs supplémentaires figurant dans cette classe.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Retourne une fabrication <xref:System.ServiceModel.Channels.MessageEncoderFactory> qui fournit un handle à la classe effective, laquelle implémente votre nouvel encodeur et doit étendre <xref:System.ServiceModel.Channels.MessageEncoder>. Pour plus d’informations, consultez <xref:System.ServiceModel.Channels.MessageEncoderFactory> et <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. Retourne la version <xref:System.ServiceModel.Channels.MessageVersion> utilisée dans cet encodage, laquelle correspond aux versions de SOAP et WS-Addressing utilisées.  
  
 Pour une liste exhaustive des méthodes et propriétés optionnelles compatibles avec les éléments de liaison d'encodage définis par l'utilisateur, consultez <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Pour plus d’informations sur la création d’un nouvel élément de liaison, consultez [création de liaisons de User-Defined](creating-user-defined-bindings.md).  
  
 Une fois que vous avez créé un élément de liaison pour votre canal, revenez à la rubrique [développement de canaux](developing-channels.md) pour déterminer si vous souhaitez ajouter la prise en charge des fichiers de configuration à votre élément de liaison, si et comment ajouter la prise en charge de la publication des métadonnées, et si et comment construire une liaison définie par l’utilisateur qui utilise votre élément de liaison.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Channels.BindingElement>
- [Développement de canaux](developing-channels.md)
- [Transport : UDP](../samples/transport-udp.md)
