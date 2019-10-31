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
ms.openlocfilehash: 0a0680651eb192e2798ede00048599c5130e63f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107360"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="9663c-103">VerifyClientKey fonction)</span><span class="sxs-lookup"><span data-stu-id="9663c-103">VerifyClientKey function</span></span>
<span data-ttu-id="9663c-104">Garantit que la clé du client offre une sécurité correcte.</span><span class="sxs-lookup"><span data-stu-id="9663c-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9663c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9663c-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey(); 
```  

## <a name="return-value"></a><span data-ttu-id="9663c-106">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9663c-106">Return value</span></span>

<span data-ttu-id="9663c-107">Si la fonction est réussie, la valeur de retour est `ERROR_SUCCESS` (0).</span><span class="sxs-lookup"><span data-stu-id="9663c-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="9663c-108">Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro défini dans *winerror. h*.</span><span class="sxs-lookup"><span data-stu-id="9663c-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="9663c-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="9663c-109">Requirements</span></span>  
 <span data-ttu-id="9663c-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9663c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9663c-111">**En-tête :** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="9663c-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="9663c-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9663c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9663c-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9663c-113">See also</span></span>

- [<span data-ttu-id="9663c-114">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="9663c-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
