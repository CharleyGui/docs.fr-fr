---
title: Fonction BeginEnumeration (Référence API non gestion)
description: La fonction BeginEnumeration réinitialise un énumérateur au début de l’énumération
ms.date: 11/06/2017
api_name:
- BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginEnumeration
helpviewer_keywords:
- BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: eac23916bd78ec3970a87566e2d2f4d79b379824
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176875"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="30f7e-103">BeginEnumeration, fonction</span><span class="sxs-lookup"><span data-stu-id="30f7e-103">BeginEnumeration function</span></span>
<span data-ttu-id="30f7e-104">Réinitialise un enumérateur au début de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="30f7e-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="30f7e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30f7e-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="30f7e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="30f7e-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="30f7e-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="30f7e-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="30f7e-108">[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="30f7e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="30f7e-109">[dans] Une combinaison peu sage des drapeaux ou des valeurs décrites dans la section [Remarques](#remarks) qui contrôle les propriétés incluses dans le recensement.</span><span class="sxs-lookup"><span data-stu-id="30f7e-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="30f7e-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="30f7e-110">Return value</span></span>

<span data-ttu-id="30f7e-111">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="30f7e-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="30f7e-112">Constant</span><span class="sxs-lookup"><span data-stu-id="30f7e-112">Constant</span></span>  |<span data-ttu-id="30f7e-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="30f7e-113">Value</span></span>  |<span data-ttu-id="30f7e-114">Description</span><span class="sxs-lookup"><span data-stu-id="30f7e-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="30f7e-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="30f7e-115">0x80041008</span></span> | <span data-ttu-id="30f7e-116">La combinaison des `lEnumFlags` drapeaux est invalide, ou un argument invalide a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="30f7e-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="30f7e-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="30f7e-117">0x8004101d</span></span> | <span data-ttu-id="30f7e-118">Un deuxième `BeginEnumeration` appel a été fait [`EndEnumeration`](endenumeration.md)sans un appel intermédiaire à .</span><span class="sxs-lookup"><span data-stu-id="30f7e-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="30f7e-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="30f7e-119">0x80041006</span></span> | <span data-ttu-id="30f7e-120">Pas assez de mémoire est disponible pour commencer une nouvelle énumération.</span><span class="sxs-lookup"><span data-stu-id="30f7e-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="30f7e-121">0</span><span class="sxs-lookup"><span data-stu-id="30f7e-121">0</span></span> | <span data-ttu-id="30f7e-122">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="30f7e-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="30f7e-123">Notes </span><span class="sxs-lookup"><span data-stu-id="30f7e-123">Remarks</span></span>

<span data-ttu-id="30f7e-124">Cette fonction enveloppe un appel à [l’IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) méthode.</span><span class="sxs-lookup"><span data-stu-id="30f7e-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="30f7e-125">Les drapeaux qui peuvent `lEnumFlags` être passés comme l’argument sont définis dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="30f7e-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="30f7e-126">Vous pouvez combiner un drapeau de chaque groupe avec n’importe quel drapeau de n’importe quel autre groupe.</span><span class="sxs-lookup"><span data-stu-id="30f7e-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="30f7e-127">Cependant, les drapeaux du même groupe s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="30f7e-127">However, flags from the same group are mutually exclusive.</span></span>

<span data-ttu-id="30f7e-128">**Groupe 1**</span><span class="sxs-lookup"><span data-stu-id="30f7e-128">**Group 1**</span></span>

|<span data-ttu-id="30f7e-129">Constant</span><span class="sxs-lookup"><span data-stu-id="30f7e-129">Constant</span></span>  |<span data-ttu-id="30f7e-130">Valeur</span><span class="sxs-lookup"><span data-stu-id="30f7e-130">Value</span></span>  |<span data-ttu-id="30f7e-131">Description</span><span class="sxs-lookup"><span data-stu-id="30f7e-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="30f7e-132">0x4</span><span class="sxs-lookup"><span data-stu-id="30f7e-132">0x4</span></span> | <span data-ttu-id="30f7e-133">Inclure les propriétés qui constituent la clé seulement.</span><span class="sxs-lookup"><span data-stu-id="30f7e-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="30f7e-134">0x8</span><span class="sxs-lookup"><span data-stu-id="30f7e-134">0x8</span></span> | <span data-ttu-id="30f7e-135">Inclure les propriétés qui sont des références d’objet seulement.</span><span class="sxs-lookup"><span data-stu-id="30f7e-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="30f7e-136">**Groupe 2**</span><span class="sxs-lookup"><span data-stu-id="30f7e-136">**Group 2**</span></span>

<span data-ttu-id="30f7e-137">Constant</span><span class="sxs-lookup"><span data-stu-id="30f7e-137">Constant</span></span>  |<span data-ttu-id="30f7e-138">Valeur</span><span class="sxs-lookup"><span data-stu-id="30f7e-138">Value</span></span>  |<span data-ttu-id="30f7e-139">Description</span><span class="sxs-lookup"><span data-stu-id="30f7e-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="30f7e-140">0x30</span><span class="sxs-lookup"><span data-stu-id="30f7e-140">0x30</span></span> | <span data-ttu-id="30f7e-141">Limiter l’énumération aux propriétés du système seulement.</span><span class="sxs-lookup"><span data-stu-id="30f7e-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="30f7e-142">0x40</span><span class="sxs-lookup"><span data-stu-id="30f7e-142">0x40</span></span> | <span data-ttu-id="30f7e-143">Inclure les propriétés locales et propagées, mais exclure les propriétés du système de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="30f7e-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="30f7e-144">Pour les classes :</span><span class="sxs-lookup"><span data-stu-id="30f7e-144">For classes:</span></span>

<span data-ttu-id="30f7e-145">Constant</span><span class="sxs-lookup"><span data-stu-id="30f7e-145">Constant</span></span>  |<span data-ttu-id="30f7e-146">Valeur</span><span class="sxs-lookup"><span data-stu-id="30f7e-146">Value</span></span>  |<span data-ttu-id="30f7e-147">Description</span><span class="sxs-lookup"><span data-stu-id="30f7e-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="30f7e-148">0x100</span><span class="sxs-lookup"><span data-stu-id="30f7e-148">0x100</span></span> | <span data-ttu-id="30f7e-149">Limiter l’énumération aux propriétés remplacées dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="30f7e-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="30f7e-150">0x100</span><span class="sxs-lookup"><span data-stu-id="30f7e-150">0x100</span></span> | <span data-ttu-id="30f7e-151">Limiter l’énumération aux propriétés remplacées dans la définition de classe actuelle et aux nouvelles propriétés définies dans la classe.</span><span class="sxs-lookup"><span data-stu-id="30f7e-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="30f7e-152">0x300</span><span class="sxs-lookup"><span data-stu-id="30f7e-152">0x300</span></span> | <span data-ttu-id="30f7e-153">Un masque (plutôt qu’un drapeau) à appliquer contre une `lEnumFlags` valeur pour vérifier si l’un ou l’autre `WBEM_FLAG_CLASS_OVERRIDES_ONLY` ou `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` est réglé.</span><span class="sxs-lookup"><span data-stu-id="30f7e-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="30f7e-154">0x10</span><span class="sxs-lookup"><span data-stu-id="30f7e-154">0x10</span></span> | <span data-ttu-id="30f7e-155">Limitez l’énumération aux propriétés qui sont définies ou modifiées dans la classe elle-même.</span><span class="sxs-lookup"><span data-stu-id="30f7e-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="30f7e-156">0x20</span><span class="sxs-lookup"><span data-stu-id="30f7e-156">0x20</span></span> | <span data-ttu-id="30f7e-157">Limitez l’énumération aux propriétés héritées des classes de base.</span><span class="sxs-lookup"><span data-stu-id="30f7e-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="30f7e-158">Pour les cas :</span><span class="sxs-lookup"><span data-stu-id="30f7e-158">For instances:</span></span>

<span data-ttu-id="30f7e-159">Constant</span><span class="sxs-lookup"><span data-stu-id="30f7e-159">Constant</span></span>  |<span data-ttu-id="30f7e-160">Valeur</span><span class="sxs-lookup"><span data-stu-id="30f7e-160">Value</span></span>  |<span data-ttu-id="30f7e-161">Description</span><span class="sxs-lookup"><span data-stu-id="30f7e-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="30f7e-162">0x10</span><span class="sxs-lookup"><span data-stu-id="30f7e-162">0x10</span></span> | <span data-ttu-id="30f7e-163">Limitez l’énumération aux propriétés qui sont définies ou modifiées dans la classe elle-même.</span><span class="sxs-lookup"><span data-stu-id="30f7e-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="30f7e-164">0x20</span><span class="sxs-lookup"><span data-stu-id="30f7e-164">0x20</span></span> | <span data-ttu-id="30f7e-165">Limitez l’énumération aux propriétés héritées des classes de base.</span><span class="sxs-lookup"><span data-stu-id="30f7e-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="30f7e-166">Spécifications</span><span class="sxs-lookup"><span data-stu-id="30f7e-166">Requirements</span></span>  
 <span data-ttu-id="30f7e-167">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30f7e-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30f7e-168">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="30f7e-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="30f7e-169">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="30f7e-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30f7e-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30f7e-170">See also</span></span>

- [<span data-ttu-id="30f7e-171">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="30f7e-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
