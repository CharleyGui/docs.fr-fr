---
title: ICorDebugCode::GetVersionNumber, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
ms.openlocfilehash: 646c20ca1b78ff0ce513b8a3c9b578c3b1b9a696
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125604"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="a690d-102">ICorDebugCode::GetVersionNumber, méthode</span><span class="sxs-lookup"><span data-stu-id="a690d-102">ICorDebugCode::GetVersionNumber Method</span></span>

<span data-ttu-id="a690d-103">Obtient le nombre de base 1 qui identifie la version du code que ce « ICorDebugCode » représente.</span><span class="sxs-lookup"><span data-stu-id="a690d-103">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>

## <a name="syntax"></a><span data-ttu-id="a690d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a690d-104">Syntax</span></span>

```cpp
HRESULT GetVersionNumber (
    [out] ULONG32    *nVersion
);
```

## <a name="parameters"></a><span data-ttu-id="a690d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a690d-105">Parameters</span></span>

 `nVersion`  
 <span data-ttu-id="a690d-106">à Pointeur vers le numéro de version du code.</span><span class="sxs-lookup"><span data-stu-id="a690d-106">[out] A pointer to the version number of the code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a690d-107">Notes</span><span class="sxs-lookup"><span data-stu-id="a690d-107">Remarks</span></span>

 <span data-ttu-id="a690d-108">Le numéro de version est incrémenté chaque fois qu’une opération de modification et de continuation (EnC) est effectuée sur le code.</span><span class="sxs-lookup"><span data-stu-id="a690d-108">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>

## <a name="requirements"></a><span data-ttu-id="a690d-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="a690d-109">Requirements</span></span>

 <span data-ttu-id="a690d-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a690d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a690d-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a690d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a690d-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a690d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a690d-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a690d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
