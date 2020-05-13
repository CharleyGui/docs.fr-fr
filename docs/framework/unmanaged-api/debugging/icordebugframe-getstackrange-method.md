---
title: ICorDebugFrame::GetStackRange, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: cacdccf5c27cd1d115134d49e754b4ace2870b72
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205160"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="9ac8f-102">ICorDebugFrame::GetStackRange, méthode</span><span class="sxs-lookup"><span data-stu-id="9ac8f-102">ICorDebugFrame::GetStackRange Method</span></span>
<span data-ttu-id="9ac8f-103">Obtient la plage d’adresses absolues de ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="9ac8f-103">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ac8f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ac8f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ac8f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ac8f-105">Parameters</span></span>  
 `pStart`  
 <span data-ttu-id="9ac8f-106">à Pointeur vers un `CORDB_ADDRESS` qui spécifie l’adresse de départ du frame de pile représenté par cet `ICorDebugFrame` objet.</span><span class="sxs-lookup"><span data-stu-id="9ac8f-106">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="9ac8f-107">à Pointeur vers un `CORDB_ADDRESS` qui spécifie l’adresse de fin du frame de pile représenté par cet `ICorDebugFrame` objet.</span><span class="sxs-lookup"><span data-stu-id="9ac8f-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ac8f-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="9ac8f-108">Remarks</span></span>  
 <span data-ttu-id="9ac8f-109">La plage d’adresses de la pile est utile pour accolant ensemble de traces de pile entrelacées rassemblées à partir de plusieurs moteurs de débogage.</span><span class="sxs-lookup"><span data-stu-id="9ac8f-109">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="9ac8f-110">La plage numérique ne fournit aucune information sur le contenu du frame de pile.</span><span class="sxs-lookup"><span data-stu-id="9ac8f-110">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="9ac8f-111">Elle est explicite uniquement pour la comparaison des emplacements de frame de pile.</span><span class="sxs-lookup"><span data-stu-id="9ac8f-111">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ac8f-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9ac8f-112">Requirements</span></span>  
 <span data-ttu-id="9ac8f-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ac8f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ac8f-114">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ac8f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ac8f-115">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ac8f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ac8f-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ac8f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
