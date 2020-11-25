---
title: Fonction BeginEnumeration (référence des API non managées)
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
ms.openlocfilehash: 6057526ddbe2efed65f8569e829c35524829e43e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708216"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="6b2f1-103">BeginEnumeration, fonction</span><span class="sxs-lookup"><span data-stu-id="6b2f1-103">BeginEnumeration function</span></span>

<span data-ttu-id="6b2f1-104">Rétablit un énumérateur au début de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-104">Resets an enumerator back to the beginning of the enumeration.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="6b2f1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b2f1-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="6b2f1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6b2f1-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="6b2f1-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="6b2f1-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="6b2f1-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`\
<span data-ttu-id="6b2f1-109">dans Combinaison d’opérations de bits des indicateurs ou valeurs décrites dans la section [Notes](#remarks) qui contrôle les propriétés incluses dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that controls the properties included in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="6b2f1-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6b2f1-110">Return value</span></span>

<span data-ttu-id="6b2f1-111">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="6b2f1-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6b2f1-112">Constante</span><span class="sxs-lookup"><span data-stu-id="6b2f1-112">Constant</span></span>  |<span data-ttu-id="6b2f1-113">Value</span><span class="sxs-lookup"><span data-stu-id="6b2f1-113">Value</span></span>  |<span data-ttu-id="6b2f1-114">Description</span><span class="sxs-lookup"><span data-stu-id="6b2f1-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6b2f1-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6b2f1-115">0x80041008</span></span> | <span data-ttu-id="6b2f1-116">La combinaison d’indicateurs dans `lEnumFlags` n’est pas valide ou un argument non valide a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-116">The combination of flags in `lEnumFlags` is invalid, or an invalid argument was specified.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="6b2f1-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="6b2f1-117">0x8004101d</span></span> | <span data-ttu-id="6b2f1-118">Un deuxième appel à `BeginEnumeration` a été effectué sans appel à [`EndEnumeration`](endenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="6b2f1-118">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6b2f1-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6b2f1-119">0x80041006</span></span> | <span data-ttu-id="6b2f1-120">Mémoire disponible insuffisante pour commencer une nouvelle énumération.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6b2f1-121">0</span><span class="sxs-lookup"><span data-stu-id="6b2f1-121">0</span></span> | <span data-ttu-id="6b2f1-122">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-122">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="6b2f1-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="6b2f1-123">Remarks</span></span>

<span data-ttu-id="6b2f1-124">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="6b2f1-124">This function wraps a call to the [IWbemClassObject::BeginEnumeration](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) method.</span></span>

<span data-ttu-id="6b2f1-125">Les indicateurs qui peuvent être passés en tant qu' `lEnumFlags` argument sont définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-125">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="6b2f1-126">Vous pouvez associer un indicateur de chaque groupe à n’importe quel indicateur de n’importe quel autre groupe.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-126">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="6b2f1-127">Toutefois, les indicateurs du même groupe s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-127">However, flags from the same group are mutually exclusive.</span></span>

<span data-ttu-id="6b2f1-128">**Groupe 1**</span><span class="sxs-lookup"><span data-stu-id="6b2f1-128">**Group 1**</span></span>

|<span data-ttu-id="6b2f1-129">Constante</span><span class="sxs-lookup"><span data-stu-id="6b2f1-129">Constant</span></span>  |<span data-ttu-id="6b2f1-130">Value</span><span class="sxs-lookup"><span data-stu-id="6b2f1-130">Value</span></span>  |<span data-ttu-id="6b2f1-131">Description</span><span class="sxs-lookup"><span data-stu-id="6b2f1-131">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="6b2f1-132">0x4</span><span class="sxs-lookup"><span data-stu-id="6b2f1-132">0x4</span></span> | <span data-ttu-id="6b2f1-133">Inclut les propriétés qui constituent la clé uniquement.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-133">Include properties that constitute the key only.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="6b2f1-134">0x8</span><span class="sxs-lookup"><span data-stu-id="6b2f1-134">0x8</span></span> | <span data-ttu-id="6b2f1-135">Inclut les propriétés qui sont des références d’objet uniquement.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-135">Include properties that are object references only.</span></span> |

<span data-ttu-id="6b2f1-136">**Groupe 2**</span><span class="sxs-lookup"><span data-stu-id="6b2f1-136">**Group 2**</span></span>

<span data-ttu-id="6b2f1-137">Constante</span><span class="sxs-lookup"><span data-stu-id="6b2f1-137">Constant</span></span>  |<span data-ttu-id="6b2f1-138">Value</span><span class="sxs-lookup"><span data-stu-id="6b2f1-138">Value</span></span>  |<span data-ttu-id="6b2f1-139">Description</span><span class="sxs-lookup"><span data-stu-id="6b2f1-139">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="6b2f1-140">0x30</span><span class="sxs-lookup"><span data-stu-id="6b2f1-140">0x30</span></span> | <span data-ttu-id="6b2f1-141">Limitez l’énumération aux propriétés système uniquement.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-141">Limit the enumeration to system properties only.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="6b2f1-142">0x40</span><span class="sxs-lookup"><span data-stu-id="6b2f1-142">0x40</span></span> | <span data-ttu-id="6b2f1-143">Incluez les propriétés locales et propagées, mais excluez les propriétés système de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-143">Include local and propagated properties but exclude system properties from the enumeration.</span></span> |

<span data-ttu-id="6b2f1-144">Pour les classes :</span><span class="sxs-lookup"><span data-stu-id="6b2f1-144">For classes:</span></span>

<span data-ttu-id="6b2f1-145">Constante</span><span class="sxs-lookup"><span data-stu-id="6b2f1-145">Constant</span></span>  |<span data-ttu-id="6b2f1-146">Value</span><span class="sxs-lookup"><span data-stu-id="6b2f1-146">Value</span></span>  |<span data-ttu-id="6b2f1-147">Description</span><span class="sxs-lookup"><span data-stu-id="6b2f1-147">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_CLASS_OVERRIDES_ONLY` | <span data-ttu-id="6b2f1-148">0x100</span><span class="sxs-lookup"><span data-stu-id="6b2f1-148">0x100</span></span> | <span data-ttu-id="6b2f1-149">Limitez l’énumération aux propriétés substituées dans la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-149">Limit the enumeration to properties overridden in the class definition.</span></span> |
|`WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` | <span data-ttu-id="6b2f1-150">0x100</span><span class="sxs-lookup"><span data-stu-id="6b2f1-150">0x100</span></span> | <span data-ttu-id="6b2f1-151">Limitez l’énumération aux propriétés substituées dans la définition de classe actuelle et aux nouvelles propriétés définies dans la classe.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-151">Limit the enumeration to properties overridden in the current class definition and to new properties defined in the class.</span></span> |
| `WBEM_MASK_CLASS_CONDITION` | <span data-ttu-id="6b2f1-152">0x300</span><span class="sxs-lookup"><span data-stu-id="6b2f1-152">0x300</span></span> | <span data-ttu-id="6b2f1-153">Masque (plutôt qu’un indicateur) à appliquer à une `lEnumFlags` valeur pour vérifier si `WBEM_FLAG_CLASS_OVERRIDES_ONLY` ou `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` est défini.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-153">A mask (rather than a flag) to apply against a `lEnumFlags` value to check if either `WBEM_FLAG_CLASS_OVERRIDES_ONLY` or `WBEM_FLAG_CLASS_LOCAL_AND_OVERRIDES` is set.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="6b2f1-154">0x10</span><span class="sxs-lookup"><span data-stu-id="6b2f1-154">0x10</span></span> | <span data-ttu-id="6b2f1-155">Limitez l’énumération aux propriétés définies ou modifiées dans la classe elle-même.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-155">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="6b2f1-156">0x20</span><span class="sxs-lookup"><span data-stu-id="6b2f1-156">0x20</span></span> | <span data-ttu-id="6b2f1-157">Limitez l’énumération aux propriétés héritées des classes de base.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-157">Limit the enumeration to properties that are inherited from base classes.</span></span> |

