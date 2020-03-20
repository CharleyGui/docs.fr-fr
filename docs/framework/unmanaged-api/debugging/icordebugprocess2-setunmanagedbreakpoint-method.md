---
title: ICorDebugProcess2::SetUnmanagedBreakpoint, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: fb8b8f3e29c141e91587a4d0cdc81cdabccdbc9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178651"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="e9797-102">ICorDebugProcess2::SetUnmanagedBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="e9797-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="e9797-103">Définit un point de rupture non menté au décalage d’image indigène spécifié.</span><span class="sxs-lookup"><span data-stu-id="e9797-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9797-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9797-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9797-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e9797-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="e9797-106">[dans] Un `CORDB_ADDRESS` objet qui spécifie l’image indigène décalée.</span><span class="sxs-lookup"><span data-stu-id="e9797-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="e9797-107">[dans] La taille, dans les `buffer` octets, du tableau.</span><span class="sxs-lookup"><span data-stu-id="e9797-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e9797-108">[out] Un tableau qui contient l’opcode qui est remplacé par le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="e9797-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="e9797-109">[out] Un pointeur sur le nombre `buffer` d’octets retournés dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="e9797-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9797-110">Notes </span><span class="sxs-lookup"><span data-stu-id="e9797-110">Remarks</span></span>  
 <span data-ttu-id="e9797-111">Si le décalage d’image natif est dans l’heure courante de course de langue (CLR), le point d’arrêt sera ignoré.</span><span class="sxs-lookup"><span data-stu-id="e9797-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="e9797-112">Cela permet au CLR d’éviter d’envoyer un point de rupture hors bande, lorsque le point d’arrêt est réglé par le débbuggeur.</span><span class="sxs-lookup"><span data-stu-id="e9797-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9797-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e9797-113">Requirements</span></span>  
 <span data-ttu-id="e9797-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9797-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9797-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9797-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9797-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9797-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9797-117">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9797-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
