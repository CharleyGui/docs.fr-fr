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
ms.openlocfilehash: 3777ad4b12c7d0593c095c470aba81088137a859
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179183"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="f6842-102">ICLRDataTarget::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="f6842-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="f6842-103">Obtient le contexte d’exécution actuel pour le thread donné dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="f6842-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="f6842-104">Cette méthode est appelée par les services d’accès aux données de l’heure courante.</span><span class="sxs-lookup"><span data-stu-id="f6842-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6842-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6842-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6842-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f6842-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="f6842-107">[dans] L’identifiant du système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="f6842-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="f6842-108">[dans] Drapeaux qui précisent quelles parties du contexte revenir.</span><span class="sxs-lookup"><span data-stu-id="f6842-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="f6842-109">La mise en œuvre reviendra au moins dans ces parties du contexte.</span><span class="sxs-lookup"><span data-stu-id="f6842-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="f6842-110">[dans] La taille du contexte.</span><span class="sxs-lookup"><span data-stu-id="f6842-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="f6842-111">[out] Pointeur vers un tampon dans lequel placer le contexte.</span><span class="sxs-lookup"><span data-stu-id="f6842-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="f6842-112">Les données `context` dans le tampon doivent être dans `CONTEXT` le format de la structure Win32.</span><span class="sxs-lookup"><span data-stu-id="f6842-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="f6842-113">Le contexte spécifie les données d’enregistrement spécifiques `CONTEXT` au processeur, de sorte que la définition de la structure Win32 dépend de l’architecture du processeur.</span><span class="sxs-lookup"><span data-stu-id="f6842-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="f6842-114">Consultez le fichier d’en-tête WinNT.h `CONTEXT` pour la définition de la structure Win32.</span><span class="sxs-lookup"><span data-stu-id="f6842-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6842-115">Notes </span><span class="sxs-lookup"><span data-stu-id="f6842-115">Remarks</span></span>  
 <span data-ttu-id="f6842-116">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="f6842-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6842-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f6842-117">Requirements</span></span>  
 <span data-ttu-id="f6842-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6842-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6842-119">**En-tête:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="f6842-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f6842-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f6842-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6842-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6842-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6842-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f6842-122">See also</span></span>

- [<span data-ttu-id="f6842-123">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="f6842-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
