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
ms.openlocfilehash: 9b7624c2902d17e437cda9a0a84ddf288323b577
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676177"
---
# <a name="_efn_stacktrace-function"></a><span data-ttu-id="0f10b-102">\_EFN \_ fonction StackTrace</span><span class="sxs-lookup"><span data-stu-id="0f10b-102">\_EFN\_StackTrace Function</span></span>

<span data-ttu-id="0f10b-103">Fournit une représentation textuelle d'une trace de pile managée et un tableau d'enregistrements `CONTEXT` pour chaque transition entre du code non managé et du code managé.</span><span class="sxs-lookup"><span data-stu-id="0f10b-103">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f10b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f10b-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="0f10b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f10b-105">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="0f10b-106">dans Client en cours de débogage.</span><span class="sxs-lookup"><span data-stu-id="0f10b-106">[in] The client being debugged.</span></span>  
  
 `wszTextOut`  
 <span data-ttu-id="0f10b-107">à Représentation textuelle de la trace de la pile.</span><span class="sxs-lookup"><span data-stu-id="0f10b-107">[out] The text representation of the stack trace.</span></span>  
  
 `puiTextLength`  
 <span data-ttu-id="0f10b-108">à Pointeur vers le nombre de caractères dans `wszTextOut` .</span><span class="sxs-lookup"><span data-stu-id="0f10b-108">[out] A pointer to the number of characters in `wszTextOut`.</span></span>  
  
 `pTransitionContexts`  
 <span data-ttu-id="0f10b-109">à Tableau de contextes de transition.</span><span class="sxs-lookup"><span data-stu-id="0f10b-109">[out] The array of transition contexts.</span></span>  
  
 `puiTransitionContextCount`  
 <span data-ttu-id="0f10b-110">à Pointeur vers le nombre de contextes de transition dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="0f10b-110">[out] A pointer to the number of transition contexts in the array.</span></span>  
  
 `uiSizeOfContext`  
 <span data-ttu-id="0f10b-111">dans Taille de la structure de contexte.</span><span class="sxs-lookup"><span data-stu-id="0f10b-111">[in] The size of the context structure.</span></span>  
  
 `Flags`  
 <span data-ttu-id="0f10b-112">dans Définissez sur 0 ou SOS_STACKTRACE_SHOWADDRESSES (0x01) pour afficher le registre EBP et le pointeur de pile Enter (ESP) devant chaque `module!functionname` ligne.</span><span class="sxs-lookup"><span data-stu-id="0f10b-112">[in] Set to either 0 or SOS_STACKTRACE_SHOWADDRESSES (0x01) to show the EBP register and the enter stack pointer (ESP) in front of each `module!functionname` line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f10b-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="0f10b-113">Remarks</span></span>  

 <span data-ttu-id="0f10b-114">La `_EFN_StackTrace` structure peut être appelée à partir d’une interface de programmation WinDbg.</span><span class="sxs-lookup"><span data-stu-id="0f10b-114">The `_EFN_StackTrace` structure can be called from a WinDbg programmatic interface.</span></span> <span data-ttu-id="0f10b-115">Les paramètres sont utilisés comme suit :</span><span class="sxs-lookup"><span data-stu-id="0f10b-115">Parameters are used as follows:</span></span>  
  
- <span data-ttu-id="0f10b-116">Si `wszTextOut` a la valeur null et que `puiTextLength` n’est pas null, la fonction retourne la longueur de la chaîne dans `puiTextLength` .</span><span class="sxs-lookup"><span data-stu-id="0f10b-116">If `wszTextOut` is null and `puiTextLength` is not null, the function returns the string length in `puiTextLength`.</span></span>  
  
- <span data-ttu-id="0f10b-117">Si `wszTextOut` n’a pas la valeur null, la fonction stocke le texte dans `wszTextOut` l’emplacement indiqué par `puiTextLength` .</span><span class="sxs-lookup"><span data-stu-id="0f10b-117">If `wszTextOut` is not null, the function stores text in `wszTextOut` up to the location indicated by `puiTextLength`.</span></span> <span data-ttu-id="0f10b-118">Elle retourne avec succès si la mémoire tampon est suffisamment grande, ou si elle retourne E_OUTOFMEMORY si la mémoire tampon n’était pas suffisamment longue.</span><span class="sxs-lookup"><span data-stu-id="0f10b-118">It returns successfully if there was enough room in the buffer, or returns E_OUTOFMEMORY if the buffer was not long enough.</span></span>  
  
