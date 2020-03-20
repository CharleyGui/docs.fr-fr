---
title: IMetaDataEmit::DefinePermissionSet, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefinePermissionSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefinePermissionSet
helpviewer_keywords:
- DefinePermissionSet method [.NET Framework metadata]
- IMetaDataEmit::DefinePermissionSet method [.NET Framework metadata]
ms.assetid: 36cffbf7-82ca-4cf9-bf60-50ab491ac2d9
topic_type:
- apiref
ms.openlocfilehash: a0fd3fdb6dde9fd6b88ea6c64ed907c8a3e9e46d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175796"
---
# <a name="imetadataemitdefinepermissionset-method"></a><span data-ttu-id="7ed90-102">IMetaDataEmit::DefinePermissionSet, méthode</span><span class="sxs-lookup"><span data-stu-id="7ed90-102">IMetaDataEmit::DefinePermissionSet Method</span></span>
<span data-ttu-id="7ed90-103">Crée une définition pour un ensemble d’autorisation avec la signature spécifiée de métadonnées, et obtient un jeton à cette définition définie d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="7ed90-103">Creates a definition for a permission set with the specified metadata signature, and gets a token to that permission set definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ed90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ed90-104">Syntax</span></span>  
  
```cpp  
HRESULT DefinePermissionSet (  
    [in]  mdToken        tk,
    [in]  DWORD          dwAction,
    [in]  void const     *pvPermission,
    [in]  ULONG          cbPermission,
    [out] mdPermission   *ppm
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ed90-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7ed90-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="7ed90-106">[dans] L’objet à décorer.</span><span class="sxs-lookup"><span data-stu-id="7ed90-106">[in] The object to be decorated.</span></span>  
  
 `dwAction`  
 <span data-ttu-id="7ed90-107">[dans] Une valeur [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) qui spécifie le type de sécurité déclarative à utiliser.</span><span class="sxs-lookup"><span data-stu-id="7ed90-107">[in] A [CorDeclSecurity](../../../../docs/framework/unmanaged-api/metadata/cordeclsecurity-enumeration.md) value that specifies the type of declarative security to be used.</span></span>  
  
 `pvPermission`  
 <span data-ttu-id="7ed90-108">[dans] La permission BLOB.</span><span class="sxs-lookup"><span data-stu-id="7ed90-108">[in] The permission BLOB.</span></span>  
  
 `cbPermission`  
 <span data-ttu-id="7ed90-109">[dans] La taille, dans les `pvPermission`octets, de .</span><span class="sxs-lookup"><span data-stu-id="7ed90-109">[in] The size, in bytes, of `pvPermission`.</span></span>  
  
 `ppm`  
 <span data-ttu-id="7ed90-110">[out] Le jeton de permission retourné.</span><span class="sxs-lookup"><span data-stu-id="7ed90-110">[out] The returned permission token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ed90-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7ed90-111">Requirements</span></span>  
 <span data-ttu-id="7ed90-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ed90-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ed90-113">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="7ed90-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7ed90-114">**Bibliothèque:** Utilisé comme ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7ed90-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ed90-115">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ed90-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed90-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ed90-116">See also</span></span>

- [<span data-ttu-id="7ed90-117">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="7ed90-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7ed90-118">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="7ed90-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
