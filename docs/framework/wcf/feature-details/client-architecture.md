---
title: Architecture du client
ms.date: 03/30/2017
ms.assetid: 02624403-0d77-41cb-9a86-ab55e98c7966
ms.openlocfilehash: c873368b82551312d203eb28d208eb6e3f50c89b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586999"
---
# <a name="client-architecture"></a>Architecture du client
Les applications utilisent des objets clients Windows Communication Foundation (WCF) pour appeler des opérations de service. Cette rubrique décrit les objets de client WCF, les canaux clients WCF et leurs relations avec l’architecture de canal sous-jacente. Pour une vue d’ensemble des objets clients WCF, consultez [vue d’ensemble du client WCF](../wcf-client-overview.md). Pour plus d’informations sur la couche de canal, consultez [extension de la couche de canal](../extending/extending-the-channel-layer.md).  
  
## <a name="overview"></a>Vue d’ensemble  
 L’heure d’exécution du modèle de service crée des clients WCF, qui sont composés des éléments suivants :  
  
- Implémentation de client générée automatiquement d'un contrat de service qui transforme les appels de votre code d'application en messages sortants, les messages de réponse en paramètres de sortie et retourne des valeurs pouvant être récupérées par votre application.  
  
- Implémentation d'une interface de contrôle (<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>) qui regroupe différentes interfaces et fournit l'accès au contrôle des fonctionnalités, plus précisément aux fonctionnalités permettant de fermer la session client et de déployer le canal.  
  
- Canal de client construit en fonction des paramètres de configuration spécifiés par la liaison utilisée.  
  
 Les applications peuvent créer de tels clients à la demande, à l’aide d’un <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> ou en créant une instance d’une <xref:System.ServiceModel.ClientBase%601> classe dérivée telle qu’elle est générée par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md). Ces classes de client déjà construites encapsulent une implémentation de canal de client construite dynamiquement par un <xref:System.ServiceModel.ChannelFactory> et délèguent vers cette implémentation. Par conséquent, cette rubrique traite principalement des canaux de client et de la fabrication de canal à leur origine.  
  
## <a name="client-objects-and-client-channels"></a>Objets et canaux de client  
 L’interface de base des clients WCF est l' <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> interface, qui expose les fonctionnalités principales du client ainsi que les fonctionnalités d’objet de communication de base de <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType> , la fonctionnalité de contexte de <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType> et le comportement extensible de <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType> .  
  
 Toutefois, l'interface <xref:System.ServiceModel.IClientChannel> ne définit pas de contrat de service. Ceux-ci sont déclarés par l’interface de contrat de service (généralement générée à partir de métadonnées de service à l’aide d’un outil tel que [ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)). Les types de clients WCF étendent <xref:System.ServiceModel.IClientChannel> à la fois et l’interface de contrat de service cible pour permettre aux applications d’appeler des opérations directement et d’avoir accès aux fonctionnalités d’exécution côté client. La création d’un client WCF fournit <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> des objets WCF avec les informations nécessaires pour créer une exécution qui peut se connecter et interagir avec le point de terminaison de service configuré.  
  
 Comme mentionné précédemment, les deux types de clients WCF doivent être configurés avant de pouvoir être utilisés. Les types de clients WCF les plus simples sont des objets qui dérivent de <xref:System.ServiceModel.ClientBase%601> (ou <xref:System.ServiceModel.DuplexClientBase%601> si le contrat de service est un contrat duplex). Vous pouvez créer ces types en utilisant un constructeur (ou un fichier de configuration) configuré par un programme, puis appelé directement pour appeler les opérations de service. Pour une vue d’ensemble des <xref:System.ServiceModel.ClientBase%601> objets, consultez [vue d’ensemble du client WCF](../wcf-client-overview.md).  
  
 Le second type est généré pendant l'exécution depuis un appel de la méthode <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A>. Les applications concernées par un contrôle étroit des caractéristiques de communication utilisent généralement ce type de client, appelé *objet de canal client*, car il permet une interaction plus directe que le système d’exécution de client sous-jacent et le système de canaux.  
  
