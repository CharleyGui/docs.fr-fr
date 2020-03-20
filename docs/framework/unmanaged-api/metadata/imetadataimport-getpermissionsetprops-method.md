---
title: IMetaDataImport::GetPermissionSetProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPermissionSetProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPermissionSetProps
helpviewer_keywords:
- GetPermissionSetProps method [.NET Framework metadata]
- IMetaDataImport::GetPermissionSetProps method [.NET Framework metadata]
ms.assetid: 9855f0e4-12c0-4d3d-ab5d-d6bc52d25eae
topic_type:
- apiref
ms.openlocfilehash: 5faf1a6ae89045b2ef17fab789ee6e5bf23eecf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175341"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="6f55d-102">IMetaDataImport::GetPermissionSetProps, méthode</span><span class="sxs-lookup"><span data-stu-id="6f55d-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="6f55d-103">Obtient les métadonnées <xref:System.Security.PermissionSet?displayProperty=nameWithType> associées à la représentation par le jeton autorisation spécifié.</span><span class="sxs-lookup"><span data-stu-id="6f55d-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f55d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f55d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,
   [out] void const        **ppvPermission,
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f55d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6f55d-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="6f55d-106">[dans] Le jeton de métadonnées d’autorisation qui représente l’ensemble d’autorisation pour obtenir les propriétés de métadonnées pour.</span><span class="sxs-lookup"><span data-stu-id="6f55d-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="6f55d-107">[out] Un pointeur à l’ensemble d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="6f55d-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="6f55d-108">[out] Un pointeur à la signature des métadonnées binaires de l’ensemble d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="6f55d-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="6f55d-109">[out] La taille dans `ppvPermission`les octets de .</span><span class="sxs-lookup"><span data-stu-id="6f55d-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f55d-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="6f55d-110">Requirements</span></span>  
 <span data-ttu-id="6f55d-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f55d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f55d-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="6f55d-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f55d-113">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6f55d-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6f55d-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f55d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f55d-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f55d-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="6f55d-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="6f55d-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6f55d-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="6f55d-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
