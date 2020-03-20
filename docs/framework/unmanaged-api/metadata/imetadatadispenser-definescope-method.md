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
ms.openlocfilehash: 2f9325f3795262a0c33af02f87fc5d3a020658cf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177640"
---
# <a name="imetadatadispenserdefinescope-method"></a><span data-ttu-id="54245-102">IMetaDataDispenser::DefineScope, méthode</span><span class="sxs-lookup"><span data-stu-id="54245-102">IMetaDataDispenser::DefineScope Method</span></span>
<span data-ttu-id="54245-103">Crée une nouvelle zone dans la mémoire dans laquelle vous pouvez créer de nouvelles métadonnées.</span><span class="sxs-lookup"><span data-stu-id="54245-103">Creates a new area in memory in which you can create new metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54245-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54245-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineScope (  
    [in]  REFCLSID    rclsid,  
    [in]  DWORD       dwCreateFlags,  
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54245-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="54245-105">Parameters</span></span>  
 `rclsid`  
 <span data-ttu-id="54245-106">[dans] Le CLSID de la version des structures de métadonnées à créer.</span><span class="sxs-lookup"><span data-stu-id="54245-106">[in] The CLSID of the version of metadata structures to be created.</span></span> <span data-ttu-id="54245-107">Cette valeur doit être CLSID_CorMetaDataRuntime pour la version cadre .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="54245-107">This value must be CLSID_CorMetaDataRuntime for the .NET Framework version 2.0.</span></span>  
  
 `dwCreateFlags`  
 <span data-ttu-id="54245-108">[dans] Drapeaux qui spécifient les options.</span><span class="sxs-lookup"><span data-stu-id="54245-108">[in] Flags that specify options.</span></span> <span data-ttu-id="54245-109">Cette valeur doit être nulle pour le cadre .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="54245-109">This value must be zero for the .NET Framework 2.0.</span></span>  
  
 `riid`  
 <span data-ttu-id="54245-110">[dans] L’IID de l’interface de métadonnée souhaitée à retourner; l’appelant utilisera l’interface pour créer les nouvelles métadonnées.</span><span class="sxs-lookup"><span data-stu-id="54245-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to create the new metadata.</span></span>  
  
 <span data-ttu-id="54245-111">La valeur `riid` de doit spécifier l’une des interfaces "emit".</span><span class="sxs-lookup"><span data-stu-id="54245-111">The value of `riid` must specify one of the "emit" interfaces.</span></span> <span data-ttu-id="54245-112">Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit ou IID_IMetaDataEmit2.</span><span class="sxs-lookup"><span data-stu-id="54245-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataAssemblyEmit, or IID_IMetaDataEmit2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="54245-113">[out] Le pointeur de l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="54245-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54245-114">Notes </span><span class="sxs-lookup"><span data-stu-id="54245-114">Remarks</span></span>  
 <span data-ttu-id="54245-115">`DefineScope`crée un ensemble de tables de métadonnées en mémoire, génère un GUID unique (identificateur de version module, ou MVID) pour les métadonnées, et crée une entrée dans la table du module pour l’unité de compilation émise.</span><span class="sxs-lookup"><span data-stu-id="54245-115">`DefineScope` creates a set of in-memory metadata tables, generates a unique GUID (module version identifier, or MVID) for the metadata, and creates an entry in the module table for the compilation unit being emitted.</span></span>  
  
 <span data-ttu-id="54245-116">Vous pouvez attacher des attributs à la portée des métadonnées dans son ensemble en utilisant [l’IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) ou [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) méthode, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="54245-116">You can attach attributes to the metadata scope as a whole by using the [IMetaDataEmit::SetModuleProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmoduleprops-method.md) or [IMetaDataEmit::DefineCustomAttribute](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definecustomattribute-method.md) method, as appropriate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54245-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="54245-117">Requirements</span></span>  
 <span data-ttu-id="54245-118">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54245-118">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54245-119">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="54245-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="54245-120">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54245-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="54245-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54245-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54245-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="54245-122">See also</span></span>

- [<span data-ttu-id="54245-123">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="54245-123">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="54245-124">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="54245-124">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="54245-125">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="54245-125">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="54245-126">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="54245-126">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="54245-127">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="54245-127">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
