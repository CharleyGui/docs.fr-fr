---
title: 'Procédure : inspecter et modifier des messages sur le service'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9c5b1cc7-84f3-45f8-9226-d59c278e8c42
ms.openlocfilehash: 1356983361c483170d9d7365932b788f2421bf09
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795602"
---
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a>Procédure : inspecter et modifier des messages sur le service
Vous pouvez inspecter ou modifier les messages entrants ou sortants sur un client Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> en implémentant un et en l’insérant dans le runtime du service. Pour plus d’informations, consultez [extension de répartiteurs](extending-dispatchers.md). La fonctionnalité équivalente sur le service est <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.  
  
### <a name="to-inspect-or-modify-messages"></a>Pour inspecter ou modifier des messages  
  
1. Implémentez l'interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.  
  
2. Implémentez une interface <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> en fonction de la portée à laquelle vous souhaitez insérer facilement l'inspecteur de message de votre service.  
  
3. Insérez votre comportement avant d'appeler la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>. Pour plus d’informations, consultez [configuration et extension du runtime à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Exemples  
 Les exemples de code suivants affichent, dans l'ordre :  
  
- L'implémentation d'un inspecteur de service.  
  
- Un comportement de service qui insère l'inspecteur.  
  
- Un fichier de configuration qui charge et exécute le comportement dans une application de service.  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [Configuration et extension de l’exécution à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md)
