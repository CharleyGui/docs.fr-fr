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
ms.openlocfilehash: 2eddd7a80c2b9c1b71f3e7fc5b1e4686ba11bccd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733163"
---
# <a name="imetadataimportgetmodulefromscope-method"></a><span data-ttu-id="4a70e-102">IMetaDataImport::GetModuleFromScope, méthode</span><span class="sxs-lookup"><span data-stu-id="4a70e-102">IMetaDataImport::GetModuleFromScope Method</span></span>

<span data-ttu-id="4a70e-103">Obtient un jeton de métadonnées pour le module référencé dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="4a70e-103">Gets a metadata token for the module referenced in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a70e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a70e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromScope (  
   [out] mdModule    *pmd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a70e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4a70e-105">Parameters</span></span>  

 `pmd`  
 <span data-ttu-id="4a70e-106">à Pointeur vers le jeton qui représente le module référencé dans la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="4a70e-106">[out] A pointer to the token representing the module referenced in the current metadata scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a70e-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4a70e-107">Requirements</span></span>  

 <span data-ttu-id="4a70e-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a70e-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a70e-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4a70e-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4a70e-110">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4a70e-110">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4a70e-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a70e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a70e-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a70e-112">See also</span></span>

- [<span data-ttu-id="4a70e-113">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="4a70e-113">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4a70e-114">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="4a70e-114">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
