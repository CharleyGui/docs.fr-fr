---
title: ICorDebugCode::GetSize, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetSize method [.NET Framework debugging]
ms.assetid: 115bc6de-f5e2-4e8e-bb38-c7cf54045434
topic_type:
- apiref
ms.openlocfilehash: 2370ff5d99078ceb1ae0509e660c046dd7a1537e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125616"
---
# <a name="icordebugcodegetsize-method"></a><span data-ttu-id="e2cfe-102">ICorDebugCode::GetSize, méthode</span><span class="sxs-lookup"><span data-stu-id="e2cfe-102">ICorDebugCode::GetSize Method</span></span>

<span data-ttu-id="e2cfe-103">Obtient la taille, en octets, du code binaire représenté par ce « ICorDebugCode ».</span><span class="sxs-lookup"><span data-stu-id="e2cfe-103">Gets the size, in bytes, of the binary code represented by this "ICorDebugCode".</span></span>

## <a name="syntax"></a><span data-ttu-id="e2cfe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2cfe-104">Syntax</span></span>

```cpp
HRESULT GetSize (
    [out] ULONG32    *pcBytes
);
```

## <a name="parameters"></a><span data-ttu-id="e2cfe-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e2cfe-105">Parameters</span></span>

`pcBytes`  
<span data-ttu-id="e2cfe-106">à Pointeur vers la taille, en octets, du code binaire que cet objet `ICorDebugCode` représente.</span><span class="sxs-lookup"><span data-stu-id="e2cfe-106">[out] A pointer to the size, in bytes, of the binary code that this `ICorDebugCode` object represents.</span></span>

## <a name="requirements"></a><span data-ttu-id="e2cfe-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="e2cfe-107">Requirements</span></span>

<span data-ttu-id="e2cfe-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2cfe-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="e2cfe-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2cfe-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="e2cfe-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2cfe-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="e2cfe-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2cfe-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
