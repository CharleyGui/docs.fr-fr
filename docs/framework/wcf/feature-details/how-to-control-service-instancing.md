---
title: "Comment : contrôler l'instanciation de service"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e0b12b34-8004-443a-a46d-83a5c00f2601
ms.openlocfilehash: 8a73dd90d268c61e0df974861753119e205a870f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599072"
---
# <a name="how-to-control-service-instancing"></a><span data-ttu-id="c5ba1-102">Comment : contrôler l'instanciation de service</span><span class="sxs-lookup"><span data-stu-id="c5ba1-102">How to: Control Service Instancing</span></span>
<span data-ttu-id="c5ba1-103">La définition du mode d'instance d'un service vous permet de spécifier quand un <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (et son objet de service associé, défini par l'utilisateur) est créé.</span><span class="sxs-lookup"><span data-stu-id="c5ba1-103">Setting the instance mode of a service enables you to specify when a <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> (and its associated user-defined service object) is created.</span></span> <span data-ttu-id="c5ba1-104">Consultez l'énumération <xref:System.ServiceModel.InstanceContextMode> pour obtenir les modes possibles.</span><span class="sxs-lookup"><span data-stu-id="c5ba1-104">See the <xref:System.ServiceModel.InstanceContextMode> enumeration for the possible modes.</span></span> <span data-ttu-id="c5ba1-105">Pour plus d’informations sur les comportements, consultez [configuration et extension du runtime à l’aide de comportements](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="c5ba1-105">For more information about behaviors, see [Configuring and Extending the Runtime with Behaviors](../extending/configuring-and-extending-the-runtime-with-behaviors.md).</span></span> <span data-ttu-id="c5ba1-106">Pour obtenir des exemples fonctionnels, consultez [comportements](../samples/behaviors.md).</span><span class="sxs-lookup"><span data-stu-id="c5ba1-106">For working examples, see [Behaviors](../samples/behaviors.md).</span></span>  
  
### <a name="to-control-the-service-instance-lifetime-using-code"></a><span data-ttu-id="c5ba1-107">Pour contrôler la durée de vie de l'instance de service en utilisant du code</span><span class="sxs-lookup"><span data-stu-id="c5ba1-107">To control the service instance lifetime using code</span></span>  
  
1. <span data-ttu-id="c5ba1-108">Appliquez <xref:System.ServiceModel.ServiceBehaviorAttribute> à la classe de service.</span><span class="sxs-lookup"><span data-stu-id="c5ba1-108">Apply the <xref:System.ServiceModel.ServiceBehaviorAttribute> to the service class.</span></span>  
  
2. <span data-ttu-id="c5ba1-109">Affectez à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> l'une des valeurs suivantes : <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession> ou <xref:System.ServiceModel.InstanceContextMode.Single>.</span><span class="sxs-lookup"><span data-stu-id="c5ba1-109">Set the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property to one of the following values: <xref:System.ServiceModel.InstanceContextMode.PerCall>, <xref:System.ServiceModel.InstanceContextMode.PerSession>, or <xref:System.ServiceModel.InstanceContextMode.Single>.</span></span>  
  
     [!code-csharp[C_ControlServiceInstancing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#1)]
     [!code-vb[C_ControlServiceInstancing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="c5ba1-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="c5ba1-110">Example</span></span>  
 <span data-ttu-id="c5ba1-111">L'exemple de code suivant affecte à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> de l'attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> la valeur <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span><span class="sxs-lookup"><span data-stu-id="c5ba1-111">The following code example sets the <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> property of the <xref:System.ServiceModel.ServiceBehaviorAttribute> attribute to <xref:System.ServiceModel.InstanceContextMode.PerCall>.</span></span>  
  
 [!code-csharp[c_ControlServiceInstancing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_controlserviceinstancing/cs/source.cs#2)]
 [!code-vb[c_ControlServiceInstancing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_controlserviceinstancing/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="c5ba1-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5ba1-112">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A>
- <xref:System.ServiceModel.InstanceContextMode>
- [<span data-ttu-id="c5ba1-113">Service : exemples de comportements</span><span class="sxs-lookup"><span data-stu-id="c5ba1-113">Service: Behaviors Samples</span></span>](../samples/behaviors.md)
