---
title: VerifyClientKey (fonction) (référence des API non managées)
description: La fonction VerifyClientKey garantit que la clé du client a la sécurité correcte.
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
ms.openlocfilehash: f4b51fe4510f4172227d9afd049eb6815790a165
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783084"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="b5c4c-103">VerifyClientKey (fonction)</span><span class="sxs-lookup"><span data-stu-id="b5c4c-103">VerifyClientKey function</span></span>
<span data-ttu-id="b5c4c-104">Garantit que la clé du client offre une sécurité correcte.</span><span class="sxs-lookup"><span data-stu-id="b5c4c-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b5c4c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5c4c-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="b5c4c-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b5c4c-106">Return value</span></span>

<span data-ttu-id="b5c4c-107">Si la fonction réussit, la valeur de retour est `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="b5c4c-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="b5c4c-108">Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans *WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="b5c4c-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="b5c4c-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b5c4c-109">Requirements</span></span>  
 <span data-ttu-id="b5c4c-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5c4c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5c4c-111">**En-tête :** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="b5c4c-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="b5c4c-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b5c4c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c4c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5c4c-113">See also</span></span>

- [<span data-ttu-id="b5c4c-114">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="b5c4c-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