- <span data-ttu-id="0f10b-119">La partie transition de la fonction est ignorée si `pTransitionContexts` et `puiTransitionContextCount` sont tous deux null.</span><span class="sxs-lookup"><span data-stu-id="0f10b-119">The transition portion of the function is ignored if `pTransitionContexts` and `puiTransitionContextCount` are both null.</span></span> <span data-ttu-id="0f10b-120">Dans ce cas, la fonction fournit aux appelants une sortie texte uniquement des noms de fonctions.</span><span class="sxs-lookup"><span data-stu-id="0f10b-120">In this case, the function provides callers with text output of only the function names.</span></span>  
  
- <span data-ttu-id="0f10b-121">Si `pTransitionContexts` a la valeur null et que `puiTransitionContextCount` n’est pas null, la fonction retourne le nombre nécessaire d’entrées de contexte dans `puiTransitionContextCount` .</span><span class="sxs-lookup"><span data-stu-id="0f10b-121">If `pTransitionContexts` is null and `puiTransitionContextCount` is not null, the function returns the necessary number of context entries in `puiTransitionContextCount`.</span></span>  
  
- <span data-ttu-id="0f10b-122">Si `pTransitionContexts` n’a pas la valeur null, la fonction la traite comme un tableau de structures de longueur `puiTransitionContextCount` .</span><span class="sxs-lookup"><span data-stu-id="0f10b-122">If `pTransitionContexts` is not null, the function treats it as an array of structures of length `puiTransitionContextCount`.</span></span> <span data-ttu-id="0f10b-123">La taille de la structure est donnée par `uiSizeOfContext` , et doit être la taille de [SimpleContext](stacktrace-simplecontext-structure.md) ou `CONTEXT` de l’architecture.</span><span class="sxs-lookup"><span data-stu-id="0f10b-123">The structure size is given by `uiSizeOfContext`, and must be the size of [SimpleContext](stacktrace-simplecontext-structure.md) or `CONTEXT` for the architecture.</span></span>  
  
- <span data-ttu-id="0f10b-124">`wszTextOut` est écrit au format suivant :</span><span class="sxs-lookup"><span data-stu-id="0f10b-124">`wszTextOut` is written in the following format:</span></span>  
  
    ```output  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
- <span data-ttu-id="0f10b-125">Si le décalage dans hex est 0x0, aucun décalage n’est écrit.</span><span class="sxs-lookup"><span data-stu-id="0f10b-125">If the offset in hex is 0x0, no offset is written.</span></span>  
  
- <span data-ttu-id="0f10b-126">S’il n’existe aucun code managé sur le thread actuellement en contexte, la fonction retourne SOS_E_NOMANAGEDCODE.</span><span class="sxs-lookup"><span data-stu-id="0f10b-126">If there is no managed code on the thread currently in context, the function returns SOS_E_NOMANAGEDCODE.</span></span>  
  
- <span data-ttu-id="0f10b-127">Le `Flags` paramètre est égal à 0 ou SOS_STACKTRACE_SHOWADDRESSES pour voir EBP et ESP devant chaque `module!functionname` ligne.</span><span class="sxs-lookup"><span data-stu-id="0f10b-127">The `Flags` parameter is either 0 or SOS_STACKTRACE_SHOWADDRESSES to see EBP and ESP in front of each `module!functionname` line.</span></span> <span data-ttu-id="0f10b-128">Par défaut, il est égal à 0.</span><span class="sxs-lookup"><span data-stu-id="0f10b-128">By default, it is 0.</span></span>  
  
    ```cpp  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a><span data-ttu-id="0f10b-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0f10b-129">Requirements</span></span>  

 <span data-ttu-id="0f10b-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f10b-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f10b-131">**En-tête :** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="0f10b-131">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="0f10b-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f10b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f10b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f10b-133">See also</span></span>

- [<span data-ttu-id="0f10b-134">Fonctions statiques globales du débogage</span><span class="sxs-lookup"><span data-stu-id="0f10b-134">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