<span data-ttu-id="6b2f1-158">Pour les instances :</span><span class="sxs-lookup"><span data-stu-id="6b2f1-158">For instances:</span></span>

<span data-ttu-id="6b2f1-159">Constante</span><span class="sxs-lookup"><span data-stu-id="6b2f1-159">Constant</span></span>  |<span data-ttu-id="6b2f1-160">Value</span><span class="sxs-lookup"><span data-stu-id="6b2f1-160">Value</span></span>  |<span data-ttu-id="6b2f1-161">Description</span><span class="sxs-lookup"><span data-stu-id="6b2f1-161">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="6b2f1-162">0x10</span><span class="sxs-lookup"><span data-stu-id="6b2f1-162">0x10</span></span> | <span data-ttu-id="6b2f1-163">Limitez l’énumération aux propriétés définies ou modifiées dans la classe elle-même.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-163">Limit the enumeration to properties that are defined or modified in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="6b2f1-164">0x20</span><span class="sxs-lookup"><span data-stu-id="6b2f1-164">0x20</span></span> | <span data-ttu-id="6b2f1-165">Limitez l’énumération aux propriétés héritées des classes de base.</span><span class="sxs-lookup"><span data-stu-id="6b2f1-165">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="6b2f1-166">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6b2f1-166">Requirements</span></span>  

 <span data-ttu-id="6b2f1-167">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b2f1-167">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b2f1-168">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="6b2f1-168">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="6b2f1-169">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6b2f1-169">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b2f1-170">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b2f1-170">See also</span></span>

- [<span data-ttu-id="6b2f1-171">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="6b2f1-171">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
