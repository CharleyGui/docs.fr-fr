---
title: IMetaDataImport::GetModuleFromScope, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetModuleFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetModuleFromScope
helpviewer_keywords:
- GetModuleFromScope method [.NET Framework metadata]
- IMetaDataImport::GetModuleFromScope method [.NET Framework metadata]
ms.assetid: add68d3f-45fd-4bef-af94-eb5273f26b11
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 05ce699669095e9c0b45882b18a01ec326640038
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779004"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="804f0-102">IMetaDataImport::GetModuleFromScope, méthode</span><span class="sxs-lookup"><span data-stu-id="804f0-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="804f0-103">Obtient les métadonnées jeton pour le module référencé dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="804f0-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="804f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="804f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="804f0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="804f0-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="804f0-106">[out] Pointeur vers le jeton représentant le module référencé dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="804f0-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="804f0-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="804f0-107">Requirements</span></span>  
 <span data-ttu-id="804f0-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="804f0-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="804f0-109">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="804f0-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="804f0-110">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="804f0-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="804f0-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="804f0-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804f0-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="804f0-112">See also</span></span>

- [<span data-ttu-id="804f0-113">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="804f0-113">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="804f0-114">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="804f0-114">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
