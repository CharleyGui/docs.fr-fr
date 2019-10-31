---
title: ICorDebugFunction::GetCurrentVersionNumber, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: 0530ba742a739003bfa33079ad75cb1e6f5f5e59
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124016"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="89b61-102">ICorDebugFunction::GetCurrentVersionNumber, méthode</span><span class="sxs-lookup"><span data-stu-id="89b61-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="89b61-103">Obtient le numéro de version de la dernière modification apportée à la fonction représentée par cet objet ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="89b61-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89b61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89b61-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89b61-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="89b61-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="89b61-106">à Pointeur vers une valeur entière qui est le numéro de version de la dernière modification apportée à cette fonction.</span><span class="sxs-lookup"><span data-stu-id="89b61-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89b61-107">Notes</span><span class="sxs-lookup"><span data-stu-id="89b61-107">Remarks</span></span>  
 <span data-ttu-id="89b61-108">Le numéro de version de la dernière modification apportée à cette fonction peut être supérieur au numéro de version de la fonction elle-même.</span><span class="sxs-lookup"><span data-stu-id="89b61-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="89b61-109">Utilisez la méthode [ICorDebugFunction2 :: GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) ou la méthode [ICorDebugCode :: GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) pour récupérer le numéro de version de la fonction.</span><span class="sxs-lookup"><span data-stu-id="89b61-109">Use either the [ICorDebugFunction2::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89b61-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="89b61-110">Requirements</span></span>  
 <span data-ttu-id="89b61-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89b61-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89b61-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="89b61-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="89b61-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="89b61-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="89b61-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89b61-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
