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
ms.openlocfilehash: acb80f3cc199d4d9f774cb3898335d26fe44b807
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127146"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="0b467-102">GetIdentityAuthority, fonction</span><span class="sxs-lookup"><span data-stu-id="0b467-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="0b467-103">Obtient un pointeur vers une instance [IIdentityAuthority](iidentityauthority-interface.md) qui gère les clés pour les objets de code.</span><span class="sxs-lookup"><span data-stu-id="0b467-103">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b467-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b467-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b467-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0b467-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="0b467-106">à Pointeur de `IIdentityAuthority` retourné.</span><span class="sxs-lookup"><span data-stu-id="0b467-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b467-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="0b467-107">Requirements</span></span>  
 <span data-ttu-id="0b467-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b467-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b467-109">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="0b467-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="0b467-110">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b467-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b467-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b467-111">See also</span></span>

- [<span data-ttu-id="0b467-112">IIdentityAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="0b467-112">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="0b467-113">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="0b467-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
