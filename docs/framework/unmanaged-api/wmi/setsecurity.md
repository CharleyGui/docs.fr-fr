---
title: Fonction SetSecurity (Référence API non gestion)
description: La fonction SetSecurity récupère le jeton d’imitation du fil actuel.
ms.date: 11/06/2017
api_name:
- SetSecurity
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SetSecurity
helpviewer_keywords:
- SetSecurity function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 809f6a95fdd6854b3a591b496877838c48d52199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176732"
---
# <a name="setsecurity-function"></a><span data-ttu-id="89340-103">SetSecurity, fonction</span><span class="sxs-lookup"><span data-stu-id="89340-103">SetSecurity function</span></span>

<span data-ttu-id="89340-104">Récupère le jeton d’emprunt d’identité associé au thread actif.</span><span class="sxs-lookup"><span data-stu-id="89340-104">Retrieves the impersonation token associated with the current thread.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="89340-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89340-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset,
   [out] HANDLE* pCurrentThreadToken
);
```

## <a name="parameters"></a><span data-ttu-id="89340-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89340-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="89340-107">[out] Lorsque la fonction revient, `boolean` contient un pointeur à un qui indique si le jeton doit être réinitialisé en appelant la fonction [ResetSecurity.](resetsecurity.md)</span><span class="sxs-lookup"><span data-stu-id="89340-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="89340-108">[out] Lorsque la fonction revient, contient un pointeur à la poignée du jeton d’imitation associé au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="89340-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="89340-109">Sa valeur `null` peut être s’il n’y a pas de jeton associé au fil actuel.</span><span class="sxs-lookup"><span data-stu-id="89340-109">Its value can be `null` if there is no token associated with the current thread.</span></span>

## <a name="return-value"></a><span data-ttu-id="89340-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="89340-110">Return value</span></span>

<span data-ttu-id="89340-111">Si la fonction réussit, `S_OK` la valeur de rendement est (0).</span><span class="sxs-lookup"><span data-stu-id="89340-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="89340-112">Si la fonction échoue, la valeur de retour est un code d’erreur non nul.</span><span class="sxs-lookup"><span data-stu-id="89340-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="89340-113">Pour obtenir des informations d’erreur étendues, appelez la fonction [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="89340-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="89340-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="89340-114">Requirements</span></span>

 <span data-ttu-id="89340-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89340-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="89340-116">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="89340-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="89340-117">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="89340-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="89340-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89340-118">See also</span></span>

- [<span data-ttu-id="89340-119">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="89340-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
