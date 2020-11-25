---
title: Fonctions statiques globales du débogage
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: 04906322e311b580abddeca7744cf3e75d471e05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722984"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="4860b-102">Fonctions statiques globales du débogage</span><span class="sxs-lookup"><span data-stu-id="4860b-102">Debugging Global Static Functions</span></span>

<span data-ttu-id="4860b-103">Cette section décrit les fonctions statiques globales non managées utilisées par l'API de débogage.</span><span class="sxs-lookup"><span data-stu-id="4860b-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4860b-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4860b-104">In This Section</span></span>  

 [<span data-ttu-id="4860b-105">_EFN_GetManagedExcepStack, fonction</span><span class="sxs-lookup"><span data-stu-id="4860b-105">_EFN_GetManagedExcepStack Function</span></span>](efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="4860b-106">Retourne une version de chaîne de la trace de pile contenue dans une adresse d'objet exception managée donnée.</span><span class="sxs-lookup"><span data-stu-id="4860b-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="4860b-107">_EFN_GetManagedObjectFieldInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="4860b-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="4860b-108">Obtient l'offset du début d'un objet jusqu'à un champ, ainsi que la valeur du champ, à l'aide du pointeur d'objet et du nom de champ fournis.</span><span class="sxs-lookup"><span data-stu-id="4860b-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="4860b-109">_EFN_GetManagedObjectName, fonction</span><span class="sxs-lookup"><span data-stu-id="4860b-109">_EFN_GetManagedObjectName Function</span></span>](efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="4860b-110">Obtient le nom d'un type à l'aide du pointeur d'objet managé fourni.</span><span class="sxs-lookup"><span data-stu-id="4860b-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="4860b-111">_EFN_StackTrace, fonction</span><span class="sxs-lookup"><span data-stu-id="4860b-111">_EFN_StackTrace Function</span></span>](efn-stacktrace-function.md)  
 <span data-ttu-id="4860b-112">Fournit une représentation textuelle d'une trace de pile managée et un tableau d'enregistrements `CONTEXT` pour chaque transition entre du code non managé et du code managé.</span><span class="sxs-lookup"><span data-stu-id="4860b-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="4860b-113">CLRDataCreateInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="4860b-113">CLRDataCreateInstance Function</span></span>](clrdatacreateinstance-function.md)  
 <span data-ttu-id="4860b-114">Appelé par les services d'accès aux données du Common Language Runtime (CLR) pour créer l'objet d'interface spécifié pour le processus cible spécifié.</span><span class="sxs-lookup"><span data-stu-id="4860b-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="4860b-115">PFN_CLRDataCreateInstance (pointeur fonction)</span><span class="sxs-lookup"><span data-stu-id="4860b-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="4860b-116">Pointe vers une fonction qui est appelée par les services d'accès aux données du CLR pour créer l'objet d'interface indiqué pour le processus cible spécifié.</span><span class="sxs-lookup"><span data-stu-id="4860b-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4860b-117">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="4860b-117">Related Sections</span></span>  

 [<span data-ttu-id="4860b-118">Débogage des coclasses</span><span class="sxs-lookup"><span data-stu-id="4860b-118">Debugging Coclasses</span></span>](debugging-coclasses.md)  
  
 [<span data-ttu-id="4860b-119">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="4860b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)  
  
 [<span data-ttu-id="4860b-120">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="4860b-120">Debugging Enumerations</span></span>](debugging-enumerations.md)  
  
 [<span data-ttu-id="4860b-121">Structures de débogage</span><span class="sxs-lookup"><span data-stu-id="4860b-121">Debugging Structures</span></span>](debugging-structures.md)
