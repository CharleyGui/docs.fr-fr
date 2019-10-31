---
title: ICorDebugProcess::IsTransitionStub, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 852c77be0dc8ef91933bacbbd3d6b3f5a69ae8c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139385"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="e5e79-102">ICorDebugProcess::IsTransitionStub, méthode</span><span class="sxs-lookup"><span data-stu-id="e5e79-102">ICorDebugProcess::IsTransitionStub Method</span></span>
<span data-ttu-id="e5e79-103">Obtient une valeur qui indique si une adresse se trouve à l’intérieur d’un stub qui entraîne une transition vers du code managé.</span><span class="sxs-lookup"><span data-stu-id="e5e79-103">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5e79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5e79-104">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e5e79-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e5e79-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="e5e79-106">dans Valeur `CORDB_ADDRESS` qui spécifie l’adresse en question.</span><span class="sxs-lookup"><span data-stu-id="e5e79-106">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="e5e79-107">à Pointeur vers une valeur booléenne qui est `true` si l’adresse spécifiée se trouve à l’intérieur d’un stub qui entraîne une transition vers du code managé ; sinon \*`pbTransitionStub` est `false`.</span><span class="sxs-lookup"><span data-stu-id="e5e79-107">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e5e79-108">Notes</span><span class="sxs-lookup"><span data-stu-id="e5e79-108">Remarks</span></span>  
 <span data-ttu-id="e5e79-109">La méthode `IsTransitionStub` peut être utilisée par le code d’exécution non managé pour décider quand retourner le contrôle pas à pas à l’exécution pas à pas managée.</span><span class="sxs-lookup"><span data-stu-id="e5e79-109">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="e5e79-110">Vous pouvez également identifier des stubs de transition en examinant les informations contenues dans le fichier exécutable portable (PE).</span><span class="sxs-lookup"><span data-stu-id="e5e79-110">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5e79-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="e5e79-111">Requirements</span></span>  
 <span data-ttu-id="e5e79-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5e79-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5e79-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e5e79-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5e79-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e5e79-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5e79-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5e79-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
