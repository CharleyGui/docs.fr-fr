---
title: IMetaDataEmit::SaveToMemory, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SaveToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SaveToMemory
helpviewer_keywords:
- IMetaDataEmit::SaveToMemory method [.NET Framework metadata]
- SaveToMemory method [.NET Framework metadata]
ms.assetid: d5237628-2675-45ed-a39e-65c0731b6a56
topic_type:
- apiref
ms.openlocfilehash: 1cd5e34d6afefab2fda7e20d4bf73b373ad42787
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688586"
---
# <a name="imetadataemitsavetomemory-method"></a><span data-ttu-id="808a7-102">IMetaDataEmit::SaveToMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="808a7-102">IMetaDataEmit::SaveToMemory Method</span></span>

<span data-ttu-id="808a7-103">Enregistre toutes les métadonnées dans la portée actuelle dans la zone de mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="808a7-103">Saves all metadata in the current scope to the specified area of memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="808a7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="808a7-104">Syntax</span></span>  
  
```cpp  
HRESULT SaveToMemory (
    [out]  void        *pbData,
    [in]   ULONG       cbData
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="808a7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="808a7-105">Parameters</span></span>  

 `pbData`  
 <span data-ttu-id="808a7-106">à Adresse à laquelle commencer l’écriture des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="808a7-106">[out] The address at which to begin writing metadata.</span></span>  
  
 `cbData`  
 <span data-ttu-id="808a7-107">dans Taille, en octets, de la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="808a7-107">[in] The size, in bytes, of the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="808a7-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="808a7-108">Requirements</span></span>  

 <span data-ttu-id="808a7-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="808a7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="808a7-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="808a7-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="808a7-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="808a7-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="808a7-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="808a7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="808a7-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="808a7-113">See also</span></span>

- [<span data-ttu-id="808a7-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="808a7-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="808a7-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="808a7-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
