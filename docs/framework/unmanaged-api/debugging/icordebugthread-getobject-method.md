---
title: ICorDebugThread::GetObject, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3695f150797e6a59a2fb1d58c99f233a35d687ce
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771847"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="08cad-102">ICorDebugThread::GetObject, méthode</span><span class="sxs-lookup"><span data-stu-id="08cad-102">ICorDebugThread::GetObject Method</span></span>
<span data-ttu-id="08cad-103">Obtient un pointeur d’interface vers le thread de common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="08cad-103">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08cad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08cad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08cad-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="08cad-105">Parameters</span></span>  
 `ppObject`  
 <span data-ttu-id="08cad-106">[out] Pointeur vers l’adresse d’un objet d’interface ICorDebugValue qui représente le thread de CLR.</span><span class="sxs-lookup"><span data-stu-id="08cad-106">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08cad-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="08cad-107">Requirements</span></span>  
 <span data-ttu-id="08cad-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08cad-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08cad-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08cad-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08cad-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08cad-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08cad-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08cad-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08cad-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08cad-112">See also</span></span>

- <xref:System.Threading.Thread>
