---
title: ICorDebugThread::GetHandle, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetHandle method [.NET Framework debugging]
ms.assetid: 172ef8c4-2ead-4cfc-bd2e-dee4fb7191cd
topic_type:
- apiref
ms.openlocfilehash: 16aafa439fc81c3606f98ca2ba860316ec46e0db
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379736"
---
# <a name="icordebugthreadgethandle-method"></a><span data-ttu-id="ce225-102">ICorDebugThread::GetHandle, méthode</span><span class="sxs-lookup"><span data-stu-id="ce225-102">ICorDebugThread::GetHandle Method</span></span>
<span data-ttu-id="ce225-103">Obtient le handle actuel pour la partie active de ce ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="ce225-103">Gets the current handle for the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce225-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce225-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle (  
    [out] HTHREAD *phThreadHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce225-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ce225-105">Parameters</span></span>  
 `phThreadHandle`  
 <span data-ttu-id="ce225-106">à Pointeur vers un HTHREAD qui est le handle de la partie active de ce thread.</span><span class="sxs-lookup"><span data-stu-id="ce225-106">[out] A pointer to an HTHREAD that is the handle of the active part of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce225-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="ce225-107">Remarks</span></span>  
 <span data-ttu-id="ce225-108">Le handle peut changer à mesure que le processus s’exécute et peut être différent pour différentes parties du thread.</span><span class="sxs-lookup"><span data-stu-id="ce225-108">The handle may change as the process executes, and may be different for different parts of the thread.</span></span>  
  
 <span data-ttu-id="ce225-109">Ce descripteur appartient à l’API de débogage.</span><span class="sxs-lookup"><span data-stu-id="ce225-109">This handle is owned by the debugging API.</span></span> <span data-ttu-id="ce225-110">Le débogueur doit le dupliquer avant de l’utiliser.</span><span class="sxs-lookup"><span data-stu-id="ce225-110">The debugger should duplicate it before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce225-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ce225-111">Requirements</span></span>  
 <span data-ttu-id="ce225-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce225-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce225-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce225-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce225-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce225-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce225-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce225-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
