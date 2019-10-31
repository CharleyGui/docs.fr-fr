---
title: Fonction QualifierSet_BeginEnumeration (référence des API non managées)
description: La fonction QualifierSet_BeginEnumeration réinitialise un énumérateur des qualificateurs d’un objet.
ms.date: 11/06/2017
api_name:
- QualifierSet_BeginEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_BeginEnumeration
helpviewer_keywords:
- QualifierSet_BeginEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 79edbd876fc9992f088b9adb159e005c735a72cb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127326"
---
# <a name="qualifierset_beginenumeration-function"></a><span data-ttu-id="60481-103">QualifierSet_BeginEnumeration fonction)</span><span class="sxs-lookup"><span data-stu-id="60481-103">QualifierSet_BeginEnumeration function</span></span>

<span data-ttu-id="60481-104">Réinitialise un énumérateur des qualificateurs d’un objet au début de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="60481-104">Resets an enumerator of the qualifiers of an object to the beginning of the enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="60481-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60481-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_BeginEnumeration (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags
);
```

## <a name="parameters"></a><span data-ttu-id="60481-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="60481-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="60481-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="60481-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="60481-108">dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="60481-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="60481-109">dans Combinaison d’opérations de bits des indicateurs ou valeurs décrites dans la section [Notes](#remarks) qui spécifie les qualificateurs à inclure dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="60481-109">[in] A bitwise combination of the flags or values described in the [Remarks](#remarks) section that specifies the qualifiers to include in the enumeration.</span></span>

## <a name="return-value"></a><span data-ttu-id="60481-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="60481-110">Return value</span></span>

<span data-ttu-id="60481-111">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="60481-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="60481-112">Constante</span><span class="sxs-lookup"><span data-stu-id="60481-112">Constant</span></span>  |<span data-ttu-id="60481-113">valeur</span><span class="sxs-lookup"><span data-stu-id="60481-113">Value</span></span>  |<span data-ttu-id="60481-114">Description</span><span class="sxs-lookup"><span data-stu-id="60481-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="60481-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="60481-115">0x80041008</span></span> | <span data-ttu-id="60481-116">Le paramètre `lFlags` n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="60481-116">The `lFlags` parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="60481-117">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="60481-117">0x8004101d</span></span> | <span data-ttu-id="60481-118">Un deuxième appel à `QualifierSet_BeginEnumeration` a été effectué sans appel intermédiaire à [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="60481-118">A second call to `QualifierSet_BeginEnumeration` was made without an intervening call to [`QualifierSet_EndEnumeration`](qualifierset-endenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="60481-119">0x80041006</span><span class="sxs-lookup"><span data-stu-id="60481-119">0x80041006</span></span> | <span data-ttu-id="60481-120">Mémoire disponible insuffisante pour commencer une nouvelle énumération.</span><span class="sxs-lookup"><span data-stu-id="60481-120">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="60481-121">0</span><span class="sxs-lookup"><span data-stu-id="60481-121">0</span></span> | <span data-ttu-id="60481-122">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="60481-122">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="60481-123">Notes</span><span class="sxs-lookup"><span data-stu-id="60481-123">Remarks</span></span>

<span data-ttu-id="60481-124">Cette fonction encapsule un appel à la méthode [IWbemQualifierSet :: BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) .</span><span class="sxs-lookup"><span data-stu-id="60481-124">This function wraps a call to the [IWbemQualifierSet::BeginEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-beginenumeration) method.</span></span>

<span data-ttu-id="60481-125">Pour énumérer tous les qualificateurs d’un objet, cette méthode doit être appelée avant le premier appel à [QualifierSet_Next](qualifierset-next.md).</span><span class="sxs-lookup"><span data-stu-id="60481-125">To enumerate all of the qualifiers on an object, this method must be called before the first call to [QualifierSet_Next](qualifierset-next.md).</span></span> <span data-ttu-id="60481-126">L’ordre dans lequel les qualificateurs sont énumérés est toujours indifférent pour une énumération donnée.</span><span class="sxs-lookup"><span data-stu-id="60481-126">The order in which qualifiers are enumerated is guaranteed to be invariant for a given enumeration.</span></span>

<span data-ttu-id="60481-127">Les indicateurs qui peuvent être passés en tant qu’argument `lEnumFlags` sont définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="60481-127">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

|<span data-ttu-id="60481-128">Constante</span><span class="sxs-lookup"><span data-stu-id="60481-128">Constant</span></span>  |<span data-ttu-id="60481-129">valeur</span><span class="sxs-lookup"><span data-stu-id="60481-129">Value</span></span>  |<span data-ttu-id="60481-130">Description</span><span class="sxs-lookup"><span data-stu-id="60481-130">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="60481-131">0</span><span class="sxs-lookup"><span data-stu-id="60481-131">0</span></span> | <span data-ttu-id="60481-132">Retourne les noms de tous les qualificateurs.</span><span class="sxs-lookup"><span data-stu-id="60481-132">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="60481-133">0x10</span><span class="sxs-lookup"><span data-stu-id="60481-133">0x10</span></span> | <span data-ttu-id="60481-134">Retourne uniquement les noms des qualificateurs spécifiques à la propriété ou à l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="60481-134">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="60481-135">Pour une propriété : retourner uniquement les qualificateurs spécifiques à la propriété (y compris les substitutions), et non les qualificateurs propagés à partir de la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="60481-135">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="60481-136">Pour une instance : retourner uniquement des noms de qualificateurs spécifiques à l’instance.</span><span class="sxs-lookup"><span data-stu-id="60481-136">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="60481-137">Pour une classe : retourne uniquement les qualificateurs spécifiques à la classe qui est dérivée.</span><span class="sxs-lookup"><span data-stu-id="60481-137">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="60481-138">0x20</span><span class="sxs-lookup"><span data-stu-id="60481-138">0x20</span></span> | <span data-ttu-id="60481-139">Retourne uniquement les noms des qualificateurs propagés à partir d’un autre objet.</span><span class="sxs-lookup"><span data-stu-id="60481-139">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="60481-140">Pour une propriété : Retournez uniquement les qualificateurs propagés à cette propriété à partir de la définition de classe, et non ceux de la propriété elle-même.</span><span class="sxs-lookup"><span data-stu-id="60481-140">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="60481-141">Pour une instance : retourner uniquement les qualificateurs propagés à partir de la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="60481-141">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="60481-142">Pour une classe : Retournez uniquement les noms de qualificateur hérités des classes parentes.</span><span class="sxs-lookup"><span data-stu-id="60481-142">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

## <a name="requirements"></a><span data-ttu-id="60481-143">spécifications</span><span class="sxs-lookup"><span data-stu-id="60481-143">Requirements</span></span>

<span data-ttu-id="60481-144">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60481-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="60481-145">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="60481-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="60481-146">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="60481-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="60481-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="60481-147">See also</span></span>

- [<span data-ttu-id="60481-148">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="60481-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
