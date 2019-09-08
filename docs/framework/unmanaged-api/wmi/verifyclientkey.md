---
title: Fonction VerifyClientKey (référence des API non managées)
description: La fonction VerifyClientKey garantit la sécurité de la clé client.
ms.date: 11/06/2017
api_name:
- VerifyClientKey
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- VerifyClientKey
helpviewer_keywords:
- VerifyClientKey function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b674e959ab93cf76b84e2af41e875a50b7d115f4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798190"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="f74b0-103">VerifyClientKey fonction)</span><span class="sxs-lookup"><span data-stu-id="f74b0-103">VerifyClientKey function</span></span>
<span data-ttu-id="f74b0-104">Garantit que la clé du client offre une sécurité correcte.</span><span class="sxs-lookup"><span data-stu-id="f74b0-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f74b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f74b0-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="f74b0-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f74b0-106">Return value</span></span>

<span data-ttu-id="f74b0-107">Si la fonction est réussie, la valeur de retour `ERROR_SUCCESS` est (0).</span><span class="sxs-lookup"><span data-stu-id="f74b0-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="f74b0-108">Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans *winerror. h*.</span><span class="sxs-lookup"><span data-stu-id="f74b0-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="f74b0-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f74b0-109">Requirements</span></span>  
 <span data-ttu-id="f74b0-110">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f74b0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f74b0-111">**En-tête :** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="f74b0-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="f74b0-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f74b0-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f74b0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f74b0-113">See also</span></span>

- [<span data-ttu-id="f74b0-114">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="f74b0-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
