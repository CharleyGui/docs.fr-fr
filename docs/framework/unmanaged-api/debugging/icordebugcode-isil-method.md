---
title: ICorDebugCode::IsIL, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b7cbadbd1494d5e4d1488dd12296f4f90890127
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395494"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="3b0b1-102">ICorDebugCode::IsIL, méthode</span><span class="sxs-lookup"><span data-stu-id="3b0b1-102">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="3b0b1-103">Obtient une valeur qui indique si ce « ICorDebugCode » représente du code qui a été compilé en langage MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="3b0b1-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="3b0b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b0b1-104">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="3b0b1-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3b0b1-105">Parameters</span></span>

`pbIL`  
<span data-ttu-id="3b0b1-106">[out] `true` si cet `ICorDebugCode` représente du code qui a été compilé en MSIL ; dans le cas contraire, `false`.</span><span class="sxs-lookup"><span data-stu-id="3b0b1-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="3b0b1-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="3b0b1-107">Requirements</span></span>

<span data-ttu-id="3b0b1-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b0b1-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3b0b1-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b0b1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="3b0b1-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b0b1-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3b0b1-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b0b1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
