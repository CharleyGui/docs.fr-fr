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
ms.openlocfilehash: a020a0343eecceb4a85ebbddffe323c7f7bdca3d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437110"
---
# <a name="imetadataimportgetpermissionsetprops-method"></a><span data-ttu-id="8a4de-102">IMetaDataImport::GetPermissionSetProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8a4de-102">IMetaDataImport::GetPermissionSetProps Method</span></span>
<span data-ttu-id="8a4de-103">Obtient les métadonnées associées au <xref:System.Security.PermissionSet?displayProperty=nameWithType> représenté par le jeton d’autorisation spécifié.</span><span class="sxs-lookup"><span data-stu-id="8a4de-103">Gets the metadata associated with the <xref:System.Security.PermissionSet?displayProperty=nameWithType> represented by the specified Permission token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a4de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a4de-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPermissionSetProps (  
   [in]  mdPermission      pm,  
   [out] DWORD             *pdwAction,   
   [out] void const        **ppvPermission,   
   [out] ULONG             *pcbPermission  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a4de-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a4de-105">Parameters</span></span>  
 `pm`  
 <span data-ttu-id="8a4de-106">dans Jeton de métadonnées d’autorisation qui représente le jeu d’autorisations pour lequel obtenir les propriétés de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="8a4de-106">[in] The Permission metadata token that represents the permission set to get the metadata properties for.</span></span>  
  
 `pdwAction`  
 <span data-ttu-id="8a4de-107">à Pointeur vers le jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="8a4de-107">[out] A pointer to the permission set.</span></span>  
  
 `ppvPermission`  
 <span data-ttu-id="8a4de-108">à Pointeur vers la signature de métadonnées binaires du jeu d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="8a4de-108">[out] A pointer to the binary metadata signature of the permission set.</span></span>  
  
 `pcbPermission`  
 <span data-ttu-id="8a4de-109">à Taille en octets de `ppvPermission`.</span><span class="sxs-lookup"><span data-stu-id="8a4de-109">[out] The size in bytes of `ppvPermission`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a4de-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8a4de-110">Requirements</span></span>  
 <span data-ttu-id="8a4de-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a4de-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a4de-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8a4de-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8a4de-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8a4de-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8a4de-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a4de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a4de-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a4de-115">See also</span></span>

- <xref:System.Security.PermissionSet>
- [<span data-ttu-id="8a4de-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="8a4de-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="8a4de-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="8a4de-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
