---
title: ICLRDataTarget::GetThreadContext, méthode
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetThreadContext
helpviewer_keywords:
- ICLRDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICLRDataTarget interface [.NET Framework debugging]
ms.assetid: b9d8c3b5-3a2e-4225-95d4-dd052c4532c3
topic_type:
- apiref
ms.openlocfilehash: b5f6a830cbe601443f03cd91a356c7e49450e7f3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793727"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="38935-102">ICLRDataTarget::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="38935-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="38935-103">Obtient le contexte d’exécution actuel du thread donné dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="38935-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="38935-104">Cette méthode est appelée par les services d’accès aux données common language runtime.</span><span class="sxs-lookup"><span data-stu-id="38935-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38935-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38935-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]   
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="38935-106">Parameters</span><span class="sxs-lookup"><span data-stu-id="38935-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="38935-107">dans Identificateur de système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="38935-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="38935-108">dans Indicateurs qui spécifient les parties du contexte à retourner.</span><span class="sxs-lookup"><span data-stu-id="38935-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="38935-109">L’implémentation renverra au moins ces parties du contexte.</span><span class="sxs-lookup"><span data-stu-id="38935-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="38935-110">dans Taille du contexte.</span><span class="sxs-lookup"><span data-stu-id="38935-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="38935-111">à Pointeur vers une mémoire tampon dans laquelle placer le contexte.</span><span class="sxs-lookup"><span data-stu-id="38935-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="38935-112">Les données de la mémoire tampon de `context` doivent être au format de la structure de `CONTEXT` Win32.</span><span class="sxs-lookup"><span data-stu-id="38935-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="38935-113">Le contexte spécifie des données de Registre spécifiques au processeur, donc la définition de la structure de `CONTEXT` Win32 dépend de l’architecture du processeur.</span><span class="sxs-lookup"><span data-stu-id="38935-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="38935-114">Reportez-vous au fichier d’en-tête Winnt. h pour la définition de la structure de `CONTEXT` Win32.</span><span class="sxs-lookup"><span data-stu-id="38935-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38935-115">Notes</span><span class="sxs-lookup"><span data-stu-id="38935-115">Remarks</span></span>  
 <span data-ttu-id="38935-116">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="38935-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38935-117">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="38935-117">Requirements</span></span>  
 <span data-ttu-id="38935-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38935-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38935-119">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="38935-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="38935-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38935-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38935-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38935-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38935-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38935-122">See also</span></span>

- [<span data-ttu-id="38935-123">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="38935-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
