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
ms.openlocfilehash: a0abc7168ff7bffdbb835c1c1bc93de9df6e381c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694865"
---
# <a name="icordebugprocessreadmemory-method"></a><span data-ttu-id="4f665-102">ICorDebugProcess::ReadMemory, méthode</span><span class="sxs-lookup"><span data-stu-id="4f665-102">ICorDebugProcess::ReadMemory Method</span></span>

<span data-ttu-id="4f665-103">Lit une zone de mémoire spécifiée pour ce processus.</span><span class="sxs-lookup"><span data-stu-id="4f665-103">Reads a specified area of memory for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f665-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4f665-104">Syntax</span></span>  
  
```cpp  
HRESULT ReadMemory(  
    [in]  CORDB_ADDRESS address,
    [in]  DWORD size,  
    [out, size_is(size), length_is(size)] BYTE buffer[],  
    [out] SIZE_T *read);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f665-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4f665-105">Parameters</span></span>  

 `address`  
 <span data-ttu-id="4f665-106">dans `CORDB_ADDRESS` Valeur qui spécifie l’adresse de base de la mémoire à lire.</span><span class="sxs-lookup"><span data-stu-id="4f665-106">[in] A `CORDB_ADDRESS` value that specifies the base address of the memory to be read.</span></span>  
  
 `size`  
 <span data-ttu-id="4f665-107">dans Nombre d’octets à lire à partir de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4f665-107">[in] The number of bytes to be read from memory.</span></span>  
  
 `buffer`  
 <span data-ttu-id="4f665-108">à Mémoire tampon qui reçoit le contenu de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4f665-108">[out] A buffer that receives the contents of the memory.</span></span>  
  
 `read`  
 <span data-ttu-id="4f665-109">à Pointeur vers le nombre d’octets transférés dans la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="4f665-109">[out] A pointer to the number of bytes transferred into the specified buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f665-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="4f665-110">Remarks</span></span>  

 <span data-ttu-id="4f665-111">La `ReadMemory` méthode est principalement destinée à être utilisée par le débogage d’interopérabilité pour inspecter les régions de mémoire utilisées par la partie non managée de l’élément débogué.</span><span class="sxs-lookup"><span data-stu-id="4f665-111">The `ReadMemory` method is primarily intended to be used by interop debugging to inspect memory regions that are being used by the unmanaged portion of the debuggee.</span></span> <span data-ttu-id="4f665-112">Cette méthode peut également être utilisée pour lire le code MSIL (Microsoft Intermediate Language) et le code natif compilé juste-à-temps.</span><span class="sxs-lookup"><span data-stu-id="4f665-112">This method can also be used to read Microsoft intermediate language (MSIL) code and native JIT-compiled code.</span></span>  
  
 <span data-ttu-id="4f665-113">Tous les points d’arrêt managés seront supprimés des données retournées dans le `buffer` paramètre.</span><span class="sxs-lookup"><span data-stu-id="4f665-113">Any managed breakpoints will be removed from the data that is returned in the `buffer` parameter.</span></span> <span data-ttu-id="4f665-114">Aucun ajustement n’est effectué pour les points d’arrêt natifs définis par [ICorDebugProcess2 :: SetUnmanagedBreakpoint,](icordebugprocess2-setunmanagedbreakpoint-method.md).</span><span class="sxs-lookup"><span data-stu-id="4f665-114">No adjustments will be made for native breakpoints set by [ICorDebugProcess2::SetUnmanagedBreakpoint](icordebugprocess2-setunmanagedbreakpoint-method.md).</span></span>  
  
 <span data-ttu-id="4f665-115">Aucune mise en cache de la mémoire du processus n’est effectuée.</span><span class="sxs-lookup"><span data-stu-id="4f665-115">No caching of process memory is performed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f665-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4f665-116">Requirements</span></span>  

 <span data-ttu-id="4f665-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f665-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f665-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f665-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f665-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f665-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f665-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f665-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
