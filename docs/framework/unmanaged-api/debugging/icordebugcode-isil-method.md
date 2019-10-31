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
ms.openlocfilehash: 77e55c4c3644ac4bd76f5c92152f4ee86cf5fa9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125562"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="1fd41-102">ICorDebugCode::IsIL, méthode</span><span class="sxs-lookup"><span data-stu-id="1fd41-102">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="1fd41-103">Obtient une valeur qui indique si ce « ICorDebugCode » représente du code qui a été compilé en langage MSIL (Microsoft Intermediate Language).</span><span class="sxs-lookup"><span data-stu-id="1fd41-103">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="1fd41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fd41-104">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="1fd41-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1fd41-105">Parameters</span></span>

`pbIL`  
<span data-ttu-id="1fd41-106">[out] `true` si ce `ICorDebugCode` représente du code qui a été compilé en MSIL ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="1fd41-106">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="1fd41-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="1fd41-107">Requirements</span></span>

<span data-ttu-id="1fd41-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fd41-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="1fd41-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1fd41-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="1fd41-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1fd41-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="1fd41-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1fd41-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
