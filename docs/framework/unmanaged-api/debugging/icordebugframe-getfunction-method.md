---
title: ICorDebugFrame::GetFunction, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetFunction method [.NET Framework debugging]
ms.assetid: 879d2311-0ff1-4616-a8b3-959ea5868b2e
topic_type:
- apiref
ms.openlocfilehash: 9f9a6238057f56459eb8dca2375da412c3cd569d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690315"
---
# <a name="icordebugframegetfunction-method"></a><span data-ttu-id="c7282-102">ICorDebugFrame::GetFunction, méthode</span><span class="sxs-lookup"><span data-stu-id="c7282-102">ICorDebugFrame::GetFunction Method</span></span>

<span data-ttu-id="c7282-103">Obtient la fonction qui contient le code associé à ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="c7282-103">Gets the function that contains the code associated with this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7282-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7282-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction  **ppFunction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7282-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7282-105">Parameters</span></span>  

 `ppFunction`  
 <span data-ttu-id="c7282-106">à Pointeur vers l’adresse d’un objet ICorDebugFunction qui représente la fonction contenant le code associé à ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="c7282-106">[out] A pointer to the address of an ICorDebugFunction object that represents the function containing the code associated with this stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7282-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="c7282-107">Remarks</span></span>  

 <span data-ttu-id="c7282-108">La `GetFunction` méthode peut échouer si le frame n’est pas associé à une fonction particulière.</span><span class="sxs-lookup"><span data-stu-id="c7282-108">The `GetFunction` method may fail if the frame is not associated with any particular function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7282-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c7282-109">Requirements</span></span>  

 <span data-ttu-id="c7282-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7282-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7282-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7282-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7282-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7282-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7282-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7282-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
