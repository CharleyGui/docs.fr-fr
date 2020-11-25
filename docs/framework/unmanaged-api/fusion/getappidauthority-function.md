---
title: GetAppIdAuthority, fonction
ms.date: 03/30/2017
api_name:
- GetAppIdAuthority
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- GetAppIdAuthority
helpviewer_keywords:
- GetAppIdAuthority function [.NET Framework fusion]
ms.assetid: 9f968dad-0d09-47fb-bebc-94c39a0d16ad
topic_type:
- apiref
ms.openlocfilehash: 5e731ac1c652b8b4505073a3a10463ae0ce21ac0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724492"
---
# <a name="getappidauthority-function"></a><span data-ttu-id="58e56-102">GetAppIdAuthority, fonction</span><span class="sxs-lookup"><span data-stu-id="58e56-102">GetAppIdAuthority Function</span></span>

<span data-ttu-id="58e56-103">Obtient un pointeur vers une instance [IAppIdAuthority](iappidauthority-interface.md) qui gère les clés pour les identités et les références de l’application.</span><span class="sxs-lookup"><span data-stu-id="58e56-103">Gets a pointer to an [IAppIdAuthority](iappidauthority-interface.md) instance that manages keys for application identities and references.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58e56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58e56-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppIdAuthority (  
    [out] IAppIdAuthority **ppIAppIdAuthority  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="58e56-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58e56-105">Parameters</span></span>  

 `ppIAppIdAuthority`  
 <span data-ttu-id="58e56-106">à Pointeur retourné `IAppIdAuthority` .</span><span class="sxs-lookup"><span data-stu-id="58e56-106">[out] The returned `IAppIdAuthority` pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58e56-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="58e56-107">Requirements</span></span>  

 <span data-ttu-id="58e56-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58e56-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58e56-109">**En-tête :** Isolation. h</span><span class="sxs-lookup"><span data-stu-id="58e56-109">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="58e56-110">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58e56-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58e56-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58e56-111">See also</span></span>

- [<span data-ttu-id="58e56-112">IAppIdAuthority, interface</span><span class="sxs-lookup"><span data-stu-id="58e56-112">IAppIdAuthority Interface</span></span>](iappidauthority-interface.md)
- [<span data-ttu-id="58e56-113">Fonctions statiques globales de la fusion</span><span class="sxs-lookup"><span data-stu-id="58e56-113">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
