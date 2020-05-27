---
title: IMetaDataDispenserEx, interface
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx
helpviewer_keywords:
- IMetaDataDispenserEx interface [.NET Framework metadata]
ms.assetid: 78b3629e-77a2-4406-89c3-56b5cc2c4594
topic_type:
- apiref
ms.openlocfilehash: 96f0c0c254ce255581ac2937c805096918ab29e8
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008051"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="3b393-102">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="3b393-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="3b393-103">Étend l’interface d' [interface IMetaDataDispenser](imetadatadispenser-interface.md) pour permettre de contrôler la manière dont les API de métadonnées fonctionnent sur la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="3b393-103">Extends the [IMetaDataDispenser Interface](imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b393-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3b393-104">Methods</span></span>  
  
|<span data-ttu-id="3b393-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="3b393-105">Method</span></span>|<span data-ttu-id="3b393-106">Description</span><span class="sxs-lookup"><span data-stu-id="3b393-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3b393-107">FindAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="3b393-107">FindAssembly Method</span></span>](imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="3b393-108">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="3b393-108">This method is not implemented.</span></span> <span data-ttu-id="3b393-109">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="3b393-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="3b393-110">FindAssemblyModule, méthode</span><span class="sxs-lookup"><span data-stu-id="3b393-110">FindAssemblyModule Method</span></span>](imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="3b393-111">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="3b393-111">This method is not implemented.</span></span> <span data-ttu-id="3b393-112">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="3b393-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="3b393-113">GetCORSystemDirectory, méthode</span><span class="sxs-lookup"><span data-stu-id="3b393-113">GetCORSystemDirectory Method</span></span>](imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="3b393-114">Obtient le répertoire qui contient le common language runtime actuel (CLR).</span><span class="sxs-lookup"><span data-stu-id="3b393-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="3b393-115">Cette méthode est prise en charge uniquement par les débogueurs hors processus.</span><span class="sxs-lookup"><span data-stu-id="3b393-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="3b393-116">Si elle est appelée à partir d’un autre composant, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="3b393-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="3b393-117">GetOption, méthode</span><span class="sxs-lookup"><span data-stu-id="3b393-117">GetOption Method</span></span>](imetadatadispenserex-getoption-method.md)|<span data-ttu-id="3b393-118">Obtient la valeur de l’option spécifiée pour la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="3b393-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="3b393-119">L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.</span><span class="sxs-lookup"><span data-stu-id="3b393-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="3b393-120">OpenScopeOnITypeInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="3b393-120">OpenScopeOnITypeInfo Method</span></span>](imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="3b393-121">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="3b393-121">This method is not implemented.</span></span> <span data-ttu-id="3b393-122">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="3b393-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="3b393-123">SetOption, méthode</span><span class="sxs-lookup"><span data-stu-id="3b393-123">SetOption Method</span></span>](imetadatadispenserex-setoption-method.md)|<span data-ttu-id="3b393-124">Définit l’option spécifiée sur une valeur donnée pour la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="3b393-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="3b393-125">L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.</span><span class="sxs-lookup"><span data-stu-id="3b393-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b393-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3b393-126">Requirements</span></span>  
 <span data-ttu-id="3b393-127">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b393-127">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b393-128">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3b393-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b393-129">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3b393-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b393-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b393-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b393-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b393-131">See also</span></span>

- [<span data-ttu-id="3b393-132">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="3b393-132">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="3b393-133">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="3b393-133">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="3b393-134">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="3b393-134">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="3b393-135">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="3b393-135">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
