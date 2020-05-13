---
title: ICorDebugFunction::GetModule, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetModule
helpviewer_keywords:
- ICorDebugFunction::GetModule method [.NET Framework debugging]
- GetModule method, ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 5031a5d3-2564-412a-9007-e36d4631308a
topic_type:
- apiref
ms.openlocfilehash: 41ad10fecca2ba1831d9e0d1120d3d1be0be92ad
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212956"
---
# <a name="icordebugfunctiongetmodule-method"></a><span data-ttu-id="5777c-102">ICorDebugFunction::GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="5777c-102">ICorDebugFunction::GetModule Method</span></span>
<span data-ttu-id="5777c-103">Obtient le module dans lequel cette fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="5777c-103">Gets the module in which this function is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5777c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5777c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5777c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5777c-105">Parameters</span></span>  
 `ppModule`  
 <span data-ttu-id="5777c-106">à Pointeur vers l’adresse d’un objet ICorDebugModule qui représente le module dans lequel cette fonction est définie.</span><span class="sxs-lookup"><span data-stu-id="5777c-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this function is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5777c-107">Spécifications</span><span class="sxs-lookup"><span data-stu-id="5777c-107">Requirements</span></span>  
 <span data-ttu-id="5777c-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5777c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5777c-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5777c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5777c-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5777c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5777c-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5777c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
