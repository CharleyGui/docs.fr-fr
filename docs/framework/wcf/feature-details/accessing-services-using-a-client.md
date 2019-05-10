---
title: Accès aux services à l'aide d'un client
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
ms.openlocfilehash: 9a38ec444c51560cab48db1b39ae331f728fba30
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635666"
---
# <a name="accessing-services-using-a-client"></a>Accès aux services à l'aide d'un client
Les applications clientes doivent créer, configurer et utiliser des objets de client ou de canal WCF pour communiquer avec les services. Le [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md) rubrique fournit une vue d’ensemble des objets et des étapes impliquées dans la création d’objets de client et le canal de base et leur utilisation.  
  
 Cette rubrique fournit des informations détaillées sur certains aspects liés aux applications clientes et aux objets de client et de canal qui peuvent être utiles selon votre scénario.  
  
## <a name="overview"></a>Vue d'ensemble  
 Cette rubrique décrit le comportement et les problèmes liés aux éléments suivants :  
  
- durées de vie de session et de canal ;  
  
- gestion des exceptions ;  
  
- présentation des problèmes de blocage ;  
  
- initialisation de canaux de manière interactive.  
  
### <a name="channel-and-session-lifetimes"></a>Durées de vie de session et de canal  
 Applications Windows Communication Foundation (WCF) inclut deux catégories de canaux de datagramme et session.  
  
 Un *datagramme* est un canal dans lequel tous les messages sont sans corrélation. Avec un canal de datagramme, si une opération d'entrée ou de sortie échoue, l'opération suivante n'est en général pas affectée et le même canal peut être réutilisé. Pour cette raison, les canaux de datagramme ne subissent généralement pas de défaillance.  
  
 *Session* canaux, sont toutefois, des canaux avec une connexion à l’autre point de terminaison. Les messages dans une session d'un côté sont toujours en corrélation avec la même session de l'autre côté. De plus, les deux participants d'une session doivent s'entendre sur le fait que les spécifications de leur conversation ont été satisfaites pour que cette session soit considérée comme réussie. S'ils ne peuvent se mettre d'accord, le canal de session peut subir une défaillance.  
  
 Ouvrir des clients explicitement ou implicitement en appelant la première opération.  
  
> [!NOTE]
>  Le fait de tenter de détecter de manière explicite des canaux de session défaillants est en général inutile, car le moment où vous en êtes informé dépend de l'implémentation de session. Par exemple, étant donné que le <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> (avec la session fiable désactivée) est à la surface de la session de la connexion TCP, si vous écoutez l'événement <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> sur le service ou le client, vous recevrez sans doute rapidement une notification en cas de panne réseau. Mais les sessions fiables (établies par des liaisons dans lesquelles le <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> est activé) sont conçues pour isoler les services des petites pannes réseau. Si la session peut être rétablie dans un délai raisonnable, la même liaison (configuré pour des sessions fiables) risque de ne subir une défaillance que longtemps après l'interruption.  
  
 La plupart des liaisons fournies par le système (qui exposent des canaux à la couche Application) utilisent des sessions par défaut, ce qui n'est pas le cas du <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>. Pour plus d’informations, consultez [à l’aide de Sessions](../../../../docs/framework/wcf/using-sessions.md).  
  
### <a name="the-proper-use-of-sessions"></a>Utilisation correcte des sessions  
 Les sessions offrent un moyen de savoir si l'intégralité de l'échange de messages a été effectué et si les deux côtés l'ont considéré réussi. Il est recommandé qu'une application appelante ouvre le canal, l'utilise et le ferme à l'intérieur d'un bloc try. Si un canal de session est ouvert, que la méthode <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> est appelée une fois et que cet appel est retourné avec succès, cela signifie que la session a réussi. Le terme « réussi » dans ce cas signifie que toutes les garanties de remise spécifiées par la liaison ont été satisfaites et que l'autre côté n'a pas appelé <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> sur le canal avant d'appeler <xref:System.ServiceModel.ICommunicationObject.Close%2A>.  
  
 La section suivante fournit un exemple de cette approche cliente.  
  
### <a name="handling-exceptions"></a>Gestion des exceptions  
 La gestion des exceptions dans les applications clientes est simple. Si un canal est ouvert, utilisé et fermé à l'intérieur d'un bloc try, cela signifie que la conversation a réussi, à moins qu'une exception ne soit levée. En général, si une exception est levée, la conversation est abandonnée.  
  
