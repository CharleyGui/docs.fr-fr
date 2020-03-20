---
title: IMetaDataEmit::DefineTypeRefByName, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
ms.openlocfilehash: 23a6931b31ea2d7e4e8d1cb3dc8adf3a51216315
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175744"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="5fdcf-102">IMetaDataEmit::DefineTypeRefByName, méthode</span><span class="sxs-lookup"><span data-stu-id="5fdcf-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="5fdcf-103">Obtient un jeton de métadonnées pour un type qui est défini dans la portée spécifiée, qui est en dehors de la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="5fdcf-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fdcf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5fdcf-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5fdcf-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5fdcf-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="5fdcf-106">[dans] Le jeton précisant la portée de résolution.</span><span class="sxs-lookup"><span data-stu-id="5fdcf-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="5fdcf-107">Les types de jetons suivants sont valides :</span><span class="sxs-lookup"><span data-stu-id="5fdcf-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="5fdcf-108">`mdModuleRef`, si le type est défini dans le même assemblage dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="5fdcf-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="5fdcf-109">`mdAssemblyRef`, si le type est défini dans un assemblage autre que celui dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="5fdcf-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="5fdcf-110">`mdTypeRef`, si le type est un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="5fdcf-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="5fdcf-111">`mdModule`, si le type est défini dans le même module dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="5fdcf-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="5fdcf-112">Null, si le type est défini globalement.</span><span class="sxs-lookup"><span data-stu-id="5fdcf-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="5fdcf-113">[dans] Le nom du type cible dans Unicode.</span><span class="sxs-lookup"><span data-stu-id="5fdcf-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="5fdcf-114">[out] Un pointeur `mdTypeRef` au jeton qui est attribué au type.</span><span class="sxs-lookup"><span data-stu-id="5fdcf-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fdcf-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5fdcf-115">Requirements</span></span>  
 <span data-ttu-id="5fdcf-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fdcf-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fdcf-117">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="5fdcf-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5fdcf-118">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5fdcf-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fdcf-119">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fdcf-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fdcf-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5fdcf-120">See also</span></span>

- [<span data-ttu-id="5fdcf-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="5fdcf-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="5fdcf-122">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="5fdcf-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
