---
title: IMetaDataImport::EnumTypeDefs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: 2d6e86a7f5a93b900e79907f8ee0762869d7f737
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177299"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="12bd6-102">IMetaDataImport::EnumTypeDefs, méthode</span><span class="sxs-lookup"><span data-stu-id="12bd6-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="12bd6-103">Énumère les jetons TypeDef représentant tous les types au sein la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="12bd6-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12bd6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12bd6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12bd6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="12bd6-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="12bd6-106">[out] Un pointeur pour le nouvel enumérateur.</span><span class="sxs-lookup"><span data-stu-id="12bd6-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="12bd6-107">Cela doit être NULL pour le premier appel de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="12bd6-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="12bd6-108">[dans] Le tableau utilisé pour stocker les jetons TypeDef.</span><span class="sxs-lookup"><span data-stu-id="12bd6-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="12bd6-109">[in] Taille maximale du tableau `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="12bd6-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="12bd6-110">[out] Le nombre de jetons TypeDef retournés dans `rTypeDefs`.</span><span class="sxs-lookup"><span data-stu-id="12bd6-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12bd6-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="12bd6-111">Return Value</span></span>  
  
|<span data-ttu-id="12bd6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12bd6-112">HRESULT</span></span>|<span data-ttu-id="12bd6-113">Description</span><span class="sxs-lookup"><span data-stu-id="12bd6-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="12bd6-114">`EnumTypeDefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="12bd6-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="12bd6-115">Il n’y a pas de jetons à énumérer.</span><span class="sxs-lookup"><span data-stu-id="12bd6-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="12bd6-116">Dans ce `pcTypeDefs` cas, c’est zéro.</span><span class="sxs-lookup"><span data-stu-id="12bd6-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12bd6-117">Notes </span><span class="sxs-lookup"><span data-stu-id="12bd6-117">Remarks</span></span>  
 <span data-ttu-id="12bd6-118">Le jeton TypeDef représente un type tel qu’une classe ou une interface, ainsi que n’importe quel type ajouté via un mécanisme d’extensibility.</span><span class="sxs-lookup"><span data-stu-id="12bd6-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12bd6-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="12bd6-119">Requirements</span></span>  
 <span data-ttu-id="12bd6-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12bd6-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12bd6-121">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="12bd6-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12bd6-122">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="12bd6-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="12bd6-123">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12bd6-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12bd6-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12bd6-124">See also</span></span>

- [<span data-ttu-id="12bd6-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="12bd6-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="12bd6-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="12bd6-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
