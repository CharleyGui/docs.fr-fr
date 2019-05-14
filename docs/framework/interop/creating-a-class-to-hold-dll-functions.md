---
title: Création d'une classe pour contenir des fonctions DLL
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b204eacd43db2c562fbe6d519b5fa91df3466cc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626410"
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="5485e-102">Création d'une classe pour contenir des fonctions DLL</span><span class="sxs-lookup"><span data-stu-id="5485e-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="5485e-103">L’enveloppement d’une fonction DLL fréquemment utilisée dans une classe managée est une stratégie efficace d’encapsulation des fonctionnalités de la plateforme.</span><span class="sxs-lookup"><span data-stu-id="5485e-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="5485e-104">Bien que cette opération ne soit pas obligatoire dans tous les cas, un wrapper de classe s’avère pratique, car la définition de fonctions DLL peut être fastidieuse et sujette à erreurs.</span><span class="sxs-lookup"><span data-stu-id="5485e-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="5485e-105">En cas de programmation en Visual Basic ou C#, vous devez déclarer les fonctions DLL dans une classe ou un module Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5485e-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="5485e-106">Dans une classe, vous définissez une méthode statique pour chaque fonction DLL que vous souhaitez appeler.</span><span class="sxs-lookup"><span data-stu-id="5485e-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="5485e-107">La définition peut inclure des informations supplémentaires, telles que le jeu de caractères ou la convention d’appel qui sont utilisés lors du passage des arguments des méthodes. Si vous ne renseignez pas ces informations, les paramètres par défaut sont alors sélectionnés.</span><span class="sxs-lookup"><span data-stu-id="5485e-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="5485e-108">Pour obtenir une liste complète des options de déclaration et de leurs paramètres par défaut, consultez [Création de prototypes dans du code managé](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="5485e-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="5485e-109">Une fois les méthodes incluses dans un wrapper, vous pouvez les appeler sur la classe de la même manière que vous appelez des méthodes statiques sur toute autre classe.</span><span class="sxs-lookup"><span data-stu-id="5485e-109">Once wrapped, you can call the methods on the class as you call static methods on any other class.</span></span> <span data-ttu-id="5485e-110">L’appel de code non managé gère automatiquement la fonction exportée sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="5485e-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="5485e-111">Lors de la conception d’une classe managée pour l’appel de code non managé, tenez compte des relations entre les classes et les fonctions DLL.</span><span class="sxs-lookup"><span data-stu-id="5485e-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="5485e-112">Par exemple, vous pouvez :</span><span class="sxs-lookup"><span data-stu-id="5485e-112">For example, you can:</span></span>  
  
- <span data-ttu-id="5485e-113">déclarer des fonctions DLL dans une classe existante ;</span><span class="sxs-lookup"><span data-stu-id="5485e-113">Declare DLL functions within an existing class.</span></span>  
  
- <span data-ttu-id="5485e-114">créer une classe individuelle pour chaque fonction DLL, en maintenant les fonctions isolées et facilement localisables ;</span><span class="sxs-lookup"><span data-stu-id="5485e-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
- <span data-ttu-id="5485e-115">créer une classe pour un ensemble de fonctions DLL associées afin de former des regroupements logiques et réduire la charge mémoire.</span><span class="sxs-lookup"><span data-stu-id="5485e-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="5485e-116">Vous pouvez nommer la classe et ses méthodes à votre convenance.</span><span class="sxs-lookup"><span data-stu-id="5485e-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="5485e-117">Pour afficher des exemples montrant comment construire des déclarations .NET à utiliser avec l’appel de code non managé, consultez [Marshaling de données à l’aide de l’appel de code non managé](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="5485e-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5485e-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5485e-118">See also</span></span>

- [<span data-ttu-id="5485e-119">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="5485e-119">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="5485e-120">Identification des fonctions des DLL</span><span class="sxs-lookup"><span data-stu-id="5485e-120">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)
- [<span data-ttu-id="5485e-121">Création de prototypes dans du code managé</span><span class="sxs-lookup"><span data-stu-id="5485e-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="5485e-122">Appel à une fonction DLL</span><span class="sxs-lookup"><span data-stu-id="5485e-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)
