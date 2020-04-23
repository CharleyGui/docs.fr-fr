---
title: Identification des fonctions des DLL
ms.date: 03/30/2017
helpviewer_keywords:
- platform invoke, identifying functions
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- identifying DLL functions
- DLL functions
ms.assetid: 3e3f6780-6d90-4413-bad7-ba641220364d
ms.openlocfilehash: 1a94bb2020b07ba8405d901f46ec4a0687e79700
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121977"
---
# <a name="identifying-functions-in-dlls"></a><span data-ttu-id="65b5e-102">Identification des fonctions des DLL</span><span class="sxs-lookup"><span data-stu-id="65b5e-102">Identifying Functions in DLLs</span></span>
<span data-ttu-id="65b5e-103">L’identité d’une fonction DLL est composée des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="65b5e-103">The identity of a DLL function consists of the following elements:</span></span>  
  
- <span data-ttu-id="65b5e-104">ordinal ou nom de la fonction ;</span><span class="sxs-lookup"><span data-stu-id="65b5e-104">Function name or ordinal</span></span>  
  
- <span data-ttu-id="65b5e-105">nom du fichier DLL dans lequel l’implémentation figure.</span><span class="sxs-lookup"><span data-stu-id="65b5e-105">Name of the DLL file in which the implementation can be found</span></span>  
  
 <span data-ttu-id="65b5e-106">Par exemple, la spécification de la fonction **MessageBox** dans User32.dll identifie la fonction (**MessageBox**) et son emplacement (User32.dll, User32 ou user32).</span><span class="sxs-lookup"><span data-stu-id="65b5e-106">For example, specifying the **MessageBox** function in the User32.dll identifies the function (**MessageBox**) and its location (User32.dll, User32, or user32).</span></span> <span data-ttu-id="65b5e-107">L’interface de programmation d’applications Microsoft Windows (API Windows) peut comporter deux versions de chaque fonction qui gère les caractères et les chaînes : une version ANSI pour les caractères à 1 octet et une version Unicode pour les caractères à 2 octets.</span><span class="sxs-lookup"><span data-stu-id="65b5e-107">The Microsoft Windows application programming interface (Windows API) can contain two versions of each function that handles characters and strings: a 1-byte character ANSI version and a 2-byte character Unicode version.</span></span> <span data-ttu-id="65b5e-108">Quand le jeu de caractères représenté par le champ <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> n’est pas spécifié, sa valeur par défaut est ANSI.</span><span class="sxs-lookup"><span data-stu-id="65b5e-108">When unspecified, the character set, represented by the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> field, defaults to ANSI.</span></span> <span data-ttu-id="65b5e-109">Certaines fonctions peuvent posséder plus de deux versions.</span><span class="sxs-lookup"><span data-stu-id="65b5e-109">Some functions can have more than two versions.</span></span>  
  
 <span data-ttu-id="65b5e-110">**MessageBoxA** est le point d’entrée ANSI de la fonction **MessageBox** ; **MessageBoxW** correspond à la version Unicode.</span><span class="sxs-lookup"><span data-stu-id="65b5e-110">**MessageBoxA** is the ANSI entry point for the **MessageBox** function; **MessageBoxW** is the Unicode version.</span></span> <span data-ttu-id="65b5e-111">Vous pouvez obtenir une liste de noms de fonctions pour une DLL spécifique, telle que user32.dll, en exécutant une variété d’outils en ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="65b5e-111">You can list function names for a specific DLL, such as user32.dll, by running a variety of command-line tools.</span></span> <span data-ttu-id="65b5e-112">Par exemple, vous pouvez utiliser `dumpbin /exports user32.dll` ou `link /dump /exports user32.dll` pour obtenir des noms de fonctions.</span><span class="sxs-lookup"><span data-stu-id="65b5e-112">For example, you can use `dumpbin /exports user32.dll` or `link /dump /exports user32.dll` to obtain function names.</span></span>  
  
 <span data-ttu-id="65b5e-113">Vous pouvez renommer une fonction non managée à votre convenance dans votre code à partir du moment où vous mappez le nouveau nom au point d’entrée d’origine dans la DLL.</span><span class="sxs-lookup"><span data-stu-id="65b5e-113">You can rename an unmanaged function to whatever you like within your code as long as you map the new name to the original entry point in the DLL.</span></span> <span data-ttu-id="65b5e-114">Pour obtenir des instructions sur l’attribution d’un nouveau nom à une fonction DLL non managée dans du code source managé, consultez [Spécification d’un point d’entrée](specifying-an-entry-point.md).</span><span class="sxs-lookup"><span data-stu-id="65b5e-114">For instructions on renaming an unmanaged DLL function in managed source code, see the [Specifying an Entry Point](specifying-an-entry-point.md).</span></span>  
  
 <span data-ttu-id="65b5e-115">L’appel de code non managé vous permet de contrôler une partie importante du système d’exploitation en appelant des fonctions dans l’interface API Windows et dans d’autres DLL.</span><span class="sxs-lookup"><span data-stu-id="65b5e-115">Platform invoke enables you to control a significant portion of the operating system by calling functions in the Windows API and other DLLs.</span></span> <span data-ttu-id="65b5e-116">Outre l’interface API Windows, de nombreuses autres interfaces API et DLL sont à votre disposition via l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="65b5e-116">In addition to the Windows API, there are numerous other APIs and DLLs available to you through platform invoke.</span></span>  
  
 <span data-ttu-id="65b5e-117">Le tableau suivant décrit plusieurs DLL fréquemment utilisées dans l’interface API Windows.</span><span class="sxs-lookup"><span data-stu-id="65b5e-117">The following table describes several commonly used DLLs in the Windows API.</span></span>  
  
