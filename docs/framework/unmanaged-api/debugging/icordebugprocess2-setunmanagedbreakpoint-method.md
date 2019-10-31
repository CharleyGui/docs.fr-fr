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
ms.openlocfilehash: ffab2762fd86e95c3272ca456039028e0897bc41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137180"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a><span data-ttu-id="82427-102">ICorDebugProcess2::SetUnmanagedBreakpoint, méthode</span><span class="sxs-lookup"><span data-stu-id="82427-102">ICorDebugProcess2::SetUnmanagedBreakpoint Method</span></span>
<span data-ttu-id="82427-103">Définit un point d’arrêt non managé au niveau de l’offset d’image native spécifié.</span><span class="sxs-lookup"><span data-stu-id="82427-103">Sets an unmanaged breakpoint at the specified native image offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82427-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82427-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82427-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82427-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="82427-106">dans Objet `CORDB_ADDRESS` qui spécifie le décalage de l’image native.</span><span class="sxs-lookup"><span data-stu-id="82427-106">[in] A `CORDB_ADDRESS` object that specifies the native image offset.</span></span>  
  
 `bufsize`  
 <span data-ttu-id="82427-107">dans Taille, en octets, du tableau de `buffer`.</span><span class="sxs-lookup"><span data-stu-id="82427-107">[in] The size, in bytes, of the `buffer` array.</span></span>  
  
 `buffer`  
 <span data-ttu-id="82427-108">à Tableau qui contient l’opcode qui est remplacé par le point d’arrêt.</span><span class="sxs-lookup"><span data-stu-id="82427-108">[out] An array that contains the opcode that is replaced by the breakpoint.</span></span>  
  
 `bufLen`  
 <span data-ttu-id="82427-109">à Pointeur vers le nombre d’octets retournés dans le tableau de `buffer`.</span><span class="sxs-lookup"><span data-stu-id="82427-109">[out] A pointer to the number of bytes returned in the `buffer` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82427-110">Notes</span><span class="sxs-lookup"><span data-stu-id="82427-110">Remarks</span></span>  
 <span data-ttu-id="82427-111">Si le décalage de l’image native se trouve dans le common language runtime (CLR), le point d’arrêt est ignoré.</span><span class="sxs-lookup"><span data-stu-id="82427-111">If the native image offset is within the common language runtime (CLR), the breakpoint will be ignored.</span></span> <span data-ttu-id="82427-112">Cela permet au CLR d’éviter la distribution d’un point d’arrêt hors bande, lorsque le point d’arrêt est défini par le débogueur.</span><span class="sxs-lookup"><span data-stu-id="82427-112">This allows the CLR to avoid dispatching an out-of-band breakpoint, when the breakpoint is set by the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82427-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="82427-113">Requirements</span></span>  
 <span data-ttu-id="82427-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82427-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82427-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82427-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82427-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82427-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82427-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82427-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
