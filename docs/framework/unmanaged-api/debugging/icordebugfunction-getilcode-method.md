---
title: ICorDebugFunction::GetILCode, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetILCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetILCode
helpviewer_keywords:
- ICorDebugFunction::GetILCode method [.NET Framework debugging]
- GetILCode method [.NET Framework debugging]
ms.assetid: f794dd47-a7cd-47f6-96e9-a41a4dae8e72
topic_type:
- apiref
ms.openlocfilehash: 8c7be2d48a30a9f649c6d86e4edbc10085195b68
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213619"
---
# <a name="icordebugfunctiongetilcode-method"></a><span data-ttu-id="a404f-102">ICorDebugFunction::GetILCode, méthode</span><span class="sxs-lookup"><span data-stu-id="a404f-102">ICorDebugFunction::GetILCode Method</span></span>
<span data-ttu-id="a404f-103">Obtient l’instance de ICorDebugCode qui représente le code MSIL (Microsoft Intermediate Language) associé à cet objet ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="a404f-103">Gets the ICorDebugCode instance that represents the Microsoft intermediate language (MSIL) code associated with this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a404f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a404f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a404f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a404f-105">Parameters</span></span>  
 `ppCode`  
 <span data-ttu-id="a404f-106">à Pointeur vers l' `ICorDebugCode` instance, ou null, si la fonction n’a pas été compilée en MSIL.</span><span class="sxs-lookup"><span data-stu-id="a404f-106">[out] A pointer to the `ICorDebugCode` instance, or null, if the function was not compiled into MSIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a404f-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="a404f-107">Remarks</span></span>  
 <span data-ttu-id="a404f-108">Si modifier & continuer a été autorisé sur cette fonction, la `GetILCode` méthode obtiendra le code MSIL correspondant à la version modifiée du code de cette fonction dans le Common Language Runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="a404f-108">If Edit and Continue has been allowed on this function, the `GetILCode` method will get the MSIL code corresponding to this function's edited version of the code in the common language runtime (CLR).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a404f-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a404f-109">Requirements</span></span>  
 <span data-ttu-id="a404f-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a404f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a404f-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a404f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a404f-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a404f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a404f-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a404f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
