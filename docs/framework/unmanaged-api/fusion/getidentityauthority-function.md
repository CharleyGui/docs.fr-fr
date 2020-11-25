---
title: GetIdentityAuthority, fonction
ms.date: 03/30/2017
api_name:
- GetIdentityAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetIdentityAuthority
helpviewer_keywords:
- GetIdentityAuthority function [.NET Framework fusion]
ms.assetid: 843cd5ab-d2b7-4ff6-86bd-e68c7a91c098
topic_type:
- apiref
ms.openlocfilehash: e9631211993afbfe968c7122828251746f15c3f6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732123"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="a7a7c-102">GetIdentityAuthority, fonction</span><span class="sxs-lookup"><span data-stu-id="a7a7c-102">GetIdentityAuthority Function</span></span>

<span data-ttu-id="a7a7c-103">Obtient un pointeur vers une instance [IIdentityAuthority](iidentityauthority-interface.md) qui gère les clés pour les objets de code.</span><span class="sxs-lookup"><span data-stu-id="a7a7c-103">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7a7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7a7c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7a7c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a7a7c-105">Parameters</span></span>  

 `ppIIdentityAuthority`  
 <span data-ttu-id="a7a7c-106">à Pointeur retourné `IIdentityAuthority` .</span><span class="sxs-lookup"><span data-stu-id="a7a7c-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7a7c-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a7a7c-107">Requirements</span></span>  

 <span data-ttu-id="a7a7c-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7a7c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7a7c-109">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="a7a7c-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="a7a7c-110">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7a7c-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a7c-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7a7c-111">See also</span></span>

- [<span data-ttu-id="a7a7c-112">IIdentityAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="a7a7c-112">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="a7a7c-113">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="a7a7c-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
