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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f29246bdb929c8eaf1ebce726164d5cd2269b9f1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796860"
---
# <a name="getidentityauthority-function"></a><span data-ttu-id="3595a-102">GetIdentityAuthority, fonction</span><span class="sxs-lookup"><span data-stu-id="3595a-102">GetIdentityAuthority Function</span></span>
<span data-ttu-id="3595a-103">Obtient un pointeur vers une instance [IIdentityAuthority](iidentityauthority-interface.md) qui gère les clés pour les objets de code.</span><span class="sxs-lookup"><span data-stu-id="3595a-103">Gets a pointer to an [IIdentityAuthority](iidentityauthority-interface.md) instance that manages keys for code objects.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3595a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3595a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIdentityAuthority (  
    [out] IIdentityAuthority   **ppIIdentityAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="3595a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3595a-105">Parameters</span></span>  
 `ppIIdentityAuthority`  
 <span data-ttu-id="3595a-106">à Pointeur retourné `IIdentityAuthority` .</span><span class="sxs-lookup"><span data-stu-id="3595a-106">[out] The returned `IIdentityAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3595a-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3595a-107">Requirements</span></span>  
 <span data-ttu-id="3595a-108">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3595a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3595a-109">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="3595a-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="3595a-110">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3595a-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3595a-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3595a-111">See also</span></span>

- [<span data-ttu-id="3595a-112">IIdentityAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="3595a-112">IIdentityAuthority Interface</span></span>](iidentityauthority-interface.md)
- [<span data-ttu-id="3595a-113">Fonctions statiques globales de fusion</span><span class="sxs-lookup"><span data-stu-id="3595a-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
