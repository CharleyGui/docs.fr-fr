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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 204e5660e95434f8d0c44d54f4fdbb1c2acc1e5d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777785"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="b8465-102">IMetaDataDispenser::OpenScopeOnMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="b8465-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>
<span data-ttu-id="b8465-103">Ouvre une zone de mémoire qui contient les métadonnées existantes.</span><span class="sxs-lookup"><span data-stu-id="b8465-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="b8465-104">Autrement dit, cette méthode ouvre une zone de mémoire dans lequel les données existantes sont traitées en tant que métadonnées spécifiée.</span><span class="sxs-lookup"><span data-stu-id="b8465-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8465-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8465-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,   
    [in]  ULONG       cbData,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8465-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b8465-106">Parameters</span></span>  
 `pData`  
 <span data-ttu-id="b8465-107">[in] Pointeur qui spécifie l’adresse de départ de la zone de mémoire.</span><span class="sxs-lookup"><span data-stu-id="b8465-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="b8465-108">[in] La taille de la zone de mémoire, en octets.</span><span class="sxs-lookup"><span data-stu-id="b8465-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="b8465-109">[in] Une valeur de la [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) énumération pour spécifier le mode (lecture, écriture et ainsi de suite) pour l’ouverture.</span><span class="sxs-lookup"><span data-stu-id="b8465-109">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="b8465-110">[in] L’IID de l’interface de métadonnées souhaitée doit être retournée ; l’appelant utilisera l’interface à importer (lecture) ou émettre des métadonnées de (écriture).</span><span class="sxs-lookup"><span data-stu-id="b8465-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="b8465-111">La valeur de `riid` doit spécifier une des interfaces « importation » ou « émettre ».</span><span class="sxs-lookup"><span data-stu-id="b8465-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="b8465-112">Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="b8465-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="b8465-113">[out] Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="b8465-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8465-114">Notes</span><span class="sxs-lookup"><span data-stu-id="b8465-114">Remarks</span></span>  
 <span data-ttu-id="b8465-115">La copie en mémoire des métadonnées peut être interrogée à l’aide de méthodes à partir d’une des interfaces « importation » ou ajouté à l’aide des méthodes à partir de l’une des interfaces « émettre ».</span><span class="sxs-lookup"><span data-stu-id="b8465-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="b8465-116">Le `OpenScopeOnMemory` méthode est similaire à la [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) (méthode), à ceci près que les métadonnées qui vous intéresse existent déjà dans la mémoire, plutôt que dans un fichier sur disque.</span><span class="sxs-lookup"><span data-stu-id="b8465-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="b8465-117">Si la zone de mémoire cible ne contient-elle pas de métadonnées de common language runtime (CLR), le `OpenScopeOnMemory` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="b8465-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8465-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b8465-118">Requirements</span></span>  
 <span data-ttu-id="b8465-119">**Plateforme :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8465-119">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8465-120">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b8465-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b8465-121">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8465-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8465-122">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8465-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8465-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8465-123">See also</span></span>

- [<span data-ttu-id="b8465-124">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="b8465-124">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="b8465-125">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="b8465-125">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="b8465-126">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="b8465-126">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="b8465-127">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="b8465-127">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="b8465-128">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="b8465-128">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b8465-129">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="b8465-129">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="b8465-130">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="b8465-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b8465-131">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="b8465-131">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
