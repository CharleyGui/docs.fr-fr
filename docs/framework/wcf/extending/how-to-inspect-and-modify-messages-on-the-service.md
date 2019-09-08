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
# <a name="how-to-inspect-and-modify-messages-on-the-service"></a><span data-ttu-id="3445a-102">Procédure : inspecter et modifier des messages sur le service</span><span class="sxs-lookup"><span data-stu-id="3445a-102">How to: Inspect and Modify Messages on the Service</span></span>
<span data-ttu-id="3445a-103">Vous pouvez inspecter ou modifier les messages entrants ou sortants sur un client Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> en implémentant un et en l’insérant dans le runtime du service.</span><span class="sxs-lookup"><span data-stu-id="3445a-103">You can inspect or modify the incoming or outgoing messages across a Windows Communication Foundation (WCF) client by implementing a <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> and inserting it into the service runtime.</span></span> <span data-ttu-id="3445a-104">Pour plus d’informations, consultez [extension de répartiteurs](extending-dispatchers.md).</span><span class="sxs-lookup"><span data-stu-id="3445a-104">For more information, see [Extending Dispatchers](extending-dispatchers.md).</span></span> <span data-ttu-id="3445a-105">La fonctionnalité équivalente sur le service est <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3445a-105">The equivalent feature on the service is the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-inspect-or-modify-messages"></a><span data-ttu-id="3445a-106">Pour inspecter ou modifier des messages</span><span class="sxs-lookup"><span data-stu-id="3445a-106">To inspect or modify messages</span></span>  
  
1. <span data-ttu-id="3445a-107">Implémentez l'interface <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3445a-107">Implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType> interface.</span></span>  
  
2. <span data-ttu-id="3445a-108">Implémentez une interface <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> en fonction de la portée à laquelle vous souhaitez insérer facilement l'inspecteur de message de votre service.</span><span class="sxs-lookup"><span data-stu-id="3445a-108">Implement a <xref:System.ServiceModel.Description.IServiceBehavior?displayProperty=nameWithType>, <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>, or <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType> interface depending upon the scope at which you want to easily insert your service message inspector.</span></span>  
  
3. <span data-ttu-id="3445a-109">Insérez votre comportement avant d'appeler la méthode <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> sur <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3445a-109">Insert your behavior prior to calling the <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> method on the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3445a-110">Pour plus d’informations, consultez [configuration et extension du runtime à l’aide de comportements](configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="3445a-110">For details, see [Configuring and Extending the Runtime with Behaviors](configuring-and-extending-the-runtime-with-behaviors.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3445a-111">Exemples</span><span class="sxs-lookup"><span data-stu-id="3445a-111">Example</span></span>  
 <span data-ttu-id="3445a-112">Les exemples de code suivants affichent, dans l'ordre :</span><span class="sxs-lookup"><span data-stu-id="3445a-112">The following code examples show, in order:</span></span>  
  
- <span data-ttu-id="3445a-113">L'implémentation d'un inspecteur de service.</span><span class="sxs-lookup"><span data-stu-id="3445a-113">A service inspector implementation.</span></span>  
  
- <span data-ttu-id="3445a-114">Un comportement de service qui insère l'inspecteur.</span><span class="sxs-lookup"><span data-stu-id="3445a-114">A service behavior that inserts the inspector.</span></span>  
  
- <span data-ttu-id="3445a-115">Un fichier de configuration qui charge et exécute le comportement dans une application de service.</span><span class="sxs-lookup"><span data-stu-id="3445a-115">A configuration file that loads and runs the behavior in a service application.</span></span>  
  
 [!code-csharp[Interceptors#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/interceptors.cs#7)]
 [!code-vb[Interceptors#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/interceptors.vb#7)]  
  
 [!code-csharp[Interceptors#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/insertingbehaviors.cs#8)]
 [!code-vb[Interceptors#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/interceptors/vb/insertingbehaviors.vb#8)]  
  
 [!code-xml[Interceptors#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/interceptors/cs/hostapplication.exe.config#9)]  
  
## <a name="see-also"></a><span data-ttu-id="3445a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3445a-116">See also</span></span>

- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector?displayProperty=nameWithType>
- [<span data-ttu-id="3445a-117">Configuration et extension de l’exécution à l’aide de comportements</span><span class="sxs-lookup"><span data-stu-id="3445a-117">Configuring and Extending the Runtime with Behaviors</span></span>](configuring-and-extending-the-runtime-with-behaviors.md)
