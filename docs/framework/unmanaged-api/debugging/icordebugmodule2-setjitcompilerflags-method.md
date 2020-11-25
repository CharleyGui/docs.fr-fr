---
title: ICorDebugModule2::SetJITCompilerFlags, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJITCompilerFlags
helpviewer_keywords:
- ICorDebugModule2::SetJITCompilerFlags method [.NET Framework debugging]
- SetJITCompilerFlags method [.NET Framework debugging]
ms.assetid: ea574c84-c622-4589-9a14-b55771af5e06
topic_type:
- apiref
ms.openlocfilehash: 11ff430c426c93f1c2a5c0582495e089a33995fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709802"
---
# <a name="icordebugmodule2setjitcompilerflags-method"></a><span data-ttu-id="1bf40-102">ICorDebugModule2::SetJITCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="1bf40-102">ICorDebugModule2::SetJITCompilerFlags Method</span></span>

<span data-ttu-id="1bf40-103">Définit les indicateurs qui contrôlent la compilation juste-à-temps (JIT) de ce ICorDebugModule2.</span><span class="sxs-lookup"><span data-stu-id="1bf40-103">Sets the flags that control the just-in-time (JIT) compilation of this ICorDebugModule2.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bf40-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bf40-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJITCompilerFlags (  
    [in] DWORD dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bf40-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1bf40-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="1bf40-106">dans Combinaison d’opérations de bits des valeurs d’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="1bf40-106">[in] A bitwise combination of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bf40-107">Remarques</span><span class="sxs-lookup"><span data-stu-id="1bf40-107">Remarks</span></span>  

 <span data-ttu-id="1bf40-108">Si la `dwFlags` valeur n’est pas valide, la `SetJITCompilerFlags` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="1bf40-108">If the `dwFlags` value is invalid, the `SetJITCompilerFlags` method will fail.</span></span>  
  
 <span data-ttu-id="1bf40-109">La `SetJITCompilerFlags` méthode peut être appelée uniquement à partir du rappel [ICorDebugManagedCallback :: LoadModule](icordebugmanagedcallback-loadmodule-method.md) pour ce module.</span><span class="sxs-lookup"><span data-stu-id="1bf40-109">The `SetJITCompilerFlags` method can be called only from within the [ICorDebugManagedCallback::LoadModule](icordebugmanagedcallback-loadmodule-method.md) callback for this module.</span></span> <span data-ttu-id="1bf40-110">Toute tentative de l’appeler une fois que le `ICorDebugManagedCallback::LoadModule` rappel a été remis échouera.</span><span class="sxs-lookup"><span data-stu-id="1bf40-110">Attempts to call it after the `ICorDebugManagedCallback::LoadModule` callback has been delivered will fail.</span></span>  
  
 <span data-ttu-id="1bf40-111">Modifier & Continuer n’est pas pris en charge sur les plateformes 64 bits ou Win9x.</span><span class="sxs-lookup"><span data-stu-id="1bf40-111">Edit and Continue is not supported on 64-bit or Win9x platforms.</span></span> <span data-ttu-id="1bf40-112">Par conséquent, si vous appelez la `SetJITCompilerFlags` méthode sur l’une de ces deux plateformes avec l’indicateur CORDEBUG_JIT_ENABLE_ENC défini dans `dwFlags` , la `SetJITCompilerFlags` méthode et toutes les méthodes spécifiques à modifier & continuer, telles que [ICorDebugModule2 :: ApplyChanges](icordebugmodule2-applychanges-method.md), échouent.</span><span class="sxs-lookup"><span data-stu-id="1bf40-112">Therefore, if you call the `SetJITCompilerFlags` method on either of these two platforms with the CORDEBUG_JIT_ENABLE_ENC flag set in `dwFlags`, the `SetJITCompilerFlags` method and all methods specific to Edit and Continue, such as [ICorDebugModule2::ApplyChanges](icordebugmodule2-applychanges-method.md), will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bf40-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1bf40-113">Requirements</span></span>  

 <span data-ttu-id="1bf40-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bf40-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bf40-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bf40-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bf40-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bf40-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bf40-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bf40-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
