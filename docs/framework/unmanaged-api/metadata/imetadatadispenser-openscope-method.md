---
title: IMetaDataDispenser::OpenScope, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataDispenser.OpenScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenser::OpenScope
helpviewer_keywords:
- IMetaDataDispenser::OpenScope method [.NET Framework metadata]
- OpenScope method, IMetaDataDispenser interface [.NET Framework metadata]
ms.assetid: 65063ad5-e0d9-4c01-8f8b-9a5950109fa6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6e157c758b472ea89e21c1ed1ba8c17693c20a3d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777790"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="4a2af-102">IMetaDataDispenser::OpenScope, méthode</span><span class="sxs-lookup"><span data-stu-id="4a2af-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="4a2af-103">Ouvre un fichier sur disque existant et mappe ses métadonnées dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4a2af-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a2af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a2af-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,   
    [in]  DWORD       dwOpenFlags,   
    [in]  REFIID      riid,   
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a2af-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4a2af-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="4a2af-106">[in] Le nom du fichier à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="4a2af-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="4a2af-107">Le fichier doit contenir des métadonnées du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="4a2af-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="4a2af-108">[in] Une valeur de la [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) énumération pour spécifier le mode (lecture, écriture et ainsi de suite) pour l’ouverture.</span><span class="sxs-lookup"><span data-stu-id="4a2af-108">[in] A value of the [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="4a2af-109">[in] L’IID de l’interface de métadonnées souhaitée doit être retournée ; l’appelant utilisera l’interface à importer (lecture) ou émettre des métadonnées de (écriture).</span><span class="sxs-lookup"><span data-stu-id="4a2af-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="4a2af-110">La valeur de `riid` doit spécifier une des interfaces « importation » ou « émettre ».</span><span class="sxs-lookup"><span data-stu-id="4a2af-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="4a2af-111">Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="4a2af-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="4a2af-112">[out] Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="4a2af-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a2af-113">Notes</span><span class="sxs-lookup"><span data-stu-id="4a2af-113">Remarks</span></span>  
 <span data-ttu-id="4a2af-114">La copie en mémoire des métadonnées peut être interrogée à l’aide de méthodes à partir d’une des interfaces « importation » ou ajouté à l’aide des méthodes à partir de l’une des interfaces « émettre ».</span><span class="sxs-lookup"><span data-stu-id="4a2af-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="4a2af-115">Si le fichier cible ne contient-elle pas de métadonnées CLR, la `OpenScope` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="4a2af-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="4a2af-116">Dans le .NET Framework versions 1.0 et 1.1, si une étendue est ouvert avec `dwOpenFlags` défini sur ofRead, elle est éligible pour le partage.</span><span class="sxs-lookup"><span data-stu-id="4a2af-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="4a2af-117">Autrement dit, si suivantes les appels à `OpenScope` transmettez le nom d’un fichier qui a été ouverte précédemment, la portée existante est réutilisée et un nouvel ensemble de structures de données n’est pas créé.</span><span class="sxs-lookup"><span data-stu-id="4a2af-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="4a2af-118">Toutefois, des problèmes peuvent survenir en raison de ce partage.</span><span class="sxs-lookup"><span data-stu-id="4a2af-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="4a2af-119">Dans la version 2.0 du .NET Framework, les portées ouvertes avec `dwOpenFlags` défini sur ofRead ne sont plus partagées.</span><span class="sxs-lookup"><span data-stu-id="4a2af-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="4a2af-120">Utilisez la valeur ofReadOnly pour autoriser l’étendue à partager.</span><span class="sxs-lookup"><span data-stu-id="4a2af-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="4a2af-121">Lorsqu’une étendue est partagée, les requêtes qui utilisent des « en lecture/écriture » des interfaces de métadonnées échoue.</span><span class="sxs-lookup"><span data-stu-id="4a2af-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a2af-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4a2af-122">Requirements</span></span>  
 <span data-ttu-id="4a2af-123">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a2af-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a2af-124">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4a2af-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a2af-125">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a2af-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a2af-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a2af-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a2af-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a2af-127">See also</span></span>

- [<span data-ttu-id="4a2af-128">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="4a2af-128">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
- [<span data-ttu-id="4a2af-129">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="4a2af-129">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="4a2af-130">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="4a2af-130">IMetaDataAssemblyEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [<span data-ttu-id="4a2af-131">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="4a2af-131">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
- [<span data-ttu-id="4a2af-132">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="4a2af-132">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="4a2af-133">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="4a2af-133">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="4a2af-134">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="4a2af-134">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="4a2af-135">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="4a2af-135">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
