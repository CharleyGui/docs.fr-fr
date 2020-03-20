---
title: IMetaDataImport::EnumMemberRefs, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMemberRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMemberRefs
helpviewer_keywords:
- EnumMemberRefs method [.NET Framework metadata]
- IMetaDataImport::EnumMemberRefs method [.NET Framework metadata]
ms.assetid: e97c97a6-6e4f-41f5-9af1-9b3cf3bdbd6b
topic_type:
- apiref
ms.openlocfilehash: b8a65b0748fec0e474d8b3b5dc03473fbd716108
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177331"
---
# <a name="imetadataimportenummemberrefs-method"></a><span data-ttu-id="02a6a-102">IMetaDataImport::EnumMemberRefs, méthode</span><span class="sxs-lookup"><span data-stu-id="02a6a-102">IMetaDataImport::EnumMemberRefs Method</span></span>
<span data-ttu-id="02a6a-103">Énumère les jetons MemberRef représentant les membres du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="02a6a-103">Enumerates MemberRef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02a6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02a6a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMemberRefs (  
   [in, out] HCORENUM    *phEnum,
   [in]   mdToken        tkParent,
   [out]  mdMemberRef    rMemberRefs[],
   [in]   ULONG          cMax,
   [out]  ULONG          *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02a6a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="02a6a-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="02a6a-106">[dans, dehors] Un pointeur à l’enumérateur.</span><span class="sxs-lookup"><span data-stu-id="02a6a-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `tkParent`  
 <span data-ttu-id="02a6a-107">[dans] Un jeton TypeDef, TypeRef, MethodDef ou ModuleRef pour le type dont les membres doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="02a6a-107">[in] A TypeDef, TypeRef, MethodDef, or ModuleRef token for the type whose members are to be enumerated.</span></span>  
  
 `rMemberRefs`  
 <span data-ttu-id="02a6a-108">[out] Le tableau utilisé pour stocker les jetons MemberRef.</span><span class="sxs-lookup"><span data-stu-id="02a6a-108">[out] The array used to store MemberRef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="02a6a-109">[in] Taille maximale du tableau `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="02a6a-109">[in] The maximum size of the `rMemberRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="02a6a-110">[out] Le nombre réel de jetons MemberRef retournés dans `rMemberRefs`.</span><span class="sxs-lookup"><span data-stu-id="02a6a-110">[out] The actual number of MemberRef tokens returned in `rMemberRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02a6a-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="02a6a-111">Return Value</span></span>  
  
|<span data-ttu-id="02a6a-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="02a6a-112">HRESULT</span></span>|<span data-ttu-id="02a6a-113">Description</span><span class="sxs-lookup"><span data-stu-id="02a6a-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="02a6a-114">`EnumMemberRefs`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="02a6a-114">`EnumMemberRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="02a6a-115">Il n’y a pas de jetons MemberRef à énumérer.</span><span class="sxs-lookup"><span data-stu-id="02a6a-115">There are no MemberRef tokens to enumerate.</span></span> <span data-ttu-id="02a6a-116">Dans ce `pcTokens` cas, est à zéro.</span><span class="sxs-lookup"><span data-stu-id="02a6a-116">In that case, `pcTokens` is to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="02a6a-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="02a6a-117">Requirements</span></span>  
 <span data-ttu-id="02a6a-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02a6a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02a6a-119">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="02a6a-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02a6a-120">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="02a6a-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="02a6a-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02a6a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a6a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02a6a-122">See also</span></span>

- [<span data-ttu-id="02a6a-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="02a6a-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="02a6a-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="02a6a-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
