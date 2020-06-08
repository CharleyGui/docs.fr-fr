---
title: IMetaDataEmit::SetParent, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetParent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetParent
helpviewer_keywords:
- SetParent method [.NET Framework metadata]
- IMetaDataEmit::SetParent method [.NET Framework metadata]
ms.assetid: 02a02ff7-ae0e-4692-a20e-372405f23052
topic_type:
- apiref
ms.openlocfilehash: d821413e67b36392d936499cd22f2e065f1556ec
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503846"
---
# <a name="imetadataemitsetparent-method"></a><span data-ttu-id="4adb6-102">IMetaDataEmit::SetParent, méthode</span><span class="sxs-lookup"><span data-stu-id="4adb6-102">IMetaDataEmit::SetParent Method</span></span>
<span data-ttu-id="4adb6-103">Établit que le membre spécifié, tel que défini par un appel antérieur à [IMetaDataEmit ::D efinememberref](imetadataemit-definememberref-method.md), est un membre du type spécifié, tel que défini par un appel antérieur à [IMetaDataEmit ::D efinetypedef](imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="4adb6-103">Establishes that the specified member, as defined by a prior call to [IMetaDataEmit::DefineMemberRef](imetadataemit-definememberref-method.md), is a member of the specified type, as defined by a prior call to [IMetaDataEmit::DefineTypeDef](imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4adb6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4adb6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetParent (
    [in]  mdMemberRef mr,
    [in]  mdToken     tk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4adb6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4adb6-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="4adb6-106">dans `mdMemberRef`Jeton pour recevoir un nouveau parent.</span><span class="sxs-lookup"><span data-stu-id="4adb6-106">[in] The `mdMemberRef` token to receive a new parent.</span></span>  
  
 `tk`  
 <span data-ttu-id="4adb6-107">dans `mdToken`Pour le nouveau parent.</span><span class="sxs-lookup"><span data-stu-id="4adb6-107">[in] The `mdToken` for the new parent.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4adb6-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4adb6-108">Requirements</span></span>  
 <span data-ttu-id="4adb6-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4adb6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4adb6-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4adb6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4adb6-111">**Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4adb6-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4adb6-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4adb6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4adb6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4adb6-113">See also</span></span>

- [<span data-ttu-id="4adb6-114">IMetaDataEmit, interface</span><span class="sxs-lookup"><span data-stu-id="4adb6-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="4adb6-115">IMetaDataEmit2, interface</span><span class="sxs-lookup"><span data-stu-id="4adb6-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
