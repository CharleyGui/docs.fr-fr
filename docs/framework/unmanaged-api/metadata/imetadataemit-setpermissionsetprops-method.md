---
title: IMetaDataEmit::SetPermissionSetProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetPermissionSetProps
helpviewer_keywords:
- SetPermissionSetProps method [.NET Framework metadata]
- IMetaDataEmit::SetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 8eaee971-40bf-45e2-a3d8-6e57674213b6
topic_type:
- apiref
ms.openlocfilehash: de4cfdf2a9353eebdebaf4df9e481d06d776ff04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177489"
---
# <a name="imetadataemitsetpermissionsetprops-method"></a><span data-ttu-id="44732-102">IMetaDataEmit::SetPermissionSetProps, méthode</span><span class="sxs-lookup"><span data-stu-id="44732-102">IMetaDataEmit::SetPermissionSetProps Method</span></span>
<span data-ttu-id="44732-103">Définit ou met à jour les fonctionnalités de la signature des métadonnées d’un ensemble d’autorisation défini par un appel préalable à [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span><span class="sxs-lookup"><span data-stu-id="44732-103">Sets or updates features of the metadata signature of a permission set defined by a prior call to [IMetaDataEmit::DefinePermissionSet](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definepermissionset-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44732-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44732-104">Syntax</span></span>  
  
```cpp  
HRESULT SetPermissionSetProps (
    [in]  mdToken         tk,
    [in]  DWORD           dwAction,
    [in]  void const      *pvPermission,
    [in]  ULONG           cbPermission,
    [out] mdPermission    *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44732-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="44732-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="44732-106">[dans] Un jeton de métadonnées qui représente l’objet à décorer.</span><span class="sxs-lookup"><span data-stu-id="44732-106">[in] A metadata token that represents the object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="44732-107">[dans] Une valeur [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) qui spécifie le type de sécurité déclarative à utiliser.</span><span class="sxs-lookup"><span data-stu-id="44732-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="44732-108">[dans] La permission BLOB.</span><span class="sxs-lookup"><span data-stu-id="44732-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="44732-109">[dans] La taille, dans les `pvPermission`octets, de .</span><span class="sxs-lookup"><span data-stu-id="44732-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="44732-110">[out] Un `mdPermission` jeton de métadonnées qui représente les autorisations mises à jour.</span><span class="sxs-lookup"><span data-stu-id="44732-110">[out] An `mdPermission` metadata token that represents the updated permissions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44732-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="44732-111">Requirements</span></span>  
 <span data-ttu-id="44732-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44732-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44732-113">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="44732-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44732-114">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="44732-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="44732-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44732-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44732-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44732-116">See also</span></span>

- [<span data-ttu-id="44732-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="44732-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="44732-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="44732-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
