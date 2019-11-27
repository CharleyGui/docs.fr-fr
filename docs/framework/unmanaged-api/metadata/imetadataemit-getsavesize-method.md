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
ms.openlocfilehash: 125a63638a41707b8eed918253cb1f93abb907eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434333"
---
# <a name="imetadataemitgetsavesize-method"></a><span data-ttu-id="b21b4-102">IMetaDataEmit::GetSaveSize, méthode</span><span class="sxs-lookup"><span data-stu-id="b21b4-102">IMetaDataEmit::GetSaveSize Method</span></span>
<span data-ttu-id="b21b4-103">Obtient la taille estimée en binaire de l’assembly et de ses métadonnées dans la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="b21b4-103">Gets the estimated binary size of the assembly and its metadata in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b21b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b21b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSaveSize (  
    [in]  CorSaveSize fSave,  
    [out] DWORD       *pdwSaveSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b21b4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b21b4-105">Parameters</span></span>  
 `fSave`  
 <span data-ttu-id="b21b4-106">dans Valeur de l’énumération [CorSaveSize,](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) qui spécifie s’il faut obtenir une taille exacte ou approximative.</span><span class="sxs-lookup"><span data-stu-id="b21b4-106">[in] A value of the [CorSaveSize](../../../../docs/framework/unmanaged-api/metadata/corsavesize-enumeration.md) enumeration that specifies whether to get an accurate or approximate size.</span></span> <span data-ttu-id="b21b4-107">Seules trois valeurs sont valides : cssAccurate, cssQuick et cssDiscardTransientCAs :</span><span class="sxs-lookup"><span data-stu-id="b21b4-107">Only three values are valid: cssAccurate, cssQuick, and cssDiscardTransientCAs:</span></span>  
  
- <span data-ttu-id="b21b4-108">cssAccurate retourne la taille d’enregistrement exacte, mais met plus de temps à calculer.</span><span class="sxs-lookup"><span data-stu-id="b21b4-108">cssAccurate returns the exact save size but takes longer to calculate.</span></span>  
  
- <span data-ttu-id="b21b4-109">cssQuick retourne une taille, complétée pour des raisons de sécurité, mais prend moins de temps pour le calcul.</span><span class="sxs-lookup"><span data-stu-id="b21b4-109">cssQuick returns a size, padded for safety, but takes less time to calculate.</span></span>  
  
- <span data-ttu-id="b21b4-110">cssDiscardTransientCAs indique `GetSaveSize` qu’il peut lever des attributs personnalisés pouvant être éliminés.</span><span class="sxs-lookup"><span data-stu-id="b21b4-110">cssDiscardTransientCAs tells `GetSaveSize` that it can throw away discardable custom attributes.</span></span>  
  
 `pdwSaveSize`  
 <span data-ttu-id="b21b4-111">à Pointeur vers la taille requise pour enregistrer le fichier.</span><span class="sxs-lookup"><span data-stu-id="b21b4-111">[out] A pointer to the size that is required to save the file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b21b4-112">Notes</span><span class="sxs-lookup"><span data-stu-id="b21b4-112">Remarks</span></span>  
 <span data-ttu-id="b21b4-113">`GetSaveSize` calcule l’espace nécessaire, en octets, pour enregistrer l’assembly et toutes ses métadonnées dans l’étendue actuelle.</span><span class="sxs-lookup"><span data-stu-id="b21b4-113">`GetSaveSize` calculates the space required, in bytes, to save the assembly and all its metadata in the current scope.</span></span> <span data-ttu-id="b21b4-114">(Un appel à la méthode [IMetaDataEmit :: SaveToStream,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) émettra ce nombre d’octets.)</span><span class="sxs-lookup"><span data-stu-id="b21b4-114">(A call to the [IMetaDataEmit::SaveToStream](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetostream-method.md) method would emit this number of bytes.)</span></span>  
  
 <span data-ttu-id="b21b4-115">Si l’appelant implémente l’interface [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) (via [IMetaDataEmit :: SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) ou [IMetaDataEmit :: Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` effectue deux passes sur les métadonnées pour les optimiser et les compresser.</span><span class="sxs-lookup"><span data-stu-id="b21b4-115">If the caller implements the [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) interface (through [IMetaDataEmit::SetHandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md) or [IMetaDataEmit::Merge](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-merge-method.md)), `GetSaveSize` will perform two passes over the metadata to optimize and compress it.</span></span> <span data-ttu-id="b21b4-116">Dans le cas contraire, aucune optimisation n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="b21b4-116">Otherwise, no optimizations are performed.</span></span>  
  
 <span data-ttu-id="b21b4-117">Si l’optimisation est effectuée, la première passe trie simplement les structures de métadonnées pour régler les performances des recherches au moment de l’importation.</span><span class="sxs-lookup"><span data-stu-id="b21b4-117">If optimization is performed, the first pass simply sorts the metadata structures to tune the performance of import-time searches.</span></span> <span data-ttu-id="b21b4-118">En général, cette étape entraîne le déplacement des enregistrements, avec l’effet secondaire que les jetons conservés par l’outil pour référence ultérieure sont invalidés.</span><span class="sxs-lookup"><span data-stu-id="b21b4-118">This step typically results in moving records around, with the side effect that tokens retained by the tool for future reference are invalidated.</span></span> <span data-ttu-id="b21b4-119">Toutefois, les métadonnées n’informent pas l’appelant de ces modifications de jeton jusqu’à la deuxième passe.</span><span class="sxs-lookup"><span data-stu-id="b21b4-119">The metadata does not inform the caller of these token changes until after the second pass, however.</span></span> <span data-ttu-id="b21b4-120">Au cours de la deuxième passe, différentes optimisations sont effectuées pour réduire la taille globale des métadonnées, telles que l’optimisation de la `mdTypeRef` et des jetons de `mdMemberRef` lorsque la référence est un type ou un membre déclaré dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="b21b4-120">In the second pass, various optimizations are performed that are intended to reduce the overall size of the metadata, such as optimizing away (early binding) `mdTypeRef` and `mdMemberRef` tokens when the reference is to a type or member that is declared in the current metadata scope.</span></span> <span data-ttu-id="b21b4-121">Dans cette étape, un autre mappage de jetons est effectué.</span><span class="sxs-lookup"><span data-stu-id="b21b4-121">In this pass, another round of token mapping occurs.</span></span> <span data-ttu-id="b21b4-122">Après cette étape, le moteur de métadonnées avertit l’appelant, via son interface `IMapToken`, des valeurs de jeton modifiées.</span><span class="sxs-lookup"><span data-stu-id="b21b4-122">After this pass, the metadata engine notifies the caller, through its `IMapToken` interface, of any changed token values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b21b4-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b21b4-123">Requirements</span></span>  
 <span data-ttu-id="b21b4-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b21b4-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b21b4-125">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b21b4-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b21b4-126">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b21b4-126">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b21b4-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b21b4-127">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b21b4-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b21b4-128">See also</span></span>

- [<span data-ttu-id="b21b4-129">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="b21b4-129">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b21b4-130">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="b21b4-130">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
