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
ms.openlocfilehash: e8662535fb6f1aa812130d96e67678baa3c41a52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734034"
---
# <a name="icordebugassemblygetprocess-method"></a><span data-ttu-id="c371f-102">ICorDebugAssembly::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="c371f-102">ICorDebugAssembly::GetProcess Method</span></span>

<span data-ttu-id="c371f-103">Obtient un pointeur d’interface vers le processus dans lequel cette instance ICorDebugAssembly est exécutée.</span><span class="sxs-lookup"><span data-stu-id="c371f-103">Gets an interface pointer to the process in which this ICorDebugAssembly instance is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c371f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c371f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c371f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c371f-105">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="c371f-106">à Pointeur vers une interface ICorDebugProcess qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="c371f-106">[out] A pointer to an ICorDebugProcess interface that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c371f-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c371f-107">Requirements</span></span>  

 <span data-ttu-id="c371f-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c371f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c371f-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c371f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c371f-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c371f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c371f-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c371f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
