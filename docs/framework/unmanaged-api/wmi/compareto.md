---
title: Fonction CompareTo (référence des API non managées)
description: La fonction CompareTo compare un objet à un autre objet WMI.
ms.date: 11/06/2017
api_name:
- CompareTo
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CompareTo
helpviewer_keywords:
- CompareTo function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3566b9b8a3b4183f936c82c39c38dc5daa3aeae1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636688"
---
# <a name="compareto-function"></a><span data-ttu-id="75237-103">CompareTo, fonction</span><span class="sxs-lookup"><span data-stu-id="75237-103">CompareTo function</span></span>

<span data-ttu-id="75237-104">Compare un objet à un autre objet WMI.</span><span class="sxs-lookup"><span data-stu-id="75237-104">Compares an object to another Windows management object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="75237-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75237-105">Syntax</span></span>

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a><span data-ttu-id="75237-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="75237-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="75237-107">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="75237-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="75237-108">[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="75237-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`\
<span data-ttu-id="75237-109">[in] Combinaison de bits des indicateurs qui spécifient les caractéristiques des objets à prendre en compte pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="75237-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="75237-110">Consultez le [notes](#remarks) section pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="75237-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`\
<span data-ttu-id="75237-111">[in] Objet pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="75237-111">[in] The object for comparison.</span></span> <span data-ttu-id="75237-112">`pCompareTo` doit être un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance ; il ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="75237-112">`pCompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="75237-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="75237-113">Return value</span></span>

<span data-ttu-id="75237-114">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="75237-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="75237-115">Constante</span><span class="sxs-lookup"><span data-stu-id="75237-115">Constant</span></span>  |<span data-ttu-id="75237-116">Value</span><span class="sxs-lookup"><span data-stu-id="75237-116">Value</span></span>  |<span data-ttu-id="75237-117">Description</span><span class="sxs-lookup"><span data-stu-id="75237-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="75237-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="75237-118">0x80041001</span></span> | <span data-ttu-id="75237-119">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="75237-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="75237-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="75237-120">0x80041008</span></span> | <span data-ttu-id="75237-121">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="75237-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="75237-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="75237-122">0x8004101d</span></span> | <span data-ttu-id="75237-123">Un deuxième appel à `BeginEnumeration` a été effectuée sans appel intermédiaire à [ `EndEnumeration` ](endenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="75237-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="75237-124">0</span><span class="sxs-lookup"><span data-stu-id="75237-124">0</span></span> | <span data-ttu-id="75237-125">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="75237-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="75237-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="75237-126">0x40003</span></span> | <span data-ttu-id="75237-127">Les objets sont différents.</span><span class="sxs-lookup"><span data-stu-id="75237-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="75237-128">0</span><span class="sxs-lookup"><span data-stu-id="75237-128">0</span></span> | <span data-ttu-id="75237-129">Les objets sont identiques selon les indicateurs de comparaison.</span><span class="sxs-lookup"><span data-stu-id="75237-129">The objects are the same based on the comparison flags.</span></span> |

## <a name="remarks"></a><span data-ttu-id="75237-130">Notes</span><span class="sxs-lookup"><span data-stu-id="75237-130">Remarks</span></span>

<span data-ttu-id="75237-131">Cette fonction encapsule un appel à la [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) (méthode).</span><span class="sxs-lookup"><span data-stu-id="75237-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="75237-132">Les indicateurs qui peuvent être passés en tant que le `lEnumFlags` argument sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="75237-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="75237-133">Vous pouvez spécifier les caractéristiques individuelles impliquées dans la comparaison en spécifiant une combinaison au niveau du bit des indicateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="75237-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="75237-134">Constante</span><span class="sxs-lookup"><span data-stu-id="75237-134">Constant</span></span>  |<span data-ttu-id="75237-135">Value</span><span class="sxs-lookup"><span data-stu-id="75237-135">Value</span></span>  |<span data-ttu-id="75237-136">Description</span><span class="sxs-lookup"><span data-stu-id="75237-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="75237-137">2</span><span class="sxs-lookup"><span data-stu-id="75237-137">2</span></span> | <span data-ttu-id="75237-138">Ignorer la source (le serveur et l’espace de noms que dont elles sont issues).</span><span class="sxs-lookup"><span data-stu-id="75237-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="75237-139">1</span><span class="sxs-lookup"><span data-stu-id="75237-139">1</span></span> | <span data-ttu-id="75237-140">Ignorer tous les qualificateurs (y compris **clé** et **dynamique**)</span><span class="sxs-lookup"><span data-stu-id="75237-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="75237-141">4</span><span class="sxs-lookup"><span data-stu-id="75237-141">4</span></span> | <span data-ttu-id="75237-142">Ignorer les valeurs par défaut des propriétés.</span><span class="sxs-lookup"><span data-stu-id="75237-142">Ignore default values of properties.</span></span> <span data-ttu-id="75237-143">Cet indicateur s’applique uniquement à la comparaison des classes.</span><span class="sxs-lookup"><span data-stu-id="75237-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="75237-144">0x20</span><span class="sxs-lookup"><span data-stu-id="75237-144">0x20</span></span> | <span data-ttu-id="75237-145">Ignorer les versions de qualificateur.</span><span class="sxs-lookup"><span data-stu-id="75237-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="75237-146">Cet indicateur toujours tienne compte, de qualificateurs mais ignore les distinctions de version telles que les règles de propagation et remplace les restrictions.</span><span class="sxs-lookup"><span data-stu-id="75237-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="75237-147">0x10</span><span class="sxs-lookup"><span data-stu-id="75237-147">0x10</span></span> | <span data-ttu-id="75237-148">Ignorer la casse pour comparer les valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="75237-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="75237-149">Cela s’applique à la fois aux chaînes et aux valeurs de qualificateur.</span><span class="sxs-lookup"><span data-stu-id="75237-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="75237-150">La comparaison des noms de propriété et le qualificateur est toujours la casse, même si cet indicateur est défini.</span><span class="sxs-lookup"><span data-stu-id="75237-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="75237-151">0x8</span><span class="sxs-lookup"><span data-stu-id="75237-151">0x8</span></span> | <span data-ttu-id="75237-152">Supposons que les objets comparés sont des instances de la même classe.</span><span class="sxs-lookup"><span data-stu-id="75237-152">Assume that the objects being compared are instances of the same class.</span></span> <span data-ttu-id="75237-153">Par conséquent, cet indicateur compare uniquement des informations relatives aux instances.</span><span class="sxs-lookup"><span data-stu-id="75237-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="75237-154">Utilisez cette indicateurs pour optimiser les performances.</span><span class="sxs-lookup"><span data-stu-id="75237-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="75237-155">Si les objets ne sont pas de la même classe, les résultats sont indéfinis.</span><span class="sxs-lookup"><span data-stu-id="75237-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="75237-156">Ou vous pouvez spécifier un indicateur composite unique comme suit :</span><span class="sxs-lookup"><span data-stu-id="75237-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="75237-157">Constante</span><span class="sxs-lookup"><span data-stu-id="75237-157">Constant</span></span>  |<span data-ttu-id="75237-158">Value</span><span class="sxs-lookup"><span data-stu-id="75237-158">Value</span></span>  |<span data-ttu-id="75237-159">Description</span><span class="sxs-lookup"><span data-stu-id="75237-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="75237-160">0</span><span class="sxs-lookup"><span data-stu-id="75237-160">0</span></span> | <span data-ttu-id="75237-161">Prendre en compte toutes les fonctionnalités dans la comparaison.</span><span class="sxs-lookup"><span data-stu-id="75237-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="75237-162">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="75237-162">Requirements</span></span>

<span data-ttu-id="75237-163">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75237-163">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="75237-164">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="75237-164">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="75237-165">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="75237-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="75237-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="75237-166">See also</span></span>

- [<span data-ttu-id="75237-167">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="75237-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
