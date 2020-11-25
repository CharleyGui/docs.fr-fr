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
ms.openlocfilehash: 14579d4c84be9bb225e618715b3a7d45ccaac0a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728145"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="35f76-102">ICorDebugFunction::GetCurrentVersionNumber, méthode</span><span class="sxs-lookup"><span data-stu-id="35f76-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>

<span data-ttu-id="35f76-103">Obtient le numéro de version de la dernière modification apportée à la fonction représentée par cet objet ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="35f76-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35f76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35f76-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35f76-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35f76-105">Parameters</span></span>  

 `pnCurrentVersion`  
 <span data-ttu-id="35f76-106">à Pointeur vers une valeur entière qui est le numéro de version de la dernière modification apportée à cette fonction.</span><span class="sxs-lookup"><span data-stu-id="35f76-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35f76-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="35f76-107">Remarks</span></span>  

 <span data-ttu-id="35f76-108">Le numéro de version de la dernière modification apportée à cette fonction peut être supérieur au numéro de version de la fonction elle-même.</span><span class="sxs-lookup"><span data-stu-id="35f76-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="35f76-109">Utilisez la méthode [ICorDebugFunction2 :: GetVersionNumber](icordebugfunction2-getversionnumber-method.md) ou la méthode [ICorDebugCode :: GetVersionNumber](icordebugcode-getversionnumber-method.md) pour récupérer le numéro de version de la fonction.</span><span class="sxs-lookup"><span data-stu-id="35f76-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35f76-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="35f76-110">Requirements</span></span>  

 <span data-ttu-id="35f76-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35f76-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35f76-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35f76-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35f76-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35f76-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35f76-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35f76-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
