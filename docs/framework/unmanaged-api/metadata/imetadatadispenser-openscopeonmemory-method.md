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
ms.openlocfilehash: 26293e38a275ca691c7d48dceb12c1e7dd316536
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713416"
---
# <a name="imetadatadispenseropenscopeonmemory-method"></a><span data-ttu-id="01567-102">IMetaDataDispenser::OpenScopeOnMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="01567-102">IMetaDataDispenser::OpenScopeOnMemory Method</span></span>

<span data-ttu-id="01567-103">Ouvre une zone de mémoire qui contient des métadonnées existantes.</span><span class="sxs-lookup"><span data-stu-id="01567-103">Opens an area of memory that contains existing metadata.</span></span> <span data-ttu-id="01567-104">Autrement dit, cette méthode ouvre une zone de mémoire spécifiée dans laquelle les données existantes sont traitées en tant que métadonnées.</span><span class="sxs-lookup"><span data-stu-id="01567-104">That is, this method opens a specified area of memory in which the existing data is treated as metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01567-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01567-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnMemory (  
    [in]  LPCVOID     pData,
    [in]  ULONG       cbData,
    [in]  DWORD       dwOpenFlags,
    [in]  REFIID      riid,
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01567-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="01567-106">Parameters</span></span>  

 `pData`  
 <span data-ttu-id="01567-107">dans Pointeur qui spécifie l’adresse de début de la zone mémoire.</span><span class="sxs-lookup"><span data-stu-id="01567-107">[in] A pointer that specifies the starting address of the memory area.</span></span>  
  
 `cbData`  
 <span data-ttu-id="01567-108">dans Taille de la zone de mémoire, en octets.</span><span class="sxs-lookup"><span data-stu-id="01567-108">[in] The size of the memory area, in bytes.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="01567-109">dans Valeur de l’énumération [CorOpenFlags](coropenflags-enumeration.md) pour spécifier le mode (lecture, écriture, etc.) à ouvrir.</span><span class="sxs-lookup"><span data-stu-id="01567-109">[in] A value of the [CorOpenFlags](coropenflags-enumeration.md) enumeration to specify the mode (read, write, and so on) for opening.</span></span>  
  
 `riid`  
 <span data-ttu-id="01567-110">dans IID de l’interface de métadonnées souhaitée à retourner ; l’appelant utilisera l’interface pour importer (Lire) ou émettre (écrire) des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="01567-110">[in] The IID of the desired metadata interface to be returned; the caller will use the interface to import (read) or emit (write) metadata.</span></span>  
  
 <span data-ttu-id="01567-111">La valeur de `riid` doit spécifier l’une des interfaces « import » ou « Emit ».</span><span class="sxs-lookup"><span data-stu-id="01567-111">The value of `riid` must specify one of the "import" or "emit" interfaces.</span></span> <span data-ttu-id="01567-112">Les valeurs valides sont IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2 ou IID_IMetaDataImport2.</span><span class="sxs-lookup"><span data-stu-id="01567-112">Valid values are IID_IMetaDataEmit, IID_IMetaDataImport, IID_IMetaDataAssemblyEmit, IID_IMetaDataAssemblyImport, IID_IMetaDataEmit2, or IID_IMetaDataImport2.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="01567-113">à Pointeur vers l’interface retournée.</span><span class="sxs-lookup"><span data-stu-id="01567-113">[out] The pointer to the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01567-114">Remarques</span><span class="sxs-lookup"><span data-stu-id="01567-114">Remarks</span></span>  

 <span data-ttu-id="01567-115">La copie en mémoire des métadonnées peut être interrogée à l’aide de méthodes de l’une des interfaces d’importation ou ajoutée à l’aide de méthodes à partir de l’une des interfaces d’émission.</span><span class="sxs-lookup"><span data-stu-id="01567-115">The in-memory copy of the metadata can be queried using methods from one of the "import" interfaces, or added to using methods from the one of the "emit" interfaces.</span></span>  
  
 <span data-ttu-id="01567-116">La `OpenScopeOnMemory` méthode est semblable à la méthode [IMetaDataDispenser :: OpenScope](imetadatadispenser-openscope-method.md) , sauf que les métadonnées d’intérêt existent déjà en mémoire, plutôt que dans un fichier sur le disque.</span><span class="sxs-lookup"><span data-stu-id="01567-116">The `OpenScopeOnMemory` method is similar to the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method, except that the metadata of interest already exists in memory, rather than in a file on disk.</span></span>  
  
 <span data-ttu-id="01567-117">Si la zone cible de la mémoire ne contient pas de métadonnées common language runtime (CLR), la `OpenScopeOnMemory` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="01567-117">If the target area of memory does not contain common language runtime (CLR) metadata, the `OpenScopeOnMemory` method will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01567-118">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="01567-118">Requirements</span></span>  

 <span data-ttu-id="01567-119">**Plateforme :** Consultez [Configuration système requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01567-119">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01567-120">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="01567-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="01567-121">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="01567-121">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="01567-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01567-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01567-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="01567-123">See also</span></span>

- [<span data-ttu-id="01567-124">IMetaDataDispenser, interface</span><span class="sxs-lookup"><span data-stu-id="01567-124">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
- [<span data-ttu-id="01567-125">IMetaDataDispenserEx, interface</span><span class="sxs-lookup"><span data-stu-id="01567-125">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="01567-126">IMetaDataAssemblyEmit, interface</span><span class="sxs-lookup"><span data-stu-id="01567-126">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="01567-127">IMetaDataAssemblyImport, interface</span><span class="sxs-lookup"><span data-stu-id="01567-127">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="01567-128">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="01567-128">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="01567-129">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="01567-129">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="01567-130">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="01567-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="01567-131">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="01567-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
