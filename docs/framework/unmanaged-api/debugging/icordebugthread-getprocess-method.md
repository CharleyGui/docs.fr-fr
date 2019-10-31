---
title: ICorDebugThread::GetProcess, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
ms.openlocfilehash: 8928e22b70af0360660c30289ee999a3e4c5e99e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133476"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="e65cb-102">ICorDebugThread::GetProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="e65cb-102">ICorDebugThread::GetProcess Method</span></span>
<span data-ttu-id="e65cb-103">Obtient un pointeur d’interface vers le processus dont ce ICorDebugThread forme un composant.</span><span class="sxs-lookup"><span data-stu-id="e65cb-103">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e65cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e65cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e65cb-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e65cb-105">Parameters</span></span>  
 `ppProcess`  
 <span data-ttu-id="e65cb-106">à Pointeur vers l’adresse d’un objet d’interface ICorDebugProcess qui représente le processus.</span><span class="sxs-lookup"><span data-stu-id="e65cb-106">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e65cb-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="e65cb-107">Requirements</span></span>  
 <span data-ttu-id="e65cb-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e65cb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e65cb-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e65cb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e65cb-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e65cb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e65cb-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e65cb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
