---
title: 'Procédure : inspecter ou modifier des paramètres'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: b4a673f97f06e8d489d9acc85d84e1ecea4656e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795585"
---
# <a name="how-to-inspect-or-modify-parameters"></a>Procédure : inspecter ou modifier des paramètres
Vous pouvez inspecter ou modifier les messages entrants ou sortants pour une seule opération sur un objet client Windows Communication Foundation (WCF) ou un service WCF <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> en implémentant l’interface et en l’insérant dans le service d’exécution du client ou du service. En général, un comportement d'opération est utilisé pour ajouter des inspecteurs de paramètre pour une seule opération ; d'autres comportements peuvent être utilisés pour fournir un accès aisé à l'exécution à une échelle plus grande. Pour plus d’informations, consultez [extension de clients](extending-clients.md) et extension de [répartiteurs](extending-dispatchers.md).  
  
### <a name="inspecting-or-modifying-parameters"></a>Inspection ou modification de paramètres  
  
1. Implémentez l'interface <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>.  
  
2. Implémentez un <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (en fonction de la portée requise) pour ajouter votre inspecteur de paramètre aux propriétés <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType>.  
  
3. Insérez votre comportement avant d'appeler <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> ou la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>. Pour plus d’informations, consultez [configuration et extension du runtime à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="example"></a>Exemples  
 Les exemples de code suivants affichent, dans l'ordre :  
  
- Une implémentation de l'inspecteur de paramètre  
  
- L'implémentation de comportement qui insère l'inspecteur de paramètre à l'aide de <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> et <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>  
  
- Un fichier de configuration qui charge et exécute le comportement de point de terminaison dans une application cliente pour insérer l'inspecteur de paramètre sur le client  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Configuration et extension de l’exécution à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md)
