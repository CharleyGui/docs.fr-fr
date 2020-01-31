---
title: ICorDebugVirtualUnwinder::GetContext, méthode
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: ff5e5bdd66ec44a0931b51212f07485718507576
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790842"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a><span data-ttu-id="7c53b-102">ICorDebugVirtualUnwinder::GetContext, méthode</span><span class="sxs-lookup"><span data-stu-id="7c53b-102">ICorDebugVirtualUnwinder::GetContext Method</span></span>
<span data-ttu-id="7c53b-103">Obtient le contexte actuel de ce dérouleur.</span><span class="sxs-lookup"><span data-stu-id="7c53b-103">Gets the current context of this unwinder.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c53b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c53b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c53b-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="7c53b-105">Parameters</span></span>  
 `contextFlags`  
 <span data-ttu-id="7c53b-106">[in] Indicateurs spécifiant les parties du contexte à retourner (définition contenue dans WinNT.h).</span><span class="sxs-lookup"><span data-stu-id="7c53b-106">[in] Flags that specify which parts of the context to return (defined in WinNT.h).</span></span>  
  
 `cbContextBuf`  
 <span data-ttu-id="7c53b-107">[in] Nombre d'octets dans `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="7c53b-107">[in] The number of bytes in `contextBuf`.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="7c53b-108">[out] Pointeur vers le nombre d'octets réellement écrits dans `contextBuf`.</span><span class="sxs-lookup"><span data-stu-id="7c53b-108">[out] A pointer to the number of bytes actually written to `contextBuf`.</span></span>  
  
 `contextBuf`  
 <span data-ttu-id="7c53b-109">[out] Tableau d'octets contenant le contexte actuel de ce dérouleur.</span><span class="sxs-lookup"><span data-stu-id="7c53b-109">[out] A byte array that contains the current context of this unwinder.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c53b-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7c53b-110">Return Value</span></span>  
 <span data-ttu-id="7c53b-111">Toute valeur HRESULT indiquant un échec reçue par mscordbi est considérée comme irrécupérable et forcent les API ICorDebug à retourner `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="7c53b-111">Any failing HRESULT value received by mscordbi is considered fatal and will cause ICorDebug APIs to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c53b-112">Notes</span><span class="sxs-lookup"><span data-stu-id="7c53b-112">Remarks</span></span>  
 <span data-ttu-id="7c53b-113">Vous définissez la valeur initiale de l’argument `contextBuf` sur la mémoire tampon de contexte retournée en appelant la méthode [ICorDebugStackWalk :: GetContext](icordebugstackwalk-getcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7c53b-113">You set the initial value of the `contextBuf` argument to the context buffer returned by calling the [ICorDebugStackWalk::GetContext](icordebugstackwalk-getcontext-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c53b-114">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7c53b-114">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="7c53b-115">Le déroulement ne pouvant restaurer qu'un sous-ensemble des registres, par exemple les registres non volatiles, le contexte peut différer de l'état du registre au moment de l'appel de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7c53b-115">Because unwinding may only restore a subset of the registers, such as the non-volatile registers only, the context may not exactly match the register state at the time of the actual method call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c53b-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="7c53b-116">Requirements</span></span>  
 <span data-ttu-id="7c53b-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c53b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c53b-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c53b-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c53b-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c53b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c53b-120">**Versions du .NET Framework :** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c53b-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c53b-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c53b-121">See also</span></span>

- [<span data-ttu-id="7c53b-122">ICorDebugMemoryBuffer, interface</span><span class="sxs-lookup"><span data-stu-id="7c53b-122">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="7c53b-123">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="7c53b-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
