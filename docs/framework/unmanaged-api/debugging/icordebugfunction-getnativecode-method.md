---
title: ICorDebugFunction::GetNativeCode, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
ms.openlocfilehash: e34dff2ebdb6e1ea56c2682b351c3e17a44416f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726312"
---
# <a name="icordebugfunctiongetnativecode-method"></a><span data-ttu-id="091d8-102">ICorDebugFunction::GetNativeCode, méthode</span><span class="sxs-lookup"><span data-stu-id="091d8-102">ICorDebugFunction::GetNativeCode Method</span></span>

<span data-ttu-id="091d8-103">Obtient le code natif pour la fonction qui est représentée par cette instance ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="091d8-103">Gets the native code for the function that is represented by this ICorDebugFunction instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="091d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="091d8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="091d8-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="091d8-105">Parameters</span></span>  

 `ppCode`  
 <span data-ttu-id="091d8-106">à Pointeur vers l’instance de ICorDebugCode qui représente le code natif pour cette fonction, ou null si cette fonction est du code MSIL (Microsoft Intermediate Language) qui n’a pas été compilé juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="091d8-106">[out] A pointer to the ICorDebugCode instance that represents the native code for this function, or null, if this function is Microsoft intermediate language (MSIL) code that has not been just-in-time (JIT) compiled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="091d8-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="091d8-107">Remarks</span></span>  

 <span data-ttu-id="091d8-108">Si la fonction représentée par cette `ICorDebugFunction` instance a été compilée juste-à-temps (JIT) plusieurs fois, comme dans le cas de types génériques, `GetNativeCode` retourne un objet de code natif aléatoire.</span><span class="sxs-lookup"><span data-stu-id="091d8-108">If the function that is represented by this `ICorDebugFunction` instance has been JIT-compiled more than once, as in the case of generic types, `GetNativeCode` returns a random native code object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="091d8-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="091d8-109">Requirements</span></span>  

 <span data-ttu-id="091d8-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="091d8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="091d8-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="091d8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="091d8-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="091d8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="091d8-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="091d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
