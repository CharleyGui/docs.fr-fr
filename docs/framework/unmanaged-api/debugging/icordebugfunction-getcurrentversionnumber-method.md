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
ms.openlocfilehash: b47580022b98ea02584a94b3f74b3fd1c276f297
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212904"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="dae76-102">ICorDebugFunction::GetCurrentVersionNumber, méthode</span><span class="sxs-lookup"><span data-stu-id="dae76-102">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>
<span data-ttu-id="dae76-103">Obtient le numéro de version de la dernière modification apportée à la fonction représentée par cet objet ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="dae76-103">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dae76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dae76-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dae76-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="dae76-105">Parameters</span></span>  
 `pnCurrentVersion`  
 <span data-ttu-id="dae76-106">à Pointeur vers une valeur entière qui est le numéro de version de la dernière modification apportée à cette fonction.</span><span class="sxs-lookup"><span data-stu-id="dae76-106">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dae76-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="dae76-107">Remarks</span></span>  
 <span data-ttu-id="dae76-108">Le numéro de version de la dernière modification apportée à cette fonction peut être supérieur au numéro de version de la fonction elle-même.</span><span class="sxs-lookup"><span data-stu-id="dae76-108">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="dae76-109">Utilisez la méthode [ICorDebugFunction2 :: GetVersionNumber](icordebugfunction2-getversionnumber-method.md) ou la méthode [ICorDebugCode :: GetVersionNumber](icordebugcode-getversionnumber-method.md) pour récupérer le numéro de version de la fonction.</span><span class="sxs-lookup"><span data-stu-id="dae76-109">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dae76-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="dae76-110">Requirements</span></span>  
 <span data-ttu-id="dae76-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dae76-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dae76-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dae76-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dae76-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dae76-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dae76-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dae76-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
