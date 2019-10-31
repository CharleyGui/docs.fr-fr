---
title: ICorDebugThread::GetActiveChain, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveChain
helpviewer_keywords:
- ICorDebugThread::GetActiveChain method [.NET Framework debugging]
- GetActiveChain method [.NET Framework debugging]
ms.assetid: f50de1f7-40ef-4949-b542-1d9a61f7bfef
topic_type:
- apiref
ms.openlocfilehash: 99a617ef21ee3c3319b1ebe7d3ab8367659b6ef8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133555"
---
# <a name="icordebugthreadgetactivechain-method"></a><span data-ttu-id="39072-102">ICorDebugThread::GetActiveChain, méthode</span><span class="sxs-lookup"><span data-stu-id="39072-102">ICorDebugThread::GetActiveChain Method</span></span>
<span data-ttu-id="39072-103">Obtient un pointeur d’interface vers la chaîne de pile active (la plus récente) sur cet objet ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="39072-103">Gets an interface pointer to the active (most recent) stack chain on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39072-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="39072-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveChain (  
    [out] ICorDebugChain **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="39072-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="39072-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="39072-106">à Pointeur vers l’adresse d’un objet ICorDebugChain qui représente la chaîne de pile.</span><span class="sxs-lookup"><span data-stu-id="39072-106">[out] A pointer to the address of an ICorDebugChain object that represents the stack chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39072-107">Notes</span><span class="sxs-lookup"><span data-stu-id="39072-107">Remarks</span></span>  
 <span data-ttu-id="39072-108">Le paramètre `ppChain` a la valeur null si aucune chaîne de pile n’est actuellement active.</span><span class="sxs-lookup"><span data-stu-id="39072-108">The `ppChain` parameter is null if no stack chain is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39072-109">spécifications</span><span class="sxs-lookup"><span data-stu-id="39072-109">Requirements</span></span>  
 <span data-ttu-id="39072-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39072-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39072-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="39072-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="39072-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="39072-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="39072-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39072-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
