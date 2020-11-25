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
ms.openlocfilehash: b83c868f1a804d4e6f32adffc190ae086aa5e0a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719331"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="a5cb7-102">IMetaDataEmit::DefineTypeRefByName, méthode</span><span class="sxs-lookup"><span data-stu-id="a5cb7-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>

<span data-ttu-id="a5cb7-103">Obtient un jeton de métadonnées pour un type qui est défini dans la portée spécifiée, qui est en dehors de la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="a5cb7-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5cb7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5cb7-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5cb7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a5cb7-105">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="a5cb7-106">dans Jeton spécifiant l’étendue de la résolution.</span><span class="sxs-lookup"><span data-stu-id="a5cb7-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="a5cb7-107">Les types de jetons suivants sont valides :</span><span class="sxs-lookup"><span data-stu-id="a5cb7-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="a5cb7-108">`mdModuleRef`Si le type est défini dans le même assembly que celui dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="a5cb7-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="a5cb7-109">`mdAssemblyRef`Si le type est défini dans un assembly autre que celui dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="a5cb7-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="a5cb7-110">`mdTypeRef`, si le type est un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="a5cb7-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="a5cb7-111">`mdModule`Si le type est défini dans le même module que celui dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="a5cb7-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="a5cb7-112">NULL, si le type est défini globalement.</span><span class="sxs-lookup"><span data-stu-id="a5cb7-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="a5cb7-113">dans Nom du type de cible au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="a5cb7-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="a5cb7-114">à Pointeur vers le `mdTypeRef` jeton qui est assigné au type.</span><span class="sxs-lookup"><span data-stu-id="a5cb7-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5cb7-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a5cb7-115">Requirements</span></span>  

 <span data-ttu-id="a5cb7-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5cb7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5cb7-117">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a5cb7-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a5cb7-118">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a5cb7-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a5cb7-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5cb7-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5cb7-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5cb7-120">See also</span></span>

- [<span data-ttu-id="a5cb7-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="a5cb7-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a5cb7-122">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="a5cb7-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
