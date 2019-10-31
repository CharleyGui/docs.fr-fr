---
title: IAssemblyName, interface
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
ms.openlocfilehash: de49d66667033dfc6918b139f90cd5523661597f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134318"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="aa581-102">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="aa581-102">IAssemblyName Interface</span></span>
<span data-ttu-id="aa581-103">Fournit des méthodes pour décrire et utiliser l’identité unique d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="aa581-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aa581-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="aa581-104">Methods</span></span>  
  
|<span data-ttu-id="aa581-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="aa581-105">Method</span></span>|<span data-ttu-id="aa581-106">Description</span><span class="sxs-lookup"><span data-stu-id="aa581-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aa581-107">Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="aa581-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="aa581-108">Crée une copie superficielle de cet objet `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="aa581-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="aa581-109">Finalize, méthode</span><span class="sxs-lookup"><span data-stu-id="aa581-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="aa581-110">Permet à cet objet `IAssemblyName` de libérer des ressources et d’effectuer d’autres opérations de nettoyage avant l’appel de son destructeur.</span><span class="sxs-lookup"><span data-stu-id="aa581-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="aa581-111">GetDisplayName, méthode</span><span class="sxs-lookup"><span data-stu-id="aa581-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="aa581-112">Obtient le nom explicite de l’assembly référencé par cet objet `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="aa581-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="aa581-113">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="aa581-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="aa581-114">Obtient le nom simple et non chiffré de l’assembly référencé par cet objet `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="aa581-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="aa581-115">GetProperty, méthode</span><span class="sxs-lookup"><span data-stu-id="aa581-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="aa581-116">Obtient un pointeur vers la propriété référencée par le `PropertyId`spécifié.</span><span class="sxs-lookup"><span data-stu-id="aa581-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="aa581-117">GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="aa581-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="aa581-118">Obtient les informations de version de l’assembly référencé par cet objet `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="aa581-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="aa581-119">IsEqual, méthode</span><span class="sxs-lookup"><span data-stu-id="aa581-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="aa581-120">Détermine si un objet `IAssemblyName` spécifié est égal à cet `IAssemblyName`, en fonction des indicateurs de comparaison spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aa581-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="aa581-121">SetProperty, méthode</span><span class="sxs-lookup"><span data-stu-id="aa581-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="aa581-122">Définit la valeur de la propriété référencée par le `PropertyId`spécifié.</span><span class="sxs-lookup"><span data-stu-id="aa581-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aa581-123">spécifications</span><span class="sxs-lookup"><span data-stu-id="aa581-123">Requirements</span></span>  
 <span data-ttu-id="aa581-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa581-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa581-125">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="aa581-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="aa581-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa581-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa581-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa581-127">See also</span></span>

- [<span data-ttu-id="aa581-128">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="aa581-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="aa581-129">IAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="aa581-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
