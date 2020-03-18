---
title: Assemblys et exécution côte à côte
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET Framework]
- assemblies [.NET Framework], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 234efba66d87b520b54d6d113afcc4bba0bfe06a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138663"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="1aadc-102">Assemblys et exécution côte à côte</span><span class="sxs-lookup"><span data-stu-id="1aadc-102">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="1aadc-103">L'exécution côte à côte consiste à stocker et exécuter plusieurs versions d'une application ou d'un composant sur un même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="1aadc-103">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="1aadc-104">Cela signifie que peuvent coexister simultanément sur un même ordinateur plusieurs versions du runtime ainsi que plusieurs versions d'applications et de composants utilisant une version du runtime.</span><span class="sxs-lookup"><span data-stu-id="1aadc-104">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="1aadc-105">L'exécution côte à côte vous offre un meilleur contrôle des versions auxquelles peut être liée une application ainsi que de la version du runtime utilisée par une application.</span><span class="sxs-lookup"><span data-stu-id="1aadc-105">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="1aadc-106">La prise en charge du stockage et de l'exécution côte à côte de différentes versions du même assembly fait partie intégrante de l'attribution des noms forts et se trouve intégrée à l'infrastructure du runtime.</span><span class="sxs-lookup"><span data-stu-id="1aadc-106">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="1aadc-107">Comme le numéro de version de l'assembly avec nom fort fait partie de son identité, le runtime peut stocker plusieurs versions du même assembly dans le Global Assembly Cache et charger ces assemblys au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="1aadc-107">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="1aadc-108">Bien que le runtime vous permette de créer des applications côte à côte, l'exécution côte à côte n'est pas automatique.</span><span class="sxs-lookup"><span data-stu-id="1aadc-108">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="1aadc-109">Pour plus d’informations sur la création d’applications d’exécution côte à côte, voir [Lignes directrices pour la création de composants pour l’exécution côte à côte](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="1aadc-109">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aadc-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1aadc-110">See also</span></span>

- [<span data-ttu-id="1aadc-111">Comment le temps d’exécution localise les assemblages</span><span class="sxs-lookup"><span data-stu-id="1aadc-111">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="1aadc-112">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="1aadc-112">Assemblies in .NET</span></span>](index.md)
