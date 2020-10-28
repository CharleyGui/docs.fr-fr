---
title: Assemblys et exécution côte à côte
description: En savoir plus sur l’exécution côte à côte, qui est la possibilité de stocker et d’exécuter plusieurs versions d’une application ou d’un composant sur le même ordinateur.
ms.date: 08/20/2019
helpviewer_keywords:
- side-by-side execution [.NET]
- assemblies [.NET], side-by-side execution
ms.assetid: e42036ee-7590-47d1-b884-cc856e39bd5d
ms.openlocfilehash: 7bedd5a384ceace014412eb894adad5c92c00b05
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687984"
---
# <a name="assemblies-and-side-by-side-execution"></a><span data-ttu-id="4c5b6-103">Assemblys et exécution côte à côte</span><span class="sxs-lookup"><span data-stu-id="4c5b6-103">Assemblies and side-by-side execution</span></span>

<span data-ttu-id="4c5b6-104">L'exécution côte à côte consiste à stocker et exécuter plusieurs versions d'une application ou d'un composant sur un même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-104">Side-by-side execution is the ability to store and execute multiple versions of an application or component on the same computer.</span></span> <span data-ttu-id="4c5b6-105">Cela signifie que peuvent coexister simultanément sur un même ordinateur plusieurs versions du runtime ainsi que plusieurs versions d'applications et de composants utilisant une version du runtime.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-105">This means that you can have multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, on the same computer at the same time.</span></span> <span data-ttu-id="4c5b6-106">L'exécution côte à côte vous offre un meilleur contrôle des versions auxquelles peut être liée une application ainsi que de la version du runtime utilisée par une application.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-106">Side-by-side execution gives you more control over what versions of a component an application binds to, and more control over what version of the runtime an application uses.</span></span>  
  
<span data-ttu-id="4c5b6-107">La prise en charge du stockage et de l'exécution côte à côte de différentes versions du même assembly fait partie intégrante de l'attribution des noms forts et se trouve intégrée à l'infrastructure du runtime.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-107">Support for side-by-side storage and execution of different versions of the same assembly is an integral part of strong naming and is built into the infrastructure of the runtime.</span></span> <span data-ttu-id="4c5b6-108">Comme le numéro de version de l'assembly avec nom fort fait partie de son identité, le runtime peut stocker plusieurs versions du même assembly dans le Global Assembly Cache et charger ces assemblys au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-108">Because the strong-named assembly's version number is part of its identity, the runtime can store multiple versions of the same assembly in the global assembly cache and load those assemblies at run time.</span></span>  
  
<span data-ttu-id="4c5b6-109">Bien que le runtime vous permette de créer des applications côte à côte, l'exécution côte à côte n'est pas automatique.</span><span class="sxs-lookup"><span data-stu-id="4c5b6-109">Although the runtime provides you with the ability to create side-by-side applications, side-by-side execution is not automatic.</span></span> <span data-ttu-id="4c5b6-110">Pour plus d’informations sur la création d’applications pour l’exécution côte à côte, consultez [instructions pour la création de composants pour l’exécution côte à côte](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span><span class="sxs-lookup"><span data-stu-id="4c5b6-110">For more information on creating applications for side-by-side execution, see [Guidelines for creating components for side-by-side execution](../../framework/deployment/guidelines-for-creating-components-for-side-by-side-execution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c5b6-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c5b6-111">See also</span></span>

- [<span data-ttu-id="4c5b6-112">Comment le runtime localise les assemblys</span><span class="sxs-lookup"><span data-stu-id="4c5b6-112">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="4c5b6-113">Assemblys dans .NET</span><span class="sxs-lookup"><span data-stu-id="4c5b6-113">Assemblies in .NET</span></span>](index.md)
