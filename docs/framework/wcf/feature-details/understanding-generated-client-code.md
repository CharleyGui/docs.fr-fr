---
title: Fonctionnement du code client généré
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c3f6e4b0-1131-4c94-aa39-a197c5c2f2ca
ms.openlocfilehash: 22cb7a7b4cd6712d509586cb2ae7699d233eff2a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96281623"
---
# <a name="understanding-generated-client-code"></a>Fonctionnement du code client généré

L' [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) génère du code client et un fichier de configuration d'application cliente à des fins de création d’applications clientes. Cette rubrique présente des exemples de code généré pour des scénarios de contrat de service standard. Pour plus d’informations sur la création d’une application cliente à l’aide du code généré, consultez [vue d’ensemble du client WCF](../wcf-client-overview.md).  
  
## <a name="overview"></a>Vue d'ensemble  

 Si vous utilisez Visual Studio pour générer des types de clients Windows Communication Foundation (WCF) pour votre projet, vous n’avez généralement pas besoin d’examiner le code client généré. Si vous n'utilisez pas un environnement de développement qui exécute les mêmes services pour vous, vous pouvez utiliser un outil tel que Svcutil.exe pour générer le code client, puis utiliser ce code pour développer votre application cliente.  
  
 Svcutil.exe disposant de plusieurs options qui modifient les informations de type générées, cette rubrique ne traite pas de tous les scénarios. Toutefois, les tâches standard suivantes impliquent la localisation de code généré :  
  
- Identification d'interfaces de contrat de service.  
  
- Identification de la classe de client WCF.  
  
- Identification des types de données.  
  
- Identification des contrats de rappel pour les services duplex.  
  
- Identification de l'interface de canal de contrat de service d'assistance.  
  
### <a name="finding-service-contract-interfaces"></a>Recherche d'interfaces de contrat de service  

 Pour trouver les interfaces qui modèlent des contrats de service, recherchez les interfaces marquées avec l'attribut <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> . Cet attribut est souvent difficile à trouver avec une lecture rapide en raison de la présence d'autres attributs et des propriétés explicites définies sur l'attribut lui-même. N'oubliez pas que l'interface de contrat de service et l'interface de contrat client sont deux types différents. L'exemple de code suivant illustre le contrat de service d'origine.  
  
 [!code-csharp[C_GeneratedCodeFiles#22](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#22)]  
  
 L'exemple de code suivant illustre le même contrat de service, tel que généré par Svcutil.exe.  
  
 [!code-csharp[C_GeneratedCodeFiles#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#12)]  
  
 Vous pouvez utiliser l’interface de contrat de service générée avec la <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> classe pour créer un objet de canal WCF avec lequel appeler des opérations de service. Pour plus d’informations, consultez [Comment : utiliser ChannelFactory](how-to-use-the-channelfactory.md).  
  
### <a name="finding-wcf-client-classes"></a>Recherche de classes de client WCF  

 Pour rechercher la classe de client WCF qui implémente le contrat de service que vous souhaitez utiliser, recherchez une extension de <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> , où le paramètre de type est l’interface de contrat de service que vous avez localisée précédemment et qui étend cette interface. L'exemple de code suivant illustre la classe <xref:System.ServiceModel.ClientBase%601> de type `ISampleService`.  
  
 [!code-csharp[C_GeneratedCodeFiles#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#14)]  
  
 Vous pouvez utiliser cette classe de client WCF en créant une nouvelle instance de celle-ci et en appelant les méthodes qu’elle implémente. Ces méthodes appellent l'opération de service avec laquelle elle est conçue et configurée pour interagir. Pour plus d’informations, consultez [vue d’ensemble du client WCF](../wcf-client-overview.md).  
  
> [!NOTE]
> Lorsque SvcUtil.exe génère une classe de client WCF, il ajoute un <xref:System.Diagnostics.DebuggerStepThroughAttribute> à la classe de client qui empêche les débogueurs de parcourir pas à pas la classe de client WCF.  
  
### <a name="finding-data-types"></a>Recherche de types de données  

 Pour trouver des types de données dans le code généré, le mécanisme le plus simple consiste à identifier le nom de type spécifié dans un contrat et à rechercher le code pour cette déclaration de type. Par exemple, le contrat suivant spécifie que le `SampleMethod` peut retourner une erreur SOAP de type `microsoft.wcf.documentation.SampleFault`.  
  
 [!code-csharp[C_GeneratedCodeFiles#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#11)]  
  
 La recherche de `SampleFault` localise la déclaration de type suivante.  
  
 [!code-csharp[C_GeneratedCodeFiles#30](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#30)]  
  
 Dans ce cas, le type de données est le type de détail levé par une exception spécifique sur le client, un <xref:System.ServiceModel.FaultException%601> où le paramètre de type de détail est `microsoft.wcf.documentation.SampleFault`. Pour plus d’informations sur les types de données, consultez [spécification de transfert de données dans les contrats de service](specifying-data-transfer-in-service-contracts.md). Pour plus d’informations sur la gestion des exceptions dans les clients, consultez [envoi et réception d’erreurs](../sending-and-receiving-faults.md).  
  
### <a name="finding-callback-contracts-for-duplex-services"></a>Recherche de contrats de rappel pour les services duplex  

 Si vous trouvez un contrat de service pour lequel l'interface de contrat spécifie une valeur pour la propriété <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> , ce contrat spécifie un contrat duplex. Les contrats duplex requièrent que l'application cliente crée une classe de rappel qui implémente le contrat de rappel et passe une instance de cette classe au <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType> ou <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType> utilisé pour communiquer avec le service. Pour plus d’informations sur les clients duplex, consultez [Comment : accéder aux services avec un contrat duplex](how-to-access-services-with-a-duplex-contract.md).  
  
 Le contrat suivant spécifie un contrat de rappel de type `SampleDuplexHelloCallback`.  
  
 [!code-csharp[C_GeneratedCodeFiles#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#2)]
 [!code-vb[C_GeneratedCodeFiles#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#2)]  
  
 La recherche de ce contrat de rappel localise l'interface suivante que l'application cliente doit implémenter.  
  
 [!code-csharp[C_GeneratedCodeFiles#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/duplexproxycode.cs#4)]
 [!code-vb[C_GeneratedCodeFiles#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_generatedcodefiles/vb/duplexproxycode.vb#4)]  
  
### <a name="finding-service-contract-channel-interfaces"></a>Recherche d'interfaces de canal de contrat de service  

 Lorsque vous utilisez la classe <xref:System.ServiceModel.ChannelFactory> avec une interface de contrat de service, vous devez effectuer une conversion de type dans l'interface <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType> pour ouvrir, fermer ou abandonner le canal de manière explicite. Pour faciliter son utilisation, l'outil Svcutil.exe génère également une interface d'assistance qui implémente à la fois l'interface de contrat de service et <xref:System.ServiceModel.IClientChannel> afin de vous permettre d'interagir avec l'infrastructure de canal client sans devoir convertir de type. Le code suivant illustre la définition d'un canal client d'assistance qui implémente le contrat de service précédent.  
  
 [!code-csharp[C_GeneratedCodeFiles#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_generatedcodefiles/cs/proxycode.cs#13)]  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble d'un client WCF](../wcf-client-overview.md)
