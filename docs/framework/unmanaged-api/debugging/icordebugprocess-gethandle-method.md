---
title: ICorDebugProcess::GetHandle, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: 87b7b7381ef53f7e2abebc053b5c9f87f94d96c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695060"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="32489-102">ICorDebugProcess::GetHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="32489-102">ICorDebugProcess::GetHandle Method</span></span>

<span data-ttu-id="32489-103">Obtient un handle pour le processus.</span><span class="sxs-lookup"><span data-stu-id="32489-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32489-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32489-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32489-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="32489-105">Parameters</span></span>  

 `phProcessHandle`  
 <span data-ttu-id="32489-106">à Pointeur vers `HPROCESS` qui est le handle du processus.</span><span class="sxs-lookup"><span data-stu-id="32489-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32489-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="32489-107">Remarks</span></span>  

 <span data-ttu-id="32489-108">Le handle récupéré appartient à l’interface de débogage.</span><span class="sxs-lookup"><span data-stu-id="32489-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="32489-109">Le débogueur doit dupliquer le handle avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="32489-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32489-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="32489-110">Requirements</span></span>  

 <span data-ttu-id="32489-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32489-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32489-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32489-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32489-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32489-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32489-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32489-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
