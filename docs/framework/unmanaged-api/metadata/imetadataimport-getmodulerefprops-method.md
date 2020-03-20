---
title: IMetaDataImport::GetModuleRefProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleRefProps
helpviewer_keywords:
- GetModuleRefProps method [.NET Framework metadata]
- IMetaDataImport::GetModuleRefProps method [.NET Framework metadata]
ms.assetid: b558e766-4c11-4628-ae47-b4e0a1800168
topic_type:
- apiref
ms.openlocfilehash: f46033b9e643ef6b4a0063c4995b8c024b8c1f7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175354"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="9a047-102">IMetaDataImport::GetModuleRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="9a047-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="9a047-103">Obtient le nom du module référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="9a047-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a047-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a047-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,
   [in]  ULONG               cchName,
   [out] ULONG               *pchName
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a047-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9a047-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="9a047-106">[dans] Les métadonnées ModuleRef qui fait référence au module pour obtenir des informations sur les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="9a047-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="9a047-107">[out] Un tampon pour tenir le nom du module.</span><span class="sxs-lookup"><span data-stu-id="9a047-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="9a047-108">[dans] La taille `szName` demandée en caractères larges.</span><span class="sxs-lookup"><span data-stu-id="9a047-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="9a047-109">[out] La taille `szName` retournée de dans les caractères larges.</span><span class="sxs-lookup"><span data-stu-id="9a047-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a047-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9a047-110">Requirements</span></span>  
 <span data-ttu-id="9a047-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a047-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a047-112">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="9a047-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a047-113">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a047-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a047-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a047-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a047-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a047-115">See also</span></span>

- [<span data-ttu-id="9a047-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="9a047-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="9a047-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="9a047-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
