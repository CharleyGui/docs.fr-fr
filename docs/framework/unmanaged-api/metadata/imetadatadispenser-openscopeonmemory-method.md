---
title: IMetaDataDispenser::OpenScopeOnMemory, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScopeOnMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScopeOnMemory
helpviewer_keywords:
- OpenScopeOnMemory method [.NET Framework metadata]
- IMetaDataDispenser::OpenScopeOnMemory method [.NET Framework metadata]
ms.assetid: 14218249-bdec-48ae-b5fc-9f57f7ca8501
topic_type:
- apiref
ms.openlocfilehash: 492c37540ad68b5b134520218eedc59013c68519
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175926"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="7074a-102">IMetaDataDispenser::OpenScopeOnMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="7074a-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="7074a-103">Ouvre une zone de mémoire qui contient des métadonnées existantes.</span><span class="sxs-lookup"><span data-stu-id="7074a-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="7074a-104">C’est-à-dire que cette méthode ouvre une zone de mémoire spécifiée dans laquelle les données existantes sont traitées comme des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="7074a-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7074a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7074a-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7074a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7074a-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="7074a-107">[dans] Un pointeur qui spécifie l’adresse de départ de la zone de mémoire.</span><span class="sxs-lookup"><span data-stu-id="7074a-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="7074a-108">[dans] La taille de la zone de mémoire, dans les octets.</span><span class="sxs-lookup"><span data-stu-id="7074a-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="7074a-109">[dans] Une valeur de l’énumération [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) pour spécifier le mode (lire, écrire, etc.) pour l’ouverture.</span><span class="sxs-lookup"><span data-stu-id="7074a-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="7074a-110">[dans] L’IID de l’interface de métadonnée souhaitée à retourner; l’appelant utilisera l’interface pour importer (lire) ou émettre des métadonnées (écrire).</span><span class="sxs-lookup"><span data-stu-id="7074a-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="7074a-111">La valeur `riid` de doit spécifier l’une des interfaces "importation" ou "émettre".</span><span class="sxs-lookup"><span data-stu-id="7074a-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="7074a-112">Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="7074a-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="7074a-113">[out] Le pointeur de l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="7074a-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7074a-114">Notes </span><span class="sxs-lookup"><span data-stu-id="7074a-114">Remarks</span></span>  
 <span data-ttu-id="7074a-115">La copie en mémoire des métadonnées peut être demandée à l’aide de méthodes à partir d’une des interfaces « d’importation », ou ajoutée à l’utilisation de méthodes de l’une des interfaces « émettrices ».</span><span class="sxs-lookup"><span data-stu-id="7074a-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="7074a-116">La `OpenScopeOnMemory` méthode est similaire à la méthode [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) méthode, sauf que les métadonnées d’intérêt existe déjà dans la mémoire, plutôt que dans un fichier sur disque.</span><span class="sxs-lookup"><span data-stu-id="7074a-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="7074a-117">Si la zone cible de mémoire ne contient pas de métadonnées courantes (CLR), la `OpenScopeOnMemory` méthode échouera.</span><span class="sxs-lookup"><span data-stu-id="7074a-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7074a-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7074a-118">Requirements</span></span>  
 <span data-ttu-id="7074a-119">**Plateforme:** Voir [Les exigences du système](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7074a-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7074a-120">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="7074a-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7074a-121">**Bibliothèque:** Utilisé comme ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7074a-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7074a-122">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7074a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7074a-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7074a-123">See also</span></span>

- [<span data-ttu-id="7074a-124">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="7074a-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="7074a-125">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="7074a-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="7074a-126">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="7074a-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="7074a-127">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="7074a-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="7074a-128">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="7074a-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7074a-129">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="7074a-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="7074a-130">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="7074a-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="7074a-131">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="7074a-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
