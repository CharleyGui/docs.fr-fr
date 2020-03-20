---
title: ICorDebugProcess::ReadMemory, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ReadMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ReadMemory
helpviewer_keywords:
- ReadMemory method [.NET Framework debugging]
- ICorDebugProcess::ReadMemory method [.NET Framework debugging]
ms.assetid: 28e4b2f6-9589-445c-be24-24a3306795e7
topic_type:
- apiref
ms.openlocfilehash: 383e3f8990a1f355c94ff5e9f9daa69bdbdd97bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178664"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="c3737-102">ICorDebugProcess::ReadMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="c3737-102">ICorDebugProcess::ReadMemory Method</span></span>
<span data-ttu-id="c3737-103">Lit une zone de mémoire spécifiée pour ce processus.</span><span class="sxs-lookup"><span data-stu-id="c3737-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3737-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3737-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3737-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3737-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="c3737-106">[dans] Une `CORDB_ADDRESS` valeur qui spécifie l’adresse de base de la mémoire à lire.</span><span class="sxs-lookup"><span data-stu-id="c3737-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="c3737-107">[dans] Le nombre d’octets à lire de mémoire.</span><span class="sxs-lookup"><span data-stu-id="c3737-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="c3737-108">[out] Un tampon qui reçoit le contenu de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="c3737-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="c3737-109">[out] Un pointeur sur le nombre d’octets transférés dans le tampon spécifié.</span><span class="sxs-lookup"><span data-stu-id="c3737-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3737-110">Notes </span><span class="sxs-lookup"><span data-stu-id="c3737-110">Remarks</span></span>  
 <span data-ttu-id="c3737-111">La `ReadMemory` méthode est principalement destinée à être utilisée par le débogage interop pour inspecter les régions de mémoire qui sont utilisées par la partie non gestion du débbuggee.</span><span class="sxs-lookup"><span data-stu-id="c3737-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="c3737-112">Cette méthode peut également être utilisée pour lire le code de langue intermédiaire Microsoft (MSIL) et le code CIT natif.</span><span class="sxs-lookup"><span data-stu-id="c3737-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="c3737-113">Tous les points d’arrêt gérés seront supprimés `buffer` des données retournées dans le paramètre.</span><span class="sxs-lookup"><span data-stu-id="c3737-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="c3737-114">Aucun ajustement ne sera apporté pour les points de rupture natifs définis par [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="c3737-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="c3737-115">Aucune mise en cache de la mémoire du processus n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="c3737-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3737-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c3737-116">Requirements</span></span>  
 <span data-ttu-id="c3737-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3737-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3737-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3737-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3737-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3737-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3737-120">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3737-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
