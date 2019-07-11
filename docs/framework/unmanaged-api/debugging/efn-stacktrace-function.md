---
title: _EFN_StackTrace, fonction
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 687fdd0735e6cb0f3a727c8a2da3cf33bffb6a39
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738983"
---
# <a name="efnstacktrace-function"></a><span data-ttu-id="23c6d-102">\_EFN\_StackTrace (fonction)</span><span class="sxs-lookup"><span data-stu-id="23c6d-102">\_EFN\_StackTrace Function</span></span>
<span data-ttu-id="23c6d-103">Fournit une représentation textuelle d'une trace de pile managée et un tableau d'enregistrements `CONTEXT` pour chaque transition entre du code non managé et du code managé.</span><span class="sxs-lookup"><span data-stu-id="23c6d-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23c6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23c6d-104">Syntax</span></span>  
  
```cpp  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23c6d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="23c6d-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="23c6d-106">[in] Le client en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="23c6d-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="23c6d-107">[out] La représentation textuelle de la trace de pile.</span><span class="sxs-lookup"><span data-stu-id="23c6d-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="23c6d-108">[out] Un pointeur vers le nombre de caractères dans `wszTextOut`.</span><span class="sxs-lookup"><span data-stu-id="23c6d-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="23c6d-109">[out] Le tableau de contextes de transition.</span><span class="sxs-lookup"><span data-stu-id="23c6d-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="23c6d-110">[out] Pointeur vers le nombre de contextes de transition dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="23c6d-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="23c6d-111">[in] La taille de la structure de contexte.</span><span class="sxs-lookup"><span data-stu-id="23c6d-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="23c6d-112">[in] La valeur 0 ou SOS_STACKTRACE_SHOWADDRESSES (0 x 01) pour afficher le registre EBP et le pointeur de pile d’entrée (ESP) devant chacun `module!functionname` ligne.</span><span class="sxs-lookup"><span data-stu-id="23c6d-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="23c6d-113">Notes</span><span class="sxs-lookup"><span data-stu-id="23c6d-113">Remarks</span></span>  
 <span data-ttu-id="23c6d-114">Le `_EFN_StackTrace` structure peut être appelée à partir d’une interface de programmation WinDbg.</span><span class="sxs-lookup"><span data-stu-id="23c6d-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="23c6d-115">Paramètres sont utilisés comme suit :</span><span class="sxs-lookup"><span data-stu-id="23c6d-115">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="23c6d-116">Si `wszTextOut` a la valeur null et `puiTextLength` est non null, la fonction retourne la longueur de chaîne dans `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="23c6d-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="23c6d-117">Si `wszTextOut` est non null, la fonction stocke le texte dans `wszTextOut` jusqu'à l’emplacement indiqué par `puiTextLength`.</span><span class="sxs-lookup"><span data-stu-id="23c6d-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="23c6d-118">Il retourne une valeur si il y a suffisamment d’espace dans la mémoire tampon, ou retourne E_OUTOFMEMORY si la mémoire tampon n’est pas assez long.</span><span class="sxs-lookup"><span data-stu-id="23c6d-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="23c6d-119">La partie de la transition de la fonction est ignorée si `pTransitionContexts` et `puiTransitionContextCount` sont tous deux null.</span><span class="sxs-lookup"><span data-stu-id="23c6d-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="23c6d-120">Dans ce cas, la fonction fournit les appelants avec sortie texte du uniquement les noms de fonction.</span><span class="sxs-lookup"><span data-stu-id="23c6d-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="23c6d-121">Si `pTransitionContexts` a la valeur null et `puiTransitionContextCount` est non null, la fonction retourne le nombre nécessaire d’entrées de contexte dans `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="23c6d-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="23c6d-122">Si `pTransitionContexts` est non null, la fonction traite comme un tableau de structures de longueur `puiTransitionContextCount`.</span><span class="sxs-lookup"><span data-stu-id="23c6d-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="23c6d-123">La taille de la structure est fournie par `uiSizeOfContext`, et doit être la taille de [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) ou `CONTEXT` pour l’architecture.</span><span class="sxs-lookup"><span data-stu-id="23c6d-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="23c6d-124">`wszTextOut` est écrit dans le format suivant :</span><span class="sxs-lookup"><span data-stu-id="23c6d-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="23c6d-125">Si l’offset en hexadécimal est 0 x 0, aucun offset n’est écrit.</span><span class="sxs-lookup"><span data-stu-id="23c6d-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="23c6d-126">S’il n’existe aucun code managé sur le thread actuellement dans le contexte, la fonction retourne alors SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="23c6d-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="23c6d-127">Le `Flags` paramètre est 0 ou SOS_STACKTRACE_SHOWADDRESSES pour voir EBP et ESP devant chaque `module!functionname` ligne.</span><span class="sxs-lookup"><span data-stu-id="23c6d-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="23c6d-128">Par défaut, il est 0.</span><span class="sxs-lookup"><span data-stu-id="23c6d-128">By default, it is 0.</span></span>  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="23c6d-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="23c6d-129">Requirements</span></span>  
 <span data-ttu-id="23c6d-130">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23c6d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23c6d-131">**En-tête :** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="23c6d-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="23c6d-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23c6d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23c6d-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23c6d-133">See also</span></span>

- [<span data-ttu-id="23c6d-134">Fonctions statiques globales de débogage</span><span class="sxs-lookup"><span data-stu-id="23c6d-134">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
