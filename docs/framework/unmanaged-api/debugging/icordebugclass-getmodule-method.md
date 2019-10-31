---
title: ICorDebugClass::GetModule, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
ms.openlocfilehash: 94f2d20816bfc28118877f52c04237c41b3859e3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125785"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="c43f2-102">ICorDebugClass::GetModule, méthode</span><span class="sxs-lookup"><span data-stu-id="c43f2-102">ICorDebugClass::GetModule Method</span></span>
<span data-ttu-id="c43f2-103">Obtient le module qui définit cette classe.</span><span class="sxs-lookup"><span data-stu-id="c43f2-103">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c43f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c43f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c43f2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c43f2-105">Parameters</span></span>  
 `pModule`  
 <span data-ttu-id="c43f2-106">à Pointeur vers l’adresse d’un objet ICorDebugModule qui représente le module dans lequel cette classe est définie.</span><span class="sxs-lookup"><span data-stu-id="c43f2-106">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c43f2-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="c43f2-107">Requirements</span></span>  
 <span data-ttu-id="c43f2-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c43f2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c43f2-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c43f2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c43f2-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c43f2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c43f2-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c43f2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
