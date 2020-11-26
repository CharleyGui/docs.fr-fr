---
title: 'Procédure : inspecter ou modifier des paramètres'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ab6c0ac7-aac4-45ba-93d6-a0e9afd1756f
ms.openlocfilehash: e8b2674d8efc0ef3ac2f1dd6ab0df559195c274c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96249031"
---
# <a name="how-to-inspect-or-modify-parameters"></a><span data-ttu-id="09fcc-102">Procédure : inspecter ou modifier des paramètres</span><span class="sxs-lookup"><span data-stu-id="09fcc-102">How to: Inspect or Modify Parameters</span></span>

<span data-ttu-id="09fcc-103">Vous pouvez inspecter ou modifier les messages entrants ou sortants pour une seule opération sur un objet client Windows Communication Foundation (WCF) ou un service WCF en implémentant l' <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface et en l’insérant dans le service d’exécution du client ou du service.</span><span class="sxs-lookup"><span data-stu-id="09fcc-103">You can inspect or modify the incoming or outgoing messages for a single operation on a Windows Communication Foundation (WCF) client object or a WCF service by implementing the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface and inserting it into the client or service runtime.</span></span> <span data-ttu-id="09fcc-104">En général, un comportement d'opération est utilisé pour ajouter des inspecteurs de paramètre pour une seule opération ; d'autres comportements peuvent être utilisés pour fournir un accès aisé à l'exécution à une échelle plus grande.</span><span class="sxs-lookup"><span data-stu-id="09fcc-104">Typically an operation behavior is used to add parameter inspectors for a single operation; other behaviors can be used to provide easy access to the runtime at a greater scope.</span></span> <span data-ttu-id="09fcc-105">Pour plus d’informations, consultez [extension de clients](extending-clients.md) et extension de [répartiteurs](extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="09fcc-105">For more information, see [Extending Clients](extending-clients.md) and [Extending Dispatchers](extending-dispatchers.md).</span></span>  
  
### <a name="inspecting-or-modifying-parameters"></a><span data-ttu-id="09fcc-106">Inspection ou modification de paramètres</span><span class="sxs-lookup"><span data-stu-id="09fcc-106">Inspecting or Modifying Parameters</span></span>  
  
1. <span data-ttu-id="09fcc-107">Implémentez l'interface <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09fcc-107">Implement the <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="09fcc-108">Implémentez un <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (en fonction de la portée requise) pour ajouter votre inspecteur de paramètre aux propriétés <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09fcc-108">Implement a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType> or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> (depending upon the required scope) to add your parameter inspector to either the <xref:System.ServiceModel.Dispatcher.ClientOperation.ParameterInspectors%2A?displayProperty=nameWithType> or <xref:System.ServiceModel.Dispatcher.DispatchOperation.ParameterInspectors%2A?displayProperty=nameWithType> properties.</span></span>  
  
3. <span data-ttu-id="09fcc-109">Insérez votre comportement avant d'appeler <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> ou la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="09fcc-109">Insert your behavior prior to calling <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType> or the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="09fcc-110">Pour plus d’informations, consultez [configuration et extension du runtime à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="09fcc-110">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="09fcc-111"> Exemple</span><span class="sxs-lookup"><span data-stu-id="09fcc-111">Example</span></span>  

 <span data-ttu-id="09fcc-112">Les exemples de code suivants affichent, dans l'ordre :</span><span class="sxs-lookup"><span data-stu-id="09fcc-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="09fcc-113">Une implémentation de l'inspecteur de paramètre</span><span class="sxs-lookup"><span data-stu-id="09fcc-113">A parameter inspector implementation.</span></span>  
  
- <span data-ttu-id="09fcc-114">L'implémentation de comportement qui insère l'inspecteur de paramètre à l'aide de <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> et <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="09fcc-114">The behavior implementation that inserts the parameter inspector using a <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, and an <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="09fcc-115">Un fichier de configuration qui charge et exécute le comportement de point de terminaison dans une application cliente pour insérer l'inspecteur de paramètre sur le client</span><span class="sxs-lookup"><span data-stu-id="09fcc-115">A configuration file that loads and runs the endpoint behavior in a client application to insert the parameter inspector on the client.</span></span>  
  
 [!code-csharp[Interceptors#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#4)]
 [!code-vb[Interceptors#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#4)]  
  
 [!code-csharp[Interceptors#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#5)]
 [!code-vb[Interceptors#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#5)]  
  
 [!code-xml[Interceptors#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/client.exe.config#3)]  
  
## <a name="see-also"></a><span data-ttu-id="09fcc-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09fcc-116">See also</span></span>

- [<span data-ttu-id="09fcc-117">Configuration et extension de l'exécution à l'aide de comportements</span><span class="sxs-lookup"><span data-stu-id="09fcc-117">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
