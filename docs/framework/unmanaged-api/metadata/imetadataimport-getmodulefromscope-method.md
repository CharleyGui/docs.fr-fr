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
ms.openlocfilehash: 4e2b2501b6b7117cefcfa43511ef20f25106bb42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503581"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="6931c-102">IMetaDataImport::GetModuleFromScope, méthode</span><span class="sxs-lookup"><span data-stu-id="6931c-102">IMetaDataImport::GetModuleFromScope Method</span></span>
<span data-ttu-id="6931c-103">Obtient un jeton de métadonnées pour le module référencé dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="6931c-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6931c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6931c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6931c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6931c-105">Parameters</span></span>  
 `pmd`  
 <span data-ttu-id="6931c-106">à Pointeur vers le jeton qui représente le module référencé dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="6931c-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6931c-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6931c-107">Requirements</span></span>  
 <span data-ttu-id="6931c-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6931c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6931c-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6931c-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6931c-110">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6931c-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6931c-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6931c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6931c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6931c-112">See also</span></span>

- [<span data-ttu-id="6931c-113">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="6931c-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="6931c-114">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="6931c-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