## <a name="channel-factories"></a>Fabrication de canal  
 La classe qui est chargée de créer le processus d'exécution sous-jacent prenant en charge les appels de client correspond à <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Les objets de client WCF et les objets de canal client WCF utilisent un <xref:System.ServiceModel.ChannelFactory%601> objet pour créer des instances ; l' <xref:System.ServiceModel.ClientBase%601> objet client dérivé encapsule la gestion de la fabrique de canal, mais pour un certain nombre de scénarios, il est tout à fait raisonnable d’utiliser la fabrique de canal directement. Vous souhaiterez le plus souvent créer à plusieurs reprises de nouveaux canaux de client à partir de la fabrication de canal existante. Si vous utilisez un objet client, vous pouvez obtenir la fabrique de canal sous-jacente à partir d’un objet client WCF en appelant la <xref:System.ServiceModel.ClientBase%601.ChannelFactory%2A?displayProperty=nameWithType> propriété.  
  
 Concernant les fabrications de canaux, il est important de garder à l'esprit qu'elles créent des nouvelles instances de canaux de client pour la configuration fournie avant l'appel de la méthode <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>. Une fois que vous avez appelé <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> (ou <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> , <xref:System.ServiceModel.ClientBase%601.CreateChannel%2A?displayProperty=nameWithType> ou toute opération sur un objet client WCF), vous ne pouvez pas modifier la fabrique de canaux et vous attendre à obtenir des canaux pour différentes instances de service, même si vous modifiez simplement l’adresse du point de terminaison cible. Si vous souhaitez créer un objet de client ou un canal de client avec une configuration différente, vous devez d'abord créer une nouvelle fabrication de canal.  
  
 Pour plus d’informations sur les différents problèmes liés à l’utilisation d’objets clients WCF et de canaux clients WCF, consultez [accès aux services à l’aide d’un client WCF](accessing-services-using-a-client.md).  
  
 Les deux sections suivantes décrivent la création et l’utilisation d’objets de canal client WCF.  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Création d'un nouvel objet de canal de client WCF  
 Dans notre exemple illustrant l'utilisation d'un canal de client, nous supposons que le contrat de service suivant a été généré.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Pour vous connecter à un service `ISampleService`, utilisez l'interface de contrat générée directement avec une fabrication de canal (<xref:System.ServiceModel.ChannelFactory%601>). Après avoir créé et configuré une fabrication de canal pour un contrat particulier, vous pouvez appeler la méthode <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A> pour retourner des objets de canal de client qui vous permettront de communiquer avec un service `ISampleService`.  
  
 Lorsque vous utilisez la classe <xref:System.ServiceModel.ChannelFactory%601> avec une interface de contrat de service, vous devez effectuer une conversion de type dans l'interface <xref:System.ServiceModel.IClientChannel> pour ouvrir, fermer ou abandonner le canal de manière explicite. Pour faciliter son utilisation, l'outil Svcutil.exe génère également une interface d'assistance qui implémente à la fois l'interface de contrat de service et <xref:System.ServiceModel.IClientChannel> afin de vous permettre d'interagir avec l'infrastructure de canal client sans devoir convertir de type. Le code suivant illustre la définition d'un canal client d'assistance qui implémente le contrat de service précédent.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
#### <a name="creating-a-new-wcf-client-channel-object"></a>Création d'un nouvel objet de canal de client WCF  
 Pour utiliser un canal client et se connecter à un service `ISampleService`, utilisez directement l’interface de contrat générée (ou la version d’assistance) avec une fabrication de canal, en passant le type de l’interface de contrat comme paramètre de type. Après avoir créé et configuré une fabrication de canal pour un contrat particulier, vous pouvez appeler la méthode <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> pour retourner des objets de canal client qui vous permettront de communiquer avec un service `ISampleService`.  
  
 Une fois créés, les objets de canal de client implémentent <xref:System.ServiceModel.IClientChannel> ainsi que l'interface de contrat. Par conséquent, vous pouvez les utiliser directement pour appeler les opérations qui interagissent avec un service prenant en charge le contrat.  
  
 La différence entre les objets de client et les objets de canal de client réside dans leurs modalités de contrôle et leur simplicité d'utilisation. De nombreux développeurs qui sont à l’aise avec l’utilisation des classes et des objets préfèrent utiliser l’objet client WCF au lieu du canal client WCF.  
  
 Pour obtenir un exemple, consultez [Comment : utiliser ChannelFactory](how-to-use-the-channelfactory.md).
