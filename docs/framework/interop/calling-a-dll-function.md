---
title: Appel à une fonction DLL
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged functions, calling
- unmanaged functions
- COM interop, platform invoke
- platform invoke, calling unmanaged functions
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 113646de-7ea0-4f0e-8df0-c46dab3e8733
ms.openlocfilehash: 14589544e05f6c59f4f58f7723fef40e75af9823
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123717"
---
# <a name="calling-a-dll-function"></a><span data-ttu-id="d6adf-102">Appel à une fonction DLL</span><span class="sxs-lookup"><span data-stu-id="d6adf-102">Calling a DLL Function</span></span>
<span data-ttu-id="d6adf-103">Même si l’appel à des fonctions DLL non managées est quasiment identique à l’appel à un autre code managé, certaines différences peuvent rendre les fonctions DLL déconcertantes au départ.</span><span class="sxs-lookup"><span data-stu-id="d6adf-103">Although calling unmanaged DLL functions is nearly identical to calling other managed code, there are differences that can make DLL functions seem confusing at first.</span></span> <span data-ttu-id="d6adf-104">Cette section présente des rubriques qui décrivent certaines questions relatives à des appels peu courants.</span><span class="sxs-lookup"><span data-stu-id="d6adf-104">This section introduces topics that describe some of the unusual calling-related issues.</span></span>  
  
 <span data-ttu-id="d6adf-105">Les structures qui sont retournées par les appels de code non managé doivent être des types de données avec la même représentation dans le code managé et non managé.</span><span class="sxs-lookup"><span data-stu-id="d6adf-105">Structures that are returned from platform invoke calls must be data types that have the same representation in managed and unmanaged code.</span></span> <span data-ttu-id="d6adf-106">Ces types sont appelés *types blittables* parce qu’ils ne nécessitent pas de conversion (consultez [Types blittables et non blittables](blittable-and-non-blittable-types.md)).</span><span class="sxs-lookup"><span data-stu-id="d6adf-106">Such types are called *blittable types* because they do not require conversion (see [Blittable and Non-Blittable Types](blittable-and-non-blittable-types.md)).</span></span> <span data-ttu-id="d6adf-107">Pour appeler une fonction qui a une structure non blittable comme type de retour, vous pouvez définir un type d’assistance blittable de la même taille que le type non blittable et convertir les données après le retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d6adf-107">To call a function that has a non-blittable structure as its return type, you can define a blittable helper type of the same size as the non-blittable type and convert the data after the function returns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6adf-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d6adf-108">In This Section</span></span>  
 [<span data-ttu-id="d6adf-109">Passage de structures</span><span class="sxs-lookup"><span data-stu-id="d6adf-109">Passing Structures</span></span>](passing-structures.md)  
 <span data-ttu-id="d6adf-110">Identifie les questions de passage de structures de données avec une disposition prédéfinie.</span><span class="sxs-lookup"><span data-stu-id="d6adf-110">Identifies the issues of passing data structures with a predefined layout.</span></span>  
  
 [<span data-ttu-id="d6adf-111">Fonctions de rappel</span><span class="sxs-lookup"><span data-stu-id="d6adf-111">Callback Functions</span></span>](callback-functions.md)  
 <span data-ttu-id="d6adf-112">Fournit des informations de base sur les fonctions de rappel.</span><span class="sxs-lookup"><span data-stu-id="d6adf-112">Provides basic information about callback functions.</span></span>  
  
 [<span data-ttu-id="d6adf-113">Comment : implémenter des fonctions de rappel</span><span class="sxs-lookup"><span data-stu-id="d6adf-113">How to: Implement Callback Functions</span></span>](how-to-implement-callback-functions.md)  
 <span data-ttu-id="d6adf-114">Décrit comment implémenter des fonctions de rappel dans du code managé.</span><span class="sxs-lookup"><span data-stu-id="d6adf-114">Describes how to implement callback functions in managed code.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d6adf-115">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="d6adf-115">Related Sections</span></span>  
 [<span data-ttu-id="d6adf-116">Consommation de fonctions DLL non managées</span><span class="sxs-lookup"><span data-stu-id="d6adf-116">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
 <span data-ttu-id="d6adf-117">Décrit comment appeler des fonctions DLL non managées à l’aide de l’appel de code non managé.</span><span class="sxs-lookup"><span data-stu-id="d6adf-117">Describes how to call unmanaged DLL functions using platform invoke.</span></span>  
  
 [<span data-ttu-id="d6adf-118">Marshaling de données à l’aide de l’appel de code managé</span><span class="sxs-lookup"><span data-stu-id="d6adf-118">Marshaling Data with Platform Invoke</span></span>](marshaling-data-with-platform-invoke.md)  
 <span data-ttu-id="d6adf-119">Décrit comment déclarer des paramètres de méthode et passer des arguments à des fonctions exportées par des bibliothèques non managées.</span><span class="sxs-lookup"><span data-stu-id="d6adf-119">Describes how to declare method parameters and pass arguments to functions exported by unmanaged libraries.</span></span>
