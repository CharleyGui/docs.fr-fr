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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be4408758db1cbf7839c12cb66ff395625925f69
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779014"
---
# <a name="imetadataimportgetmodulerefprops-method"></a><span data-ttu-id="72b8c-102">IMetaDataImport::GetModuleRefProps, méthode</span><span class="sxs-lookup"><span data-stu-id="72b8c-102">IMetaDataImport::GetModuleRefProps Method</span></span>
<span data-ttu-id="72b8c-103">Obtient le nom du module référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="72b8c-103">Gets the name of the module referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72b8c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72b8c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleRefProps (  
   [in]  mdModuleRef         mur,  
   [out] LPWSTR              szName,   
   [in]  ULONG               cchName,   
   [out] ULONG               *pchName   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72b8c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="72b8c-105">Parameters</span></span>  
 `mur`  
 <span data-ttu-id="72b8c-106">[in] Le jeton de métadonnées ModuleRef qui fait référence au module pour obtenir des informations de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="72b8c-106">[in] The ModuleRef metadata token that references the module to get metadata information for.</span></span>  
  
 `szName`  
 <span data-ttu-id="72b8c-107">[out] Une mémoire tampon pour contenir le nom du module.</span><span class="sxs-lookup"><span data-stu-id="72b8c-107">[out] A buffer to hold the module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="72b8c-108">[in] La taille demandée de `szName` en caractères larges.</span><span class="sxs-lookup"><span data-stu-id="72b8c-108">[in] The requested size of `szName` in wide characters.</span></span>  
  
 `pchName`  
 <span data-ttu-id="72b8c-109">[out] La taille retournée de `szName` en caractères larges.</span><span class="sxs-lookup"><span data-stu-id="72b8c-109">[out] The returned size of `szName` in wide characters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72b8c-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="72b8c-110">Requirements</span></span>  
 <span data-ttu-id="72b8c-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72b8c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72b8c-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="72b8c-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72b8c-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72b8c-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72b8c-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72b8c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72b8c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72b8c-115">See also</span></span>

- [<span data-ttu-id="72b8c-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="72b8c-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="72b8c-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="72b8c-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
