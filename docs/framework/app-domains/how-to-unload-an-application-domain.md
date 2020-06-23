---
title: 'Procédure : décharger un domaine d’application'
description: Lisez comment décharger un domaine d’application dans .NET, à l’aide de la méthode AppDomain. Unload pour arrêter correctement le domaine d’application spécifié.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
ms.openlocfilehash: b64a9553f63aa4a8deb57f23a97fa464edd64fee
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104678"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="7f73f-103">Procédure : décharger un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="7f73f-103">How to: Unload an Application Domain</span></span>
<span data-ttu-id="7f73f-104">Quand vous avez fini d’utiliser un domaine d’application, déchargez-le à l’aide de la méthode <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f73f-104">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7f73f-105">La méthode **Unload** arrête de façon correcte le domaine d’application spécifié.</span><span class="sxs-lookup"><span data-stu-id="7f73f-105">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="7f73f-106">Au cours du processus de déchargement, aucun nouveau thread ne peut accéder au domaine d’application, et toutes les structures de données spécifiques au domaine d’application sont libérées.</span><span class="sxs-lookup"><span data-stu-id="7f73f-106">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="7f73f-107">Les assemblys chargés dans le domaine d’application sont supprimés et ne sont plus disponibles.</span><span class="sxs-lookup"><span data-stu-id="7f73f-107">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="7f73f-108">Si un assembly dans le domaine d’application est indépendant du domaine, les données de l’assembly restent en mémoire jusqu’à ce que l’ensemble du processus soit arrêté.</span><span class="sxs-lookup"><span data-stu-id="7f73f-108">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="7f73f-109">Pour décharger un assembly indépendant du domaine, il n’existe pas d’autre mécanisme que l’arrêt de l’ensemble du processus.</span><span class="sxs-lookup"><span data-stu-id="7f73f-109">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="7f73f-110">Il existe des cas où la demande de déchargement d’un domaine d’application ne fonctionne pas et provoque une exception <xref:System.CannotUnloadAppDomainException>.</span><span class="sxs-lookup"><span data-stu-id="7f73f-110">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="7f73f-111">L’exemple suivant crée un nouveau domaine d’application appelé `MyDomain`, imprime certaines informations dans la console, puis décharge le domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="7f73f-111">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="7f73f-112">Remarquez que le code tente ensuite d’imprimer le nom convivial du domaine d’application déchargé dans la console.</span><span class="sxs-lookup"><span data-stu-id="7f73f-112">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="7f73f-113">Cette action génère une exception qui est gérée par les instructions try/catch à la fin du programme.</span><span class="sxs-lookup"><span data-stu-id="7f73f-113">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f73f-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="7f73f-114">Example</span></span>  
 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="7f73f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f73f-115">See also</span></span>

- [<span data-ttu-id="7f73f-116">Programmation avec des domaines d’application</span><span class="sxs-lookup"><span data-stu-id="7f73f-116">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="7f73f-117">Procédure : créer un domaine d’application</span><span class="sxs-lookup"><span data-stu-id="7f73f-117">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)
- [<span data-ttu-id="7f73f-118">Utilisation des domaines d'application</span><span class="sxs-lookup"><span data-stu-id="7f73f-118">Using Application Domains</span></span>](use.md)
