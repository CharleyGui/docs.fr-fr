---
title: ICorDebugAssembly::GetProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::GetProcess
helpviewer_keywords:
- ICorDebugAssembly::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugAssembly interface [.NET Framework debugging]
ms.assetid: ea52be06-0a16-4f57-afca-4287d72e76c4
topic_type:
- apiref
ms.openlocfilehash: 49b234b065eb66dc2ec0bc7e991117c5b54a92f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196346"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="b2418-102">ICorDebugAssembly::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="b2418-102">ICorDebugAssembly::GetProcess Method</span></span>
<span data-ttu-id="b2418-103">Obtient un pointeur d’interface vers le processus dans lequel cette instance ICorDebugAssembly est exécutée.</span><span class="sxs-lookup"><span data-stu-id="b2418-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2418-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2418-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2418-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2418-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="b2418-106">à Pointeur vers une interface ICorDebugProcess qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="b2418-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2418-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="b2418-107">Requirements</span></span>  
 <span data-ttu-id="b2418-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2418-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2418-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2418-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2418-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2418-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2418-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2418-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
