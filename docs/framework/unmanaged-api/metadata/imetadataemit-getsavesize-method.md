---
title: IMetaDataEmit::GetSaveSize, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetSaveSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetSaveSize
helpviewer_keywords:
- IMetaDataEmit::GetSaveSize method [.NET Framework metadata]
- GetSaveSize method [.NET Framework metadata]
ms.assetid: 8aea2e2c-23a3-4cda-9a06-e19f97383830
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21f6c07976198416bff6e8e2a1789e4ccbf5ca55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665013"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="04ab4-102">IMetaDataEmit::GetSaveSize, méthode</span><span class="sxs-lookup"><span data-stu-id="04ab4-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="04ab4-103">Obtient la taille binaire estimée de l’assembly et ses métadonnées dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="04ab4-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ab4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04ab4-104">Syntax</span></span>  
  
```  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04ab4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="04ab4-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="04ab4-106">[in] Une valeur de la [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) énumération qui spécifie s’il faut obtenir une taille exacte ou approximative.</span><span class="sxs-lookup"><span data-stu-id="04ab4-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="04ab4-107">Seuls les trois valeurs sont valides : cssAccurate, cssQuick et cssDiscardTransientCAs :</span><span class="sxs-lookup"><span data-stu-id="04ab4-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="04ab4-108">cssAccurate retourne la taille d’enregistrement exact, mais prend plus de temps à calculer.</span><span class="sxs-lookup"><span data-stu-id="04ab4-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="04ab4-109">cssQuick retourne une taille, remplie pour la sécurité, mais prend moins de temps à calculer.</span><span class="sxs-lookup"><span data-stu-id="04ab4-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="04ab4-110">cssDiscardTransientCAs indique à `GetSaveSize` qu’il peut jeter des attributs personnalisés pouvant être éliminées.</span><span class="sxs-lookup"><span data-stu-id="04ab4-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="04ab4-111">[out] Un pointeur vers la taille qui est requis pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="04ab4-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04ab4-112">Notes</span><span class="sxs-lookup"><span data-stu-id="04ab4-112">Remarks</span></span>  
 <span data-ttu-id="04ab4-113">`GetSaveSize` calcule l’espace requis, en octets, pour enregistrer l’assembly et toutes ses métadonnées dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="04ab4-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="04ab4-114">(Un appel à la [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) méthode émet ce nombre d’octets.)</span><span class="sxs-lookup"><span data-stu-id="04ab4-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="04ab4-115">Si l’appelant implémente le [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (via [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) ou [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` effectue deux passes sur les métadonnées pour optimiser et les compresser.</span><span class="sxs-lookup"><span data-stu-id="04ab4-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="04ab4-116">Sinon, aucune des optimisations.</span><span class="sxs-lookup"><span data-stu-id="04ab4-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="04ab4-117">Si l’optimisation est effectuée, le premier passage trie simplement les structures de métadonnées pour régler les performances des recherches au moment de l’importation.</span><span class="sxs-lookup"><span data-stu-id="04ab4-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="04ab4-118">Cette étape se produit généralement dans le déplacement des enregistrements, avec comme conséquence que les jetons conservés par l’outil pour référence ultérieure sont invalidés.</span><span class="sxs-lookup"><span data-stu-id="04ab4-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="04ab4-119">Les métadonnées ne pas informent l’appelant de ces modifications apportées aux jetons jusqu’après la deuxième passe, toutefois.</span><span class="sxs-lookup"><span data-stu-id="04ab4-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="04ab4-120">Dans la deuxième passe, différents des optimisations qui sont destinées à réduire la taille globale des métadonnées, telles que l’optimisation (liaison anticipée) `mdTypeRef` et `mdMemberRef` jetons lors de la référence concerne un type ou membre qui est déclaré dans le portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="04ab4-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="04ab4-121">Dans cette étape, une autre série de mappages de jetons se produit.</span><span class="sxs-lookup"><span data-stu-id="04ab4-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="04ab4-122">Après ce passage, le moteur de métadonnées informe l’appelant, via son `IMapToken` interface, de n’importe quel modifié les valeurs de jeton.</span><span class="sxs-lookup"><span data-stu-id="04ab4-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04ab4-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="04ab4-123">Requirements</span></span>  
 <span data-ttu-id="04ab4-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04ab4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04ab4-125">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="04ab4-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04ab4-126">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04ab4-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04ab4-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04ab4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04ab4-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04ab4-128">See also</span></span>

- [<span data-ttu-id="04ab4-129">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="04ab4-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="04ab4-130">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="04ab4-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
