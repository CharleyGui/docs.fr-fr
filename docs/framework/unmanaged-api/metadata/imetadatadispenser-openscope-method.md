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
ms.openlocfilehash: 8d9de753f1c44338a96e990def80643d591f2a8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007466"
---
# <a name="imetadatadispenseropenscope-method"></a><span data-ttu-id="89dda-102">IMetaDataDispenser::OpenScope, méthode</span><span class="sxs-lookup"><span data-stu-id="89dda-102">IMetaDataDispenser::OpenScope Method</span></span>
<span data-ttu-id="89dda-103">Ouvre un fichier sur disque existant et mappe ses métadonnées en mémoire.</span><span class="sxs-lookup"><span data-stu-id="89dda-103">Opens an existing, on-disk file and maps its metadata into memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89dda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89dda-104">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope (  
    [in]  LPCWSTR     szScope,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89dda-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89dda-105">Parameters</span></span>  
 `szScope`  
 <span data-ttu-id="89dda-106">dans Nom du fichier à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="89dda-106">[in] The name of the file to be opened.</span></span> <span data-ttu-id="89dda-107">Le fichier doit contenir des métadonnées common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="89dda-107">The file must contain common language runtime (CLR) metadata.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="89dda-108">dans Valeur de l’énumération [CorOpenFlags](coropenflags-enumeration.md) pour spécifier le mode (lecture, écriture, etc.) à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="89dda-108">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="89dda-109">dans IID de l’interface de métadonnées souhaitée à retourner ; l’appelant utilisera l’interface pour importer (Lire) ou émettre (écrire) des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="89dda-109">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="89dda-110">La valeur de `riid` doit spécifier l’une des interfaces « import » ou « Emit ».</span><span class="sxs-lookup"><span data-stu-id="89dda-110">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="89dda-111">Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="89dda-111">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="89dda-112">à Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="89dda-112">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89dda-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="89dda-113">Remarks</span></span>  
 <span data-ttu-id="89dda-114">La copie en mémoire des métadonnées peut être interrogée à l’aide de méthodes de l’une des interfaces d’importation ou ajoutée à l’aide de méthodes à partir de l’une des interfaces d’émission.</span><span class="sxs-lookup"><span data-stu-id="89dda-114">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="89dda-115">Si le fichier cible ne contient pas de métadonnées CLR, la `OpenScope` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="89dda-115">If the target file does not contain CLR metadata, the `OpenScope` method will fail.</span></span>  
  
 <span data-ttu-id="89dda-116">Dans le .NET Framework version 1,0 et la version 1,1, si une étendue est ouverte avec la `dwOpenFlags` valeur ofRead, elle est éligible au partage.</span><span class="sxs-lookup"><span data-stu-id="89dda-116">In the .NET Framework version 1.0 and version 1.1, if a scope is opened with `dwOpenFlags` set to ofRead, it is eligible for sharing.</span></span> <span data-ttu-id="89dda-117">Autrement dit, si des appels suivants sont `OpenScope` passés au nom d’un fichier qui a été ouvert précédemment, l’étendue existante est réutilisée et un nouvel ensemble de structures de données n’est pas créé.</span><span class="sxs-lookup"><span data-stu-id="89dda-117">That is, if subsequent calls to `OpenScope` pass in the name of a file that was previously opened, the existing scope is reused and a new set of data structures is not created.</span></span> <span data-ttu-id="89dda-118">Toutefois, des problèmes peuvent survenir en raison de ce partage.</span><span class="sxs-lookup"><span data-stu-id="89dda-118">However, problems can arise due to this sharing.</span></span>  
  
 <span data-ttu-id="89dda-119">Dans la version de .NET Framework 2,0, les étendues ouvertes avec `dwOpenFlags` définies sur ofRead ne sont plus partagées.</span><span class="sxs-lookup"><span data-stu-id="89dda-119">In the .NET Framework version 2.0, scopes opened with `dwOpenFlags` set to ofRead are no longer shared.</span></span> <span data-ttu-id="89dda-120">Utilisez la valeur ofReadOnly pour autoriser le partage de l’étendue.</span><span class="sxs-lookup"><span data-stu-id="89dda-120">Use the ofReadOnly value to allow the scope to be shared.</span></span> <span data-ttu-id="89dda-121">Lorsqu’une étendue est partagée, les requêtes qui utilisent des interfaces de métadonnées en lecture/écriture échouent.</span><span class="sxs-lookup"><span data-stu-id="89dda-121">When a scope is shared, queries that use "read/write" metadata interfaces will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89dda-122">Spécifications</span><span class="sxs-lookup"><span data-stu-id="89dda-122">Requirements</span></span>  
 <span data-ttu-id="89dda-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89dda-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89dda-124">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="89dda-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89dda-125">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="89dda-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="89dda-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89dda-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89dda-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89dda-127">See also</span></span>

- [<span data-ttu-id="89dda-128">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="89dda-128">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="89dda-129">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="89dda-129">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="89dda-130">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="89dda-130">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="89dda-131">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="89dda-131">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="89dda-132">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="89dda-132">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="89dda-133">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="89dda-133">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="89dda-134">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="89dda-134">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="89dda-135">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="89dda-135">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
