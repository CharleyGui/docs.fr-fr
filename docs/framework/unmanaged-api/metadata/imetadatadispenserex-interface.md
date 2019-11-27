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
ms.openlocfilehash: 985cdea670714394119fb846e9e55a01713559a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431143"
---
# <a name="imetadatadispenserex-interface"></a><span data-ttu-id="f1a37-102">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="f1a37-102">IMetaDataDispenserEx Interface</span></span>
<span data-ttu-id="f1a37-103">Étend l’interface d' [interface IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) pour permettre de contrôler la manière dont les API de métadonnées fonctionnent sur la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="f1a37-103">Extends the [IMetaDataDispenser Interface](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md) interface to provide the capability to control how the metadata APIs operate on the current metadata scope.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1a37-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="f1a37-104">Methods</span></span>  
  
|<span data-ttu-id="f1a37-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="f1a37-105">Method</span></span>|<span data-ttu-id="f1a37-106">Description</span><span class="sxs-lookup"><span data-stu-id="f1a37-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1a37-107">FindAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="f1a37-107">FindAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassembly-method.md)|<span data-ttu-id="f1a37-108">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="f1a37-108">This method is not implemented.</span></span> <span data-ttu-id="f1a37-109">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="f1a37-109">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="f1a37-110">FindAssemblyModule, méthode</span><span class="sxs-lookup"><span data-stu-id="f1a37-110">FindAssemblyModule Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-findassemblymodule-method.md)|<span data-ttu-id="f1a37-111">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="f1a37-111">This method is not implemented.</span></span> <span data-ttu-id="f1a37-112">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="f1a37-112">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="f1a37-113">GetCORSystemDirectory, méthode</span><span class="sxs-lookup"><span data-stu-id="f1a37-113">GetCORSystemDirectory Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getcorsystemdirectory-method.md)|<span data-ttu-id="f1a37-114">Obtient le répertoire qui contient le common language runtime actuel (CLR).</span><span class="sxs-lookup"><span data-stu-id="f1a37-114">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="f1a37-115">Cette méthode est prise en charge uniquement par les débogueurs hors processus.</span><span class="sxs-lookup"><span data-stu-id="f1a37-115">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="f1a37-116">Si elle est appelée à partir d’un autre composant, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="f1a37-116">If called from another component, it will return E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="f1a37-117">GetOption, méthode</span><span class="sxs-lookup"><span data-stu-id="f1a37-117">GetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-getoption-method.md)|<span data-ttu-id="f1a37-118">Obtient la valeur de l’option spécifiée pour la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="f1a37-118">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="f1a37-119">L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.</span><span class="sxs-lookup"><span data-stu-id="f1a37-119">The option controls how calls to the current metadata scope are handled.</span></span>|  
|[<span data-ttu-id="f1a37-120">OpenScopeOnITypeInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="f1a37-120">OpenScopeOnITypeInfo Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-openscopeonitypeinfo-method.md)|<span data-ttu-id="f1a37-121">Cette méthode n’est pas implémentée.</span><span class="sxs-lookup"><span data-stu-id="f1a37-121">This method is not implemented.</span></span> <span data-ttu-id="f1a37-122">Si elle est appelée, elle retourne E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="f1a37-122">If called, it returns E_NOTIMPL.</span></span>|  
|[<span data-ttu-id="f1a37-123">SetOption, méthode</span><span class="sxs-lookup"><span data-stu-id="f1a37-123">SetOption Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)|<span data-ttu-id="f1a37-124">Définit l’option spécifiée sur une valeur donnée pour la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="f1a37-124">Sets the specified option to a given value for the current metadata scope.</span></span> <span data-ttu-id="f1a37-125">L’option contrôle la manière dont les appels à la portée de métadonnées actuelle sont gérés.</span><span class="sxs-lookup"><span data-stu-id="f1a37-125">The option controls how calls to the current metadata scope are handled.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1a37-126">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f1a37-126">Requirements</span></span>  
 <span data-ttu-id="f1a37-127">**Plateforme :** Consultez [Configuration système requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1a37-127">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1a37-128">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f1a37-128">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f1a37-129">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f1a37-129">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f1a37-130">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1a37-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a37-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1a37-131">See also</span></span>

- [<span data-ttu-id="f1a37-132">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="f1a37-132">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="f1a37-133">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="f1a37-133">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="f1a37-134">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="f1a37-134">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="f1a37-135">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="f1a37-135">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
