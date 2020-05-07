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
ms.openlocfilehash: 5c0fb023dd355f3a9c1ed846913f86b354592ed5
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860603"
---
# <a name="iclrdatatargetgetthreadcontext-method"></a><span data-ttu-id="cd0e6-102">ICLRDataTarget::GetThreadContext, méthode</span><span class="sxs-lookup"><span data-stu-id="cd0e6-102">ICLRDataTarget::GetThreadContext Method</span></span>
<span data-ttu-id="cd0e6-103">Obtient le contexte d’exécution actuel du thread donné dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="cd0e6-103">Gets the current execution context for the given thread in the target process.</span></span> <span data-ttu-id="cd0e6-104">Cette méthode est appelée par les services d’accès aux données common language runtime.</span><span class="sxs-lookup"><span data-stu-id="cd0e6-104">This method is called by the common language runtime data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd0e6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd0e6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext (  
    [in] ULONG32            threadID,  
    [in] ULONG32            contextFlags,  
    [in] ULONG32            contextSize,  
    [out, size_is(contextSize)]
        BYTE                *context  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd0e6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cd0e6-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="cd0e6-107">dans Identificateur de système d’exploitation d’un thread dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="cd0e6-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `contextFlags`  
 <span data-ttu-id="cd0e6-108">dans Indicateurs qui spécifient les parties du contexte à retourner.</span><span class="sxs-lookup"><span data-stu-id="cd0e6-108">[in] Flags that specify which parts of the context to return.</span></span> <span data-ttu-id="cd0e6-109">L’implémentation renverra au moins ces parties du contexte.</span><span class="sxs-lookup"><span data-stu-id="cd0e6-109">The implementation will return at least these parts of the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="cd0e6-110">dans Taille du contexte.</span><span class="sxs-lookup"><span data-stu-id="cd0e6-110">[in] The size of the context.</span></span>  
  
 `context`  
 <span data-ttu-id="cd0e6-111">à Pointeur vers une mémoire tampon dans laquelle placer le contexte.</span><span class="sxs-lookup"><span data-stu-id="cd0e6-111">[out] Pointer to a buffer in which to place the context.</span></span>  
  
 <span data-ttu-id="cd0e6-112">Les données de la `context` mémoire tampon doivent être au format de la structure `CONTEXT` Win32.</span><span class="sxs-lookup"><span data-stu-id="cd0e6-112">The data in the `context` buffer must be in the format of the Win32 `CONTEXT` structure.</span></span> <span data-ttu-id="cd0e6-113">Le contexte spécifie des données de Registre spécifiques au processeur, donc la définition `CONTEXT` de la structure Win32 dépend de l’architecture du processeur.</span><span class="sxs-lookup"><span data-stu-id="cd0e6-113">The context specifies processor-specific register data, so the definition of the Win32 `CONTEXT` structure depends on the processor's architecture.</span></span> <span data-ttu-id="cd0e6-114">Reportez-vous au fichier d’en-tête Winnt. `CONTEXT` h pour la définition de la structure Win32.</span><span class="sxs-lookup"><span data-stu-id="cd0e6-114">Refer to the WinNT.h header file for the definition of the Win32 `CONTEXT` structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd0e6-115">Notes </span><span class="sxs-lookup"><span data-stu-id="cd0e6-115">Remarks</span></span>  
 <span data-ttu-id="cd0e6-116">Cette méthode est implémentée par le writer de l'application de débogage.</span><span class="sxs-lookup"><span data-stu-id="cd0e6-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd0e6-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cd0e6-117">Requirements</span></span>  
 <span data-ttu-id="cd0e6-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd0e6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd0e6-119">**En-tête :** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="cd0e6-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="cd0e6-120">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd0e6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd0e6-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd0e6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd0e6-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd0e6-122">See also</span></span>

- [<span data-ttu-id="cd0e6-123">ICLRDataTarget, interface</span><span class="sxs-lookup"><span data-stu-id="cd0e6-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
