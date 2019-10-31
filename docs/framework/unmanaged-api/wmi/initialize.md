---
title: Fonction Initialize (référence des API non managées)
description: La fonction Initialize effectue l’initialisation WMI.
ms.date: 11/06/2017
api_name:
- Initialize
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Initialize
helpviewer_keywords:
- Initialize function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b1f96b6285911b12d72ac136127d736b75d44023
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127393"
---
# <a name="initialize-function"></a><span data-ttu-id="17bbf-103">Fonction Initialize</span><span class="sxs-lookup"><span data-stu-id="17bbf-103">Initialize function</span></span>

<span data-ttu-id="17bbf-104">Effectue l’initialisation WMI.</span><span class="sxs-lookup"><span data-stu-id="17bbf-104">Performs WMI initialization.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="17bbf-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17bbf-105">Syntax</span></span>

```cpp
HRESULT Initialize(
   [in] boolean bAllowIManagementObjectQI
);
```

## <a name="parameters"></a><span data-ttu-id="17bbf-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17bbf-106">Parameters</span></span>

`bAllowIManagementObjectQI`

<span data-ttu-id="17bbf-107">[in] `true` pour indiquer que les appels à QueryInterface sur les objets WMI sont autorisés ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="17bbf-107">[in] `true` to indicate that calls to QueryInterface on WMI objects are allowed; `false` otherwise.</span></span>

## <a name="return-value"></a><span data-ttu-id="17bbf-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="17bbf-108">Return value</span></span>

<span data-ttu-id="17bbf-109">La fonction retourne toujours `S_OK` (0).</span><span class="sxs-lookup"><span data-stu-id="17bbf-109">The function always returns `S_OK` (0).</span></span>

## <a name="requirements"></a><span data-ttu-id="17bbf-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="17bbf-110">Requirements</span></span>

<span data-ttu-id="17bbf-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17bbf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="17bbf-112">**En-tête :** WMINet_Utils. def</span><span class="sxs-lookup"><span data-stu-id="17bbf-112">**Header:** WMINet_Utils.def</span></span>

<span data-ttu-id="17bbf-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="17bbf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="17bbf-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17bbf-114">See also</span></span>

- [<span data-ttu-id="17bbf-115">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="17bbf-115">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
