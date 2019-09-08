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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796554"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="68f61-102">IAssemblyName, interface</span><span class="sxs-lookup"><span data-stu-id="68f61-102">IAssemblyName Interface</span></span>
<span data-ttu-id="68f61-103">Fournit des méthodes pour décrire et utiliser l’identité unique d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="68f61-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68f61-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="68f61-104">Methods</span></span>  
  
|<span data-ttu-id="68f61-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="68f61-105">Method</span></span>|<span data-ttu-id="68f61-106">Description</span><span class="sxs-lookup"><span data-stu-id="68f61-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68f61-107">Clone, méthode</span><span class="sxs-lookup"><span data-stu-id="68f61-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="68f61-108">Crée une copie superficielle de cet `IAssemblyName` objet.</span><span class="sxs-lookup"><span data-stu-id="68f61-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="68f61-109">Finalize, méthode</span><span class="sxs-lookup"><span data-stu-id="68f61-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="68f61-110">Permet à `IAssemblyName` cet objet de libérer des ressources et d’effectuer d’autres opérations de nettoyage avant l’appel de son destructeur.</span><span class="sxs-lookup"><span data-stu-id="68f61-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="68f61-111">GetDisplayName, méthode</span><span class="sxs-lookup"><span data-stu-id="68f61-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="68f61-112">Obtient le nom explicite de l’assembly référencé par cet `IAssemblyName` objet.</span><span class="sxs-lookup"><span data-stu-id="68f61-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="68f61-113">GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="68f61-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="68f61-114">Obtient le nom simple et non chiffré de l’assembly référencé par cet `IAssemblyName` objet.</span><span class="sxs-lookup"><span data-stu-id="68f61-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="68f61-115">GetProperty, méthode</span><span class="sxs-lookup"><span data-stu-id="68f61-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="68f61-116">Obtient un pointeur vers la propriété référencée par le spécifié `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="68f61-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="68f61-117">GetVersion, méthode</span><span class="sxs-lookup"><span data-stu-id="68f61-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="68f61-118">Obtient les informations de version de l’assembly référencé par `IAssemblyName` cet objet.</span><span class="sxs-lookup"><span data-stu-id="68f61-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="68f61-119">IsEqual, méthode</span><span class="sxs-lookup"><span data-stu-id="68f61-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="68f61-120">Détermine si un objet `IAssemblyName` spécifié est égal à ce `IAssemblyName`, en fonction des indicateurs de comparaison spécifiés.</span><span class="sxs-lookup"><span data-stu-id="68f61-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="68f61-121">SetProperty, méthode</span><span class="sxs-lookup"><span data-stu-id="68f61-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="68f61-122">Définit la valeur de la propriété référencée par le spécifié `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="68f61-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68f61-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="68f61-123">Requirements</span></span>  
 <span data-ttu-id="68f61-124">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68f61-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f61-125">**En-tête :** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="68f61-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="68f61-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f61-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f61-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68f61-127">See also</span></span>

- [<span data-ttu-id="68f61-128">Interfaces de fusion</span><span class="sxs-lookup"><span data-stu-id="68f61-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="68f61-129">IAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="68f61-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
