---
title: Création d'une classe pour contenir des fonctions DLL
description: Créez un wrapper de classe managé dans .NET pour contenir des fonctions DLL, ce qui permet d’encapsuler les fonctionnalités de la plateforme.
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
ms.openlocfilehash: b8aa0361ee5213cb947a102f903d1a7a35331f17
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622170"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="6f9be-103">Création d'une classe pour contenir des fonctions DLL</span><span class="sxs-lookup"><span data-stu-id="6f9be-103">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="6f9be-104">L’enveloppement d’une fonction DLL fréquemment utilisée dans une classe managée est une stratégie efficace d’encapsulation des fonctionnalités de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="6f9be-104">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="6f9be-105">Bien que cette opération ne soit pas obligatoire dans tous les cas, un wrapper de classe s’avère pratique, car la définition de fonctions DLL peut être fastidieuse et sujette à erreurs.</span><span class="sxs-lookup"><span data-stu-id="6f9be-105">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="6f9be-106">En cas de programmation en Visual Basic ou C#, vous devez déclarer les fonctions DLL dans une classe ou un module Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6f9be-106">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="6f9be-107">Dans une classe, vous définissez une méthode statique pour chaque fonction DLL que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="6f9be-107">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="6f9be-108">La définition peut inclure des informations supplémentaires, telles que le jeu de caractères ou la convention d’appel qui sont utilisés lors du passage des arguments des méthodes. Si vous ne renseignez pas ces informations, les paramètres par défaut sont alors sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="6f9be-108">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="6f9be-109">Pour obtenir une liste complète des options de déclaration et de leurs paramètres par défaut, consultez [Création de prototypes dans du code managé](creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="6f9be-109">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="6f9be-110">Une fois les méthodes incluses dans un wrapper, vous pouvez les appeler sur la classe de la même manière que vous appelez des méthodes statiques sur toute autre classe.</span><span class="sxs-lookup"><span data-stu-id="6f9be-110">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="6f9be-111">L’appel de code non managé gère automatiquement la fonction exportée sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="6f9be-111">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="6f9be-112">Lors de la conception d’une classe managée pour l’appel de code non managé, tenez compte des relations entre les classes et les fonctions DLL.</span><span class="sxs-lookup"><span data-stu-id="6f9be-112">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="6f9be-113">Par exemple, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="6f9be-113">For example, you can:</span></span>  
  
- <span data-ttu-id="6f9be-114">déclarer des fonctions DLL dans une classe existante ;</span><span class="sxs-lookup"><span data-stu-id="6f9be-114">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="6f9be-115">créer une classe individuelle pour chaque fonction DLL, en maintenant les fonctions isolées et facilement localisables ;</span><span class="sxs-lookup"><span data-stu-id="6f9be-115">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="6f9be-116">créer une classe pour un ensemble de fonctions DLL associées afin de former des regroupements logiques et réduire la charge mémoire.</span><span class="sxs-lookup"><span data-stu-id="6f9be-116">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="6f9be-117">Vous pouvez nommer la classe et ses méthodes à votre convenance.</span><span class="sxs-lookup"><span data-stu-id="6f9be-117">You can name the class and its methods as you please.</span></span> <span data-ttu-id="6f9be-118">Pour afficher des exemples montrant comment construire des déclarations .NET à utiliser avec l’appel de code non managé, consultez [Marshaling de données à l’aide de l’appel de code non managé](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="6f9be-118">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f9be-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f9be-119">See also</span></span>

- [<span data-ttu-id="6f9be-120">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="6f9be-120">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="6f9be-121">Identification des fonctions des DLL</span><span class="sxs-lookup"><span data-stu-id="6f9be-121">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="6f9be-122">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="6f9be-122">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="6f9be-123">Appel à une fonction DLL</span><span class="sxs-lookup"><span data-stu-id="6f9be-123">Calling a DLL Function</span></span>](calling-a-dll-function.md)