|<span data-ttu-id="65b5e-118">DLL</span><span class="sxs-lookup"><span data-stu-id="65b5e-118">DLL</span></span>|<span data-ttu-id="65b5e-119">Description du contenu</span><span class="sxs-lookup"><span data-stu-id="65b5e-119">Description of Contents</span></span>|  
|---------|-----------------------------|  
|<span data-ttu-id="65b5e-120">GDI32.dll</span><span class="sxs-lookup"><span data-stu-id="65b5e-120">GDI32.dll</span></span>|<span data-ttu-id="65b5e-121">Fonctions GDI (Graphics Device Interface) pour la sortie d’appareils, telles que celles pour la gestion du dessin et des polices.</span><span class="sxs-lookup"><span data-stu-id="65b5e-121">Graphics Device Interface (GDI) functions for device output, such as those for drawing and font management.</span></span>|  
|<span data-ttu-id="65b5e-122">Kernel32.dll</span><span class="sxs-lookup"><span data-stu-id="65b5e-122">Kernel32.dll</span></span>|<span data-ttu-id="65b5e-123">Fonctions du système d’exploitation de bas niveau pour la gestion de la mémoire et des ressources.</span><span class="sxs-lookup"><span data-stu-id="65b5e-123">Low-level operating system functions for memory management and resource handling.</span></span>|  
|<span data-ttu-id="65b5e-124">User32.dll</span><span class="sxs-lookup"><span data-stu-id="65b5e-124">User32.dll</span></span>|<span data-ttu-id="65b5e-125">Fonctions de gestion Windows pour les messages, les minuteries, les menus et les communications.</span><span class="sxs-lookup"><span data-stu-id="65b5e-125">Windows management functions for message handling, timers, menus, and communications.</span></span>|  
  
 <span data-ttu-id="65b5e-126">Pour obtenir une documentation complète sur l’interface API Windows, consultez le Kit Platform SDK.</span><span class="sxs-lookup"><span data-stu-id="65b5e-126">For complete documentation on the Windows API, see the Platform SDK.</span></span> <span data-ttu-id="65b5e-127">Pour afficher des exemples montrant comment construire des déclarations .NET à utiliser avec l’appel de code non managé, consultez [Marshaling de données à l’aide de l’appel de code non managé](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="65b5e-127">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b5e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65b5e-128">See also</span></span>

- [<span data-ttu-id="65b5e-129">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="65b5e-129">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="65b5e-130">Spécification d’un point d’entrée</span><span class="sxs-lookup"><span data-stu-id="65b5e-130">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="65b5e-131">Création d’une classe pour contenir des fonctions DLL</span><span class="sxs-lookup"><span data-stu-id="65b5e-131">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="65b5e-132">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="65b5e-132">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="65b5e-133">Appel à une fonction DLL</span><span class="sxs-lookup"><span data-stu-id="65b5e-133">Calling a DLL Function</span></span>](calling-a-dll-function.md)
