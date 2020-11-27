---
title: 'Procédure : utiliser ChannelFactory'
description: Découvrez comment créer une fabrique de canaux pour créer plusieurs canaux pour accéder aux services à l’aide d’un client WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: dd767443fefb16ebc02300bffa4264357f12c3ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280583"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="9ab2e-103">Procédure : utiliser ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="9ab2e-103">How to: Use the ChannelFactory</span></span>

<span data-ttu-id="9ab2e-104">La classe <xref:System.ServiceModel.ChannelFactory%601> générique est utilisée dans les scénarios avancés qui requièrent la création d'une fabrication de canal pouvant être utilisée pour créer plusieurs canaux.</span><span class="sxs-lookup"><span data-stu-id="9ab2e-104">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="9ab2e-105">Pour créer et utiliser la classe ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="9ab2e-105">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="9ab2e-106">Générez et exécutez un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9ab2e-106">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="9ab2e-107">Pour plus d’informations, consultez [conception et implémentation de services](../designing-and-implementing-services.md), [configuration de services](../configuring-services.md)et Hébergement de [services](../hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="9ab2e-107">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md), [Configuring Services](../configuring-services.md), and [Hosting Services](../hosting-services.md).</span></span>  
  
2. <span data-ttu-id="9ab2e-108">Utilisez l' [outil ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour générer le contrat (interface) du client.</span><span class="sxs-lookup"><span data-stu-id="9ab2e-108">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="9ab2e-109">Dans le code client, utilisez la classe <xref:System.ServiceModel.ChannelFactory%601> pour créer plusieurs écouteurs de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="9ab2e-109">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ab2e-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="9ab2e-110">Example</span></span>  

 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
