---
title: Fonction ResetSecurity (Référence API non gestion)
description: La fonction ResetSecurity attribue un jeton d’imitation au fil actuel.
ms.date: 11/06/2017
api_name:
- ResetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ResetSecurity
helpviewer_keywords:
- ResetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: ce74494455c6cc7fe382a4ea4ef2ff0c4e98c61b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174860"
---
# <a name="resetsecurity-function"></a><span data-ttu-id="40c0e-103">ResetSecurity, fonction</span><span class="sxs-lookup"><span data-stu-id="40c0e-103">ResetSecurity function</span></span>
<span data-ttu-id="40c0e-104">Assigne le jeton d’emprunt d’identité fourni au thread actif.</span><span class="sxs-lookup"><span data-stu-id="40c0e-104">Assigns the supplied impersonation token to the current thread.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="40c0e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40c0e-105">Syntax</span></span>  
  
```cpp  
HRESULT ResetSecurity (
   [in] HANDLE token
);
```  

## <a name="parameters"></a><span data-ttu-id="40c0e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="40c0e-106">Parameters</span></span>

`token`  
<span data-ttu-id="40c0e-107">[dans] Le jeton d’imitation pour s’associer au fil actuel.</span><span class="sxs-lookup"><span data-stu-id="40c0e-107">[in] The impersonation token to associate with the current thread.</span></span> <span data-ttu-id="40c0e-108">Sa valeur peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="40c0e-108">Its value can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="40c0e-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="40c0e-109">Return value</span></span>

<span data-ttu-id="40c0e-110">Si la fonction réussit, `S_OK` la valeur de rendement est (0).</span><span class="sxs-lookup"><span data-stu-id="40c0e-110">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="40c0e-111">Si la fonction échoue, la valeur de retour est un code d’erreur non nul.</span><span class="sxs-lookup"><span data-stu-id="40c0e-111">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="40c0e-112">Pour obtenir des informations d’erreur étendues, appelez la fonction [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="40c0e-112">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="40c0e-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="40c0e-113">Requirements</span></span>  
 <span data-ttu-id="40c0e-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40c0e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c0e-115">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="40c0e-115">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="40c0e-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="40c0e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c0e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40c0e-117">See also</span></span>

- [<span data-ttu-id="40c0e-118">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="40c0e-118">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
