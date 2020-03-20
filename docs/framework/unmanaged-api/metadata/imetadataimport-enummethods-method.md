---
title: IMetaDataImport::EnumMethods, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMethods
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMethods
helpviewer_keywords:
- IMetaDataImport::EnumMethods method [.NET Framework metadata]
- EnumMethods method [.NET Framework metadata]
ms.assetid: 8cc3b0c3-d97d-4f71-9e7d-ef2a92b4959a
topic_type:
- apiref
ms.openlocfilehash: 218b65b5899692774c434ae136a3976ecb97ea2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177305"
---
# <a name="imetadataimportenummethods-method"></a><span data-ttu-id="ec6ec-102">IMetaDataImport::EnumMethods, méthode</span><span class="sxs-lookup"><span data-stu-id="ec6ec-102">IMetaDataImport::EnumMethods Method</span></span>
<span data-ttu-id="ec6ec-103">Énumère les jetons MethodDef représentant les méthodes du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="ec6ec-103">Enumerates MethodDef tokens representing methods of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec6ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec6ec-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMethods (  
   [in, out] HCORENUM   *phEnum,
   [in]  mdTypeDef      cl,
   [out] mdMethodDef    rMethods[],
   [in]  ULONG          cMax,
   [out] ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ec6ec-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec6ec-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="ec6ec-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="ec6ec-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="ec6ec-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="ec6ec-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="ec6ec-108">[dans] Un jeton TypeDef représentant le type avec les méthodes pour énumérer.</span><span class="sxs-lookup"><span data-stu-id="ec6ec-108">[in] A TypeDef token representing the type with the methods to enumerate.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="ec6ec-109">[out] Le tableau pour stocker les jetons MethodDef.</span><span class="sxs-lookup"><span data-stu-id="ec6ec-109">[out] The array to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="ec6ec-110">[dans] La taille maximale du `rMethods` tableau MethodDef.</span><span class="sxs-lookup"><span data-stu-id="ec6ec-110">[in] The maximum size of the MethodDef `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="ec6ec-111">[out] Le nombre de jetons MethodDef retournés dans `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="ec6ec-111">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ec6ec-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ec6ec-112">Return Value</span></span>  
  
|<span data-ttu-id="ec6ec-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ec6ec-113">HRESULT</span></span>|<span data-ttu-id="ec6ec-114">Description</span><span class="sxs-lookup"><span data-stu-id="ec6ec-114">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="ec6ec-115">`EnumMethods`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="ec6ec-115">`EnumMethods` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="ec6ec-116">Il n’y a pas de jetons MethodDef à énumérer.</span><span class="sxs-lookup"><span data-stu-id="ec6ec-116">There are no MethodDef tokens to enumerate.</span></span> <span data-ttu-id="ec6ec-117">Dans ce `pcTokens` cas, c’est zéro.</span><span class="sxs-lookup"><span data-stu-id="ec6ec-117">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec6ec-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ec6ec-118">Requirements</span></span>  
 <span data-ttu-id="ec6ec-119">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec6ec-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec6ec-120">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="ec6ec-120">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ec6ec-121">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ec6ec-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ec6ec-122">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec6ec-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec6ec-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec6ec-123">See also</span></span>

- [<span data-ttu-id="ec6ec-124">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="ec6ec-124">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ec6ec-125">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="ec6ec-125">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
