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
ms.openlocfilehash: 3dfdd473b01bfe83def52f957c52e0f4d11375ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434383"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="56fdb-102">IMetaDataEmit::DefineTypeRefByName, méthode</span><span class="sxs-lookup"><span data-stu-id="56fdb-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="56fdb-103">Obtient un jeton de métadonnées pour un type qui est défini dans la portée spécifiée, qui est en dehors de la portée actuelle.</span><span class="sxs-lookup"><span data-stu-id="56fdb-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56fdb-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56fdb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56fdb-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="56fdb-106">dans Jeton spécifiant l’étendue de la résolution.</span><span class="sxs-lookup"><span data-stu-id="56fdb-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="56fdb-107">Les types de jetons suivants sont valides :</span><span class="sxs-lookup"><span data-stu-id="56fdb-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="56fdb-108">`mdModuleRef`, si le type est défini dans le même assembly que celui dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="56fdb-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="56fdb-109">`mdAssemblyRef`, si le type est défini dans un assembly autre que celui dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="56fdb-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="56fdb-110">`mdTypeRef`, si le type est un type imbriqué.</span><span class="sxs-lookup"><span data-stu-id="56fdb-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="56fdb-111">`mdModule`, si le type est défini dans le même module dans lequel l’appelant est défini.</span><span class="sxs-lookup"><span data-stu-id="56fdb-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="56fdb-112">NULL, si le type est défini globalement.</span><span class="sxs-lookup"><span data-stu-id="56fdb-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="56fdb-113">dans Nom du type de cible au format Unicode.</span><span class="sxs-lookup"><span data-stu-id="56fdb-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="56fdb-114">à Pointeur vers le jeton de `mdTypeRef` assigné au type.</span><span class="sxs-lookup"><span data-stu-id="56fdb-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56fdb-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="56fdb-115">Requirements</span></span>  
 <span data-ttu-id="56fdb-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56fdb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56fdb-117">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="56fdb-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56fdb-118">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="56fdb-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="56fdb-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56fdb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fdb-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56fdb-120">See also</span></span>

- [<span data-ttu-id="56fdb-121">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="56fdb-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="56fdb-122">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="56fdb-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
