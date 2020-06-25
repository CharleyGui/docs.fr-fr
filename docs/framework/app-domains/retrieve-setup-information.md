---
title: Récupération d'informations d'installation à partir d'un domaine d'application
description: Récupérez les informations d’installation d’un domaine d’application dans .NET à l’aide de la classe System. AppDomain ou de l’objet AppDomainSetup.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- AppDomainSetup object
- retrieving setup information
- application domains, retrieving setup information
ms.assetid: 5cdb12ae-1e37-4a62-8ec7-93d6dcc6e8d9
ms.openlocfilehash: 3b7fdd302ac11caa423815483a4add38264f0910
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325661"
---
# <a name="retrieve-setup-information-from-an-application-domain"></a><span data-ttu-id="054b8-103">Récupérer les informations d’installation à partir d’un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="054b8-103">Retrieve setup information from an application domain</span></span>

<span data-ttu-id="054b8-104">Chaque instance d’un domaine d’application se compose des deux propriétés et d’informations <xref:System.AppDomainSetup>.</span><span class="sxs-lookup"><span data-stu-id="054b8-104">Each instance of an application domain consists of both properties and <xref:System.AppDomainSetup> information.</span></span> <span data-ttu-id="054b8-105">Vous pouvez récupérer les informations d’installation à partir d’un domaine d’application à l’aide de la classe <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="054b8-105">You can retrieve setup information from an application domain using the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="054b8-106">Cette classe fournit plusieurs membres qui récupèrent les informations de configuration sur un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="054b8-106">This class provides several members that retrieve configuration information about an application domain.</span></span>  
  
 <span data-ttu-id="054b8-107">Vous pouvez également interroger l’objet **AppDomainSetup** pour le domaine d’application afin d’obtenir les informations d’installation passées au domaine au moment de sa création.</span><span class="sxs-lookup"><span data-stu-id="054b8-107">You can also query the **AppDomainSetup** object for the application domain to obtain setup information that was passed to the domain when it was created.</span></span>  
  
 <span data-ttu-id="054b8-108">L’exemple suivant crée un domaine d’application, puis imprime plusieurs valeurs de membre sur la console.</span><span class="sxs-lookup"><span data-stu-id="054b8-108">The following example creates a new application domain and then prints several member values to the console.</span></span>  
  
 [!code-cpp[AppDomain_Setup#2](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source2.cpp#2)]
 [!code-csharp[AppDomain_Setup#2](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source2.cs#2)]
 [!code-vb[AppDomain_Setup#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source2.vb#2)]  
  
 <span data-ttu-id="054b8-109">L’exemple suivant définit, puis récupère les informations d’installation pour un domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="054b8-109">The following example sets, and then retrieves, setup information for an application domain.</span></span> <span data-ttu-id="054b8-110">`AppDomain.SetupInformation.ApplicationBase`Obtient les informations de configuration.</span><span class="sxs-lookup"><span data-stu-id="054b8-110">`AppDomain.SetupInformation.ApplicationBase` gets the configuration information.</span></span>  
  
 [!code-cpp[AppDomain_Setup#3](../../../samples/snippets/cpp/VS_Snippets_CLR/AppDomain_Setup/CPP/source3.cpp#3)]
 [!code-csharp[AppDomain_Setup#3](../../../samples/snippets/csharp/VS_Snippets_CLR/AppDomain_Setup/CS/source3.cs#3)]
 [!code-vb[AppDomain_Setup#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AppDomain_Setup/VB/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="054b8-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="054b8-111">See also</span></span>

- [<span data-ttu-id="054b8-112">Programmation avec des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="054b8-112">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="054b8-113">Utilisation des domaines d'application</span><span class="sxs-lookup"><span data-stu-id="054b8-113">Using Application Domains</span></span>](use.md)