> [!NOTE]
>  Utilisation de la `using` instruction (`Using` en Visual Basic) n’est pas recommandée. Cela est dû au fait que la fin de l'instruction `using` peut provoquer des exceptions qui peuvent masquer d'autres exceptions dont vous devez avoir connaissance. Pour plus d’informations, consultez [utilisez fermer et abandon pour libérer les ressources de client WCF](../../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md).  
  
 L'exemple de code suivant illustre le modèle client recommandé à l'aide d'un bloc try/catch, et non de l'instruction `using`.  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  La vérification de la valeur de la propriété <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> est une condition de concurrence et n'est pas recommandée pour déterminer s'il faut réutiliser ou fermer un canal.  
  
 Les canaux de datagramme ne subissent jamais de défaillance, même si des exceptions se produisent lorsqu'ils sont fermés. De plus, les clients non-duplex qui ne parviennent pas à s'authentifier à l'aide d'une conversation sécurisée lèvent en général une exception <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>. Toutefois, si le client duplex qui utilise une conversation sécurisée ne parvient pas à s'authentifier, il reçoit une exception <xref:System.TimeoutException?displayProperty=nameWithType>.  
  
 Pour obtenir des informations plus complètes sur l’utilisation des informations d’erreur au niveau de l’application, consultez [spécification et gestion des erreurs dans les contrats et Services](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). [Exceptions attendues](../../../../docs/framework/wcf/samples/expected-exceptions.md) décrit les exceptions attendues et montre comment les gérer. Pour plus d’informations sur la gestion des erreurs lors du développement de canaux, consultez [gestion des Exceptions et erreurs](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
### <a name="client-blocking-and-performance"></a>Blocage de client et performances  
 Lorsqu'une application appelle une opération demande-réponse de façon synchrone, le client se bloque jusqu'à ce qu'une valeur de retour soit reçue ou qu'une exception (par exemple <xref:System.TimeoutException?displayProperty=nameWithType>) soit levée. Ce comportement est semblable au comportement local. Lorsqu’une application appelle une opération sur un objet client WCF ou un canal de façon synchrone, le client ne retourne pas jusqu'à ce que la couche de canal peut écrire les données dans le réseau ou jusqu'à ce qu’une exception est levée. Et bien que le modèle d’échange de messages unidirectionnel (spécifié en marquant une opération avec <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> défini à `true`) puisse améliorer la capacité de réponse de certains clients, les opérations unidirectionnelles peuvent également subir un blocage, en fonction de la liaison et des messages qui ont déjà été envoyés. Les opérations unidirectionnelles concernent uniquement l'échange de messages, ni plus ni moins. Pour plus d’informations, consultez [unidirectionnel Services](../../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
 Les grands segments de données peuvent ralentir le traitement client, quel que soit le modèle d’échange de messages. Pour comprendre comment gérer ces problèmes, consultez [données volumineuses et diffusion en continu](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
 Si votre application doit effectuer plus de travail pendant une opération se termine, vous devez créer une paire de méthodes asynchrones sur l’interface de contrat de service qui implémente votre client WCF. Le moyen le plus simple pour ce faire consiste à utiliser le `/async` basculer le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Pour voir un exemple, consultez [Comment : Appeler des opérations de Service de façon asynchrone](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).  
  
 Pour plus d’informations sur les performances de client croissant, consultez [Applications clientes de niveau intermédiaire](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md).  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>Autoriser l'utilisateur à sélectionner des informations d'identification de manière dynamique  
 L'interface <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> permet aux applications d'afficher une interface utilisateur qui permet à l'utilisateur de choisir des informations d'identification avec lesquelles un canal est créé avant le démarrage des minuteries de délai d'attente.  
  
 Les développeurs d'applications peuvent utiliser un <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> inséré de deux façons. L’application cliente peut appeler <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (ou une version asynchrone) avant d’ouvrir le canal (le *explicite* approche) ou appeler la première opération (le *implicite*approche).  
  
 Lors de l’utilisation de l’approche implicite, l’application doit appeler la première opération sur une extension <xref:System.ServiceModel.ClientBase%601> ou <xref:System.ServiceModel.IClientChannel>. Si elle appelle une autre opération que la première, une exception est levée.  
  
 Lors de l'utilisation de l'approche explicite, l'application doit exécuter les étapes suivantes, dans l'ordre :  
  
1. Appelez <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (ou une version asynchrone).  
  
2. Lorsque les initialiseurs ont retourné, appelez la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A> sur l'objet <xref:System.ServiceModel.IClientChannel> ou sur l'objet <xref:System.ServiceModel.IClientChannel> retourné par la propriété <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType>.  
  
3. Appelez les opérations.  
  
 Il est recommandé que les applications de qualité de production contrôlent le processus d'interface utilisateur en adoptant l'approche explicite.  
  
 Les applications qui utilisent l'approche implicite appellent les initialiseurs d'interface utilisateur, mais si l'utilisateur de l'application ne répond pas avant la fin du délai d'attente d'envoi de la liaison, une exception est levée lorsque l'interface utilisateur retourne.  
  
## <a name="see-also"></a>Voir aussi

- [Services duplex](../../../../docs/framework/wcf/feature-details/duplex-services.md)
- [Guide pratique pour Accéder aux Services avec unidirectionnel et contrats demande-réponse](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [Guide pratique pour Access Services avec un contrat Duplex](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [Guide pratique pour Accéder à un service WSE 3.0 Service](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [Guide pratique pour Utiliser la classe ChannelFactory](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
- [Guide pratique pour Appeler des opérations de Service de façon asynchrone](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [Applications clientes de niveau intermédiaire](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)
