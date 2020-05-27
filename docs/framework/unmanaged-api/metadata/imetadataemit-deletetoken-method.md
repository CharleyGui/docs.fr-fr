---
title: IMetaDataEmit::DeleteToken, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DeleteToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DeleteToken
helpviewer_keywords:
- DeleteToken method [.NET Framework metadata]
- IMetaDataEmit::DeleteToken method [.NET Framework metadata]
ms.assetid: a4926d0a-261b-46b1-9994-82633661a64b
topic_type:
- apiref
ms.openlocfilehash: 78f3ea0d84c932732a752f3af2dc952100fef831
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009273"
---
# <a name="imetadataemitdeletetoken-method"></a><span data-ttu-id="0dfee-102">IMetaDataEmit::DeleteToken, méthode</span><span class="sxs-lookup"><span data-stu-id="0dfee-102">IMetaDataEmit::DeleteToken Method</span></span>
<span data-ttu-id="0dfee-103">Supprime le jeton spécifié de la portée de métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="0dfee-103">Deletes the specified token from the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dfee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0dfee-104">Syntax</span></span>  
  
```cpp  
HRESULT DeleteToken (
    [in]  mdToken     tkObj
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dfee-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0dfee-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="0dfee-106">dans Jeton à supprimer.</span><span class="sxs-lookup"><span data-stu-id="0dfee-106">[in] The token to be deleted.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dfee-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0dfee-107">Requirements</span></span>  
 <span data-ttu-id="0dfee-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dfee-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dfee-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0dfee-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0dfee-110">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0dfee-110">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0dfee-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dfee-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dfee-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dfee-112">See also</span></span>

- [<span data-ttu-id="0dfee-113">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="0dfee-113">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0dfee-114">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="0dfee-114">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
