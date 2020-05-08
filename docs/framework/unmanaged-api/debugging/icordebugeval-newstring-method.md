---
title: ICorDebugEval::NewString, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: b263fed7db5cb2ef687da45f8cbc99a02e1e3ea2
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976133"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="179f7-102">ICorDebugEval::NewString, méthode</span><span class="sxs-lookup"><span data-stu-id="179f7-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="179f7-103">Alloue une nouvelle instance de chaîne avec le contenu spécifié.</span><span class="sxs-lookup"><span data-stu-id="179f7-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="179f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="179f7-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="179f7-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="179f7-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="179f7-106">dans Pointeur vers le contenu de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="179f7-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="179f7-107">Notes </span><span class="sxs-lookup"><span data-stu-id="179f7-107">Remarks</span></span>  
 <span data-ttu-id="179f7-108">La chaîne est toujours créée dans le domaine d’application dans lequel le thread est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="179f7-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="179f7-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="179f7-109">Requirements</span></span>  
 <span data-ttu-id="179f7-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="179f7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="179f7-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="179f7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="179f7-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="179f7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="179f7-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="179f7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
