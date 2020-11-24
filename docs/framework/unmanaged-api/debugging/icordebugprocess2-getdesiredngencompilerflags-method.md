---
title: ICorDebugProcess2::GetDesiredNGENCompilerFlags, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::GetDesiredNGENCompilerFlags method [.NET Framework debugging]
- GetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: fc834580-3a90-4315-95d2-349b6bb7d059
topic_type:
- apiref
ms.openlocfilehash: 223f66639ae24f2a54f1bc936f4a0765573356eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673889"
---
# <a name="icordebugprocess2getdesiredngencompilerflags-method"></a><span data-ttu-id="a7f4d-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="a7f4d-102">ICorDebugProcess2::GetDesiredNGENCompilerFlags Method</span></span>

<span data-ttu-id="a7f4d-103">Obtient les paramètres d’indicateur de compilateur en cours que le common language runtime (CLR) utilise pour sélectionner l’image précompilée (autrement dit, native) appropriée à charger dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="a7f4d-103">Gets the current compiler flag settings that the common language runtime (CLR) uses to select the correct precompiled (that is, native) image to be loaded into this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7f4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7f4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDesiredNGENCompilerFlags (  
    [out] DWORD   *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7f4d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a7f4d-105">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="a7f4d-106">à Pointeur vers une combinaison d’opérations de bits des valeurs d’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) utilisées pour sélectionner l’image précompilée appropriée à charger.</span><span class="sxs-lookup"><span data-stu-id="a7f4d-106">[out] A pointer to a bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values that are used to select the correct precompiled image to be loaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7f4d-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="a7f4d-107">Remarks</span></span>  

 <span data-ttu-id="a7f4d-108">Utilisez la méthode [ICorDebugProcess2 :: SetDesiredNGENCompilerFlags,](icordebugprocess2-setdesiredngencompilerflags-method.md) pour définir les indicateurs que le CLR utilisera pour sélectionner l’image précompilée appropriée à charger.</span><span class="sxs-lookup"><span data-stu-id="a7f4d-108">Use the [ICorDebugProcess2::SetDesiredNGENCompilerFlags](icordebugprocess2-setdesiredngencompilerflags-method.md) method to set the flags that the CLR will use to select the correct pre-compiled image to load.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7f4d-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a7f4d-109">Requirements</span></span>  

 <span data-ttu-id="a7f4d-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7f4d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7f4d-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7f4d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7f4d-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7f4d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7f4d-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7f4d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
