---
title: IMetaDataDispenser::DefineScope, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.DefineScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::DefineScope
helpviewer_keywords:
- DefineScope method [.NET Framework metadata]
- IMetaDataDispenser::DefineScope method [.NET Framework metadata]
ms.assetid: af28db02-29af-45ac-aec6-8d6c6123c2ff
topic_type:
- apiref
ms.openlocfilehash: 12a32b5d2f0647ea2d9b696d08d6644e30be0c65
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501350"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="67a7d-102">IMetaDataDispenser::DefineScope, méthode</span><span class="sxs-lookup"><span data-stu-id="67a7d-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="67a7d-103">Crée une zone en mémoire dans laquelle vous pouvez créer des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="67a7d-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67a7d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="67a7d-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67a7d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="67a7d-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="67a7d-106">dans CLSID de la version des structures de métadonnées à créer.</span><span class="sxs-lookup"><span data-stu-id="67a7d-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="67a7d-107">Cette valeur doit être CLSID_CorMetaDataRuntime pour la version .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="67a7d-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="67a7d-108">dans Indicateurs qui spécifient des options.</span><span class="sxs-lookup"><span data-stu-id="67a7d-108">[in] Flags that specify options.</span></span> <span data-ttu-id="67a7d-109">Cette valeur doit être égale à zéro pour le .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="67a7d-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="67a7d-110">dans IID de l’interface de métadonnées souhaitée à retourner ; l’appelant utilisera l’interface pour créer les nouvelles métadonnées.</span><span class="sxs-lookup"><span data-stu-id="67a7d-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="67a7d-111">La valeur de `riid` doit spécifier l’une des interfaces « Emit ».</span><span class="sxs-lookup"><span data-stu-id="67a7d-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="67a7d-112">Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit ou IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="67a7d-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="67a7d-113">à Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="67a7d-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="67a7d-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="67a7d-114">Remarks</span></span>  
 <span data-ttu-id="67a7d-115">`DefineScope`crée un ensemble de tables de métadonnées en mémoire, génère un GUID unique (identificateur de version de module, ou MVID) pour les métadonnées, et crée une entrée dans la table de module pour l’unité de compilation en cours d’émission.</span><span class="sxs-lookup"><span data-stu-id="67a7d-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="67a7d-116">Vous pouvez attacher des attributs à la portée de métadonnées dans son ensemble à l’aide de la méthode [IMetaDataEmit :: SetModuleProps,](imetadataemit-setmoduleprops-method.md) ou [IMetaDataEmit ::D efinecustomattribute](imetadataemit-definecustomattribute-method.md) , selon le cas.</span><span class="sxs-lookup"><span data-stu-id="67a7d-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67a7d-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="67a7d-117">Requirements</span></span>  
 <span data-ttu-id="67a7d-118">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67a7d-118">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67a7d-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="67a7d-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="67a7d-120">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="67a7d-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="67a7d-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67a7d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67a7d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67a7d-122">See also</span></span>

- [<span data-ttu-id="67a7d-123">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="67a7d-123">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="67a7d-124">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="67a7d-124">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="67a7d-125">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="67a7d-125">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="67a7d-126">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="67a7d-126">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="67a7d-127">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="67a7d-127">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
