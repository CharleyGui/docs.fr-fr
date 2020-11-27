---
title: Extensibilité des liaisons
ms.date: 03/30/2017
ms.assetid: cabdd583-ddf5-493e-9dba-c6c31cde8f65
ms.openlocfilehash: c99713416181aed8a8800c819e0f5786411187ab
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283599"
---
# <a name="binding-extensibility"></a><span data-ttu-id="9d6c8-102">Extensibilité des liaisons</span><span class="sxs-lookup"><span data-stu-id="9d6c8-102">Binding Extensibility</span></span>

<span data-ttu-id="9d6c8-103">Cette section contient des exemples qui illustrent la liaison personnalisée dans Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9d6c8-103">This section contains samples that demonstrate custom binding in Windows Communication Foundation (WCF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d6c8-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9d6c8-104">In This Section</span></span>  

 <xref:System.ServiceModel.NetHttpBinding>  
 <span data-ttu-id="9d6c8-105">Montre comment implémenter une liaison qui empile <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ou le <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> au-dessus du <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="9d6c8-105">Demonstrates how to implement a binding that stacks <xref:System.ServiceModel.Channels.HttpTransportBindingElement> or the <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> on top of the <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.</span></span>  
  
 [<span data-ttu-id="9d6c8-106">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9d6c8-106">WSStreamedHttpBinding</span></span>](wsstreamedhttpbinding.md)  
 <span data-ttu-id="9d6c8-107">Montre comment créer une liaison conçue pour prendre en charge des scénarios de diffusion en continu lorsque le transport HTTP est utilisé.</span><span class="sxs-lookup"><span data-stu-id="9d6c8-107">Demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>  
