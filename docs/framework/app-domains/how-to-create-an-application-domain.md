---
title: 'Procédure : créer un domaine d’application'
description: Consultez Comment créer un domaine d’application dans .NET. Vous pouvez créer un domaine d’application pour charger des assemblys pour gérer personnellement ou en créer un pour exécuter du code.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- application domains, creating
ms.assetid: ba1fa43e-49f5-47d9-bd7f-3024af16f4ba
ms.openlocfilehash: 8e44e682f64854dbc0181b26f6ed3fa2905b7814
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104805"
---
# <a name="how-to-create-an-application-domain"></a><span data-ttu-id="ca1ca-104">Procédure : créer un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="ca1ca-104">How to: Create an Application Domain</span></span>
<span data-ttu-id="ca1ca-105">Un hôte Common Language Runtime crée automatiquement des domaines d’application quand ils sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="ca1ca-105">A common language runtime host creates application domains automatically when they are needed.</span></span> <span data-ttu-id="ca1ca-106">Toutefois, vous pouvez créer vos propres domaines d’application et y charger les assemblys que vous souhaitez gérer personnellement.</span><span class="sxs-lookup"><span data-stu-id="ca1ca-106">However, you can create your own application domains and load into them those assemblies that you want to manage personally.</span></span> <span data-ttu-id="ca1ca-107">Vous pouvez également créer des domaines d’application à partir desquels vous exécutez du code.</span><span class="sxs-lookup"><span data-stu-id="ca1ca-107">You can also create application domains from which you execute code.</span></span>  
  
 <span data-ttu-id="ca1ca-108">Vous pouvez créer un domaine d’application à l’aide de l’une des méthodes **CreateDomain** surchargées dans la classe <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca1ca-108">You create a new application domain using one of the overloaded **CreateDomain** methods in the <xref:System.AppDomain?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="ca1ca-109">Vous pouvez nommer le domaine d’application et le référencer par ce nom.</span><span class="sxs-lookup"><span data-stu-id="ca1ca-109">You can give the application domain a name and reference it by that name.</span></span>  
  
 <span data-ttu-id="ca1ca-110">L’exemple suivant crée un domaine d’application et lui attribue le nom `MyDomain`, puis imprime le nom du domaine hôte et du domaine d’application enfant créé dans la console.</span><span class="sxs-lookup"><span data-stu-id="ca1ca-110">The following example creates a new application domain, assigns it the name `MyDomain`, and then prints the name of the host domain and the newly created child application domain to the console.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca1ca-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="ca1ca-111">Example</span></span>  
 [!code-cpp[ADCreateDomain#2](../../../samples/snippets/cpp/VS_Snippets_CLR/ADCreateDomain/CPP/source2.cpp#2)]
 [!code-csharp[ADCreateDomain#2](../../../samples/snippets/csharp/VS_Snippets_CLR/ADCreateDomain/CS/source2.cs#2)]
 [!code-vb[ADCreateDomain#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/ADCreateDomain/VB/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ca1ca-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca1ca-112">See also</span></span>

- [<span data-ttu-id="ca1ca-113">Programmation avec des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="ca1ca-113">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="ca1ca-114">Utilisation des domaines d'application</span><span class="sxs-lookup"><span data-stu-id="ca1ca-114">Using Application Domains</span></span>](use.md)
