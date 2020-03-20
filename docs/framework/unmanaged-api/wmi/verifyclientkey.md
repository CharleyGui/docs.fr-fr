---
title: Fonction VerifyClientKey (référence API non gestion)
description: La fonction VerifyClientKey garantit que la clé client a la sécurité correcte.
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
ms.openlocfilehash: ebb794240494deb0c831b50e95461ec52017a215
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176706"
---
# <a name="verifyclientkey-function"></a><span data-ttu-id="576c8-103">Fonction VerifyClientKey</span><span class="sxs-lookup"><span data-stu-id="576c8-103">VerifyClientKey function</span></span>
<span data-ttu-id="576c8-104">Garantit que la clé du client offre une sécurité correcte.</span><span class="sxs-lookup"><span data-stu-id="576c8-104">Ensures that the client key has the correct security.</span></span>  
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="576c8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="576c8-105">Syntax</span></span>  
  
```cpp  
LONG VerifyClientKey();
```  

## <a name="return-value"></a><span data-ttu-id="576c8-106">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="576c8-106">Return value</span></span>

<span data-ttu-id="576c8-107">Si la fonction réussit, `ERROR_SUCCESS` la valeur de rendement est (0).</span><span class="sxs-lookup"><span data-stu-id="576c8-107">If the function succeeds, the return value is `ERROR_SUCCESS` (0).</span></span>

<span data-ttu-id="576c8-108">Si la fonction échoue, la valeur de retour est un code d’erreur non zéro défini dans *WinError.h*.</span><span class="sxs-lookup"><span data-stu-id="576c8-108">If the function fails, the return value is a non-zero error code defined in *WinError.h*.</span></span>

## <a name="requirements"></a><span data-ttu-id="576c8-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="576c8-109">Requirements</span></span>  
 <span data-ttu-id="576c8-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="576c8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="576c8-111">**En-tête:** WMINet_Utils.def</span><span class="sxs-lookup"><span data-stu-id="576c8-111">**Header:** WMINet_Utils.def</span></span>  
  
 <span data-ttu-id="576c8-112">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="576c8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="576c8-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="576c8-113">See also</span></span>

- [<span data-ttu-id="576c8-114">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="576c8-114">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
