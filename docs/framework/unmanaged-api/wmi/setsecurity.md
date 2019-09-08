---
title: Fonction SetSecurity (référence des API non managées)
description: La fonction SetSecurity récupère le jeton d’emprunt d’identité du thread actuel.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 94c76213acb66116105d181e9961a33976047ee7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798237"
---
# <a name="setsecurity-function"></a><span data-ttu-id="680fe-103">SetSecurity fonction)</span><span class="sxs-lookup"><span data-stu-id="680fe-103">SetSecurity function</span></span>

<span data-ttu-id="680fe-104">Récupère le jeton d’emprunt d’identité associé au thread actif.</span><span class="sxs-lookup"><span data-stu-id="680fe-104">Retrieves the impersonation token associated with the current thread.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="680fe-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="680fe-105">Syntax</span></span>

```cpp
HRESULT SetSecurity (
   [out] boolean* pNeedToReset, 
   [out] HANDLE* pCurrentThreadToken
); 
```

## <a name="parameters"></a><span data-ttu-id="680fe-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="680fe-106">Parameters</span></span>

`pNeedToReset`\
<span data-ttu-id="680fe-107">à Quand la fonction retourne une valeur, contient un pointeur `boolean` vers une valeur qui indique si le jeton doit être réinitialisé en appelant la fonction [ResetSecurity](resetsecurity.md) .</span><span class="sxs-lookup"><span data-stu-id="680fe-107">[out] When the function returns, contains a pointer to a `boolean` that indicates whether the token should be reset by calling the [ResetSecurity](resetsecurity.md) function.</span></span>

`token`\
<span data-ttu-id="680fe-108">à Quand la fonction retourne une valeur, contient un pointeur vers le handle du jeton d’emprunt d’identité associé au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="680fe-108">[out] When the function returns, contains a pointer to the handle of the impersonation token associated with the current thread.</span></span> <span data-ttu-id="680fe-109">Sa valeur peut être `null` si aucun jeton n’est associé au thread actuel.</span><span class="sxs-lookup"><span data-stu-id="680fe-109">Its value can be `null` if there is no token associated with the current thread.</span></span> 

## <a name="return-value"></a><span data-ttu-id="680fe-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="680fe-110">Return value</span></span>

<span data-ttu-id="680fe-111">Si la fonction est réussie, la valeur de retour `S_OK` est (0).</span><span class="sxs-lookup"><span data-stu-id="680fe-111">If the function succeeds, the return value is `S_OK` (0).</span></span>

<span data-ttu-id="680fe-112">Si la fonction échoue, la valeur de retour est un code d’erreur différent de zéro.</span><span class="sxs-lookup"><span data-stu-id="680fe-112">If the function fails, the return value is a non-zero error code.</span></span> <span data-ttu-id="680fe-113">Pour afficher les informations d’erreur étendues, appelez la fonction [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="680fe-113">To get extended error information, call the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="680fe-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="680fe-114">Requirements</span></span>

 <span data-ttu-id="680fe-115">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="680fe-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="680fe-116">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="680fe-116">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="680fe-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="680fe-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="680fe-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="680fe-118">See also</span></span>

- [<span data-ttu-id="680fe-119">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="680fe-119">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
