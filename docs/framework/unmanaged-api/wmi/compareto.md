---
title: CompareTo, fonction (référence des API non managées)
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
ms.openlocfilehash: 2ec42dff333422e247a11b4a3a5b9aed9bd316fa
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798772"
---
# <a name="compareto-function"></a><span data-ttu-id="df40d-103">CompareTo, fonction</span><span class="sxs-lookup"><span data-stu-id="df40d-103">CompareTo function</span></span>

<span data-ttu-id="df40d-104">Compare un objet à un autre objet WMI.</span><span class="sxs-lookup"><span data-stu-id="df40d-104">Compares an object to another Windows management object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="df40d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df40d-105">Syntax</span></span>

```cpp
HRESULT CompareTo (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              flags,
   [in] IWbemClassObject* pCompareTo
);
```

## <a name="parameters"></a><span data-ttu-id="df40d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df40d-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="df40d-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="df40d-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="df40d-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="df40d-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`flags`\
<span data-ttu-id="df40d-109">dans Combinaison d’opérations de bits des indicateurs qui spécifient les caractéristiques d’objet à prendre en compte pour la comparaison.</span><span class="sxs-lookup"><span data-stu-id="df40d-109">[in] A bitwise combination of the flags that specify the object characteristics to consider for the comparison.</span></span> <span data-ttu-id="df40d-110">Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="df40d-110">See the [Remarks](#remarks) section for more information.</span></span>

`pCompareTo`\
<span data-ttu-id="df40d-111">dans Objet à comparer.</span><span class="sxs-lookup"><span data-stu-id="df40d-111">[in] The object for comparison.</span></span> <span data-ttu-id="df40d-112">`pCompareTo`doit être une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) valide ; elle ne peut `null`pas être.</span><span class="sxs-lookup"><span data-stu-id="df40d-112">`pCompareTo` must be a valid [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance; it cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="df40d-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="df40d-113">Return value</span></span>

<span data-ttu-id="df40d-114">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="df40d-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="df40d-115">Constante</span><span class="sxs-lookup"><span data-stu-id="df40d-115">Constant</span></span>  |<span data-ttu-id="df40d-116">`Value`</span><span class="sxs-lookup"><span data-stu-id="df40d-116">Value</span></span>  |<span data-ttu-id="df40d-117">Description</span><span class="sxs-lookup"><span data-stu-id="df40d-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="df40d-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="df40d-118">0x80041001</span></span> | <span data-ttu-id="df40d-119">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="df40d-119">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="df40d-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="df40d-120">0x80041008</span></span> | <span data-ttu-id="df40d-121">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="df40d-121">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="df40d-122">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="df40d-122">0x8004101d</span></span> | <span data-ttu-id="df40d-123">Un deuxième appel à `BeginEnumeration` a été effectué sans appel à. [`EndEnumeration`](endenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="df40d-123">A second call to `BeginEnumeration` was made without an intervening call to [`EndEnumeration`](endenumeration.md).</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="df40d-124">0</span><span class="sxs-lookup"><span data-stu-id="df40d-124">0</span></span> | <span data-ttu-id="df40d-125">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="df40d-125">The function call was successful.</span></span>  |
| `WBEM_S_DIFFERENT` | <span data-ttu-id="df40d-126">0x40003</span><span class="sxs-lookup"><span data-stu-id="df40d-126">0x40003</span></span> | <span data-ttu-id="df40d-127">Les objets sont différents.</span><span class="sxs-lookup"><span data-stu-id="df40d-127">The objects are different.</span></span> |
| `WBEM_S_SAME` | <span data-ttu-id="df40d-128">0</span><span class="sxs-lookup"><span data-stu-id="df40d-128">0</span></span> | <span data-ttu-id="df40d-129">Les objets sont les mêmes en fonction des indicateurs de comparaison.</span><span class="sxs-lookup"><span data-stu-id="df40d-129">The objects are the same based on the comparison flags.</span></span> |

## <a name="remarks"></a><span data-ttu-id="df40d-130">Notes</span><span class="sxs-lookup"><span data-stu-id="df40d-130">Remarks</span></span>

<span data-ttu-id="df40d-131">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) .</span><span class="sxs-lookup"><span data-stu-id="df40d-131">This function wraps a call to the [IWbemClassObject::CompareTo](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-compareto) method.</span></span>

<span data-ttu-id="df40d-132">Les indicateurs qui peuvent être passés en tant `lEnumFlags` qu’argument sont définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="df40d-132">The flags that can be passed as the `lEnumFlags` argument are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span> <span data-ttu-id="df40d-133">Vous pouvez spécifier les caractéristiques individuelles impliquées dans la comparaison en spécifiant une combinaison d’opérations de bits des indicateurs suivants :</span><span class="sxs-lookup"><span data-stu-id="df40d-133">You can specify the individual characteristics involved in the comparison by specifying a bitwise combination of the following flags:</span></span>

|<span data-ttu-id="df40d-134">Constante</span><span class="sxs-lookup"><span data-stu-id="df40d-134">Constant</span></span>  |<span data-ttu-id="df40d-135">`Value`</span><span class="sxs-lookup"><span data-stu-id="df40d-135">Value</span></span>  |<span data-ttu-id="df40d-136">Description</span><span class="sxs-lookup"><span data-stu-id="df40d-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_IGNORE_OBJECT_SOURCE` | <span data-ttu-id="df40d-137">2</span><span class="sxs-lookup"><span data-stu-id="df40d-137">2</span></span> | <span data-ttu-id="df40d-138">Ignorez la source (le serveur et l’espace de noms à partir desquels ils proviennent).</span><span class="sxs-lookup"><span data-stu-id="df40d-138">Ignore the source (the server and the namespace they came from).</span></span> |
| `WBEM_FLAG_IGNORE_QUALIFIERS` | <span data-ttu-id="df40d-139">1</span><span class="sxs-lookup"><span data-stu-id="df40d-139">1</span></span> | <span data-ttu-id="df40d-140">Ignorer tous les qualificateurs (y compris les **clés** et **dynamiques**)</span><span class="sxs-lookup"><span data-stu-id="df40d-140">Ignore all qualifiers (including **Key** and **Dynamic**)</span></span> |
| `WBEM_FLAG_IGNORE_DEFAULT_VALUES` | <span data-ttu-id="df40d-141">4</span><span class="sxs-lookup"><span data-stu-id="df40d-141">4</span></span> | <span data-ttu-id="df40d-142">Ignore les valeurs par défaut des propriétés.</span><span class="sxs-lookup"><span data-stu-id="df40d-142">Ignore default values of properties.</span></span> <span data-ttu-id="df40d-143">Cet indicateur s’applique uniquement à la comparaison des classes.</span><span class="sxs-lookup"><span data-stu-id="df40d-143">This flag only applies to comparison of classes.</span></span> |
| `WBEM_FLAG_IGNORE_FLAVOR` | <span data-ttu-id="df40d-144">0x20</span><span class="sxs-lookup"><span data-stu-id="df40d-144">0x20</span></span> | <span data-ttu-id="df40d-145">Ignore les versions de qualificateur.</span><span class="sxs-lookup"><span data-stu-id="df40d-145">Ignore qualifier flavors.</span></span> <span data-ttu-id="df40d-146">Cet indicateur prend toujours en compte les qualificateurs, mais ignore les distinctions de parfum telles que les règles de propagation et les restrictions de remplacement.</span><span class="sxs-lookup"><span data-stu-id="df40d-146">This flag still takes qualifiers into account, but ignores flavor distinctions such as propagation rules and override restrictions.</span></span> |
| `WBEM_FLAG_IGNORE_CASE` | <span data-ttu-id="df40d-147">0x10</span><span class="sxs-lookup"><span data-stu-id="df40d-147">0x10</span></span> | <span data-ttu-id="df40d-148">Ignorer la casse lors de la comparaison des valeurs de chaîne.</span><span class="sxs-lookup"><span data-stu-id="df40d-148">Ignore case in comparing string values.</span></span> <span data-ttu-id="df40d-149">Cela s’applique à la fois aux chaînes et aux valeurs de qualificateur.</span><span class="sxs-lookup"><span data-stu-id="df40d-149">This applies both to strings and qualifier values.</span></span> <span data-ttu-id="df40d-150">La comparaison des noms de propriétés et de qualificateurs respecte toujours la casse, que cet indicateur soit défini ou non.</span><span class="sxs-lookup"><span data-stu-id="df40d-150">The comparison of property and qualifier names is always case-sensitive regardless of whether this flag is set.</span></span> |
| `WBEM_FLAG_IGNORE_CLASS` | <span data-ttu-id="df40d-151">0x8</span><span class="sxs-lookup"><span data-stu-id="df40d-151">0x8</span></span> | <span data-ttu-id="df40d-152">Supposons que les objets comparés sont des instances de la même classe.</span><span class="sxs-lookup"><span data-stu-id="df40d-152">Assume that the objects being compared are instances of the same class.</span></span> <span data-ttu-id="df40d-153">Par conséquent, cet indicateur ne compare que les informations relatives à l’instance.</span><span class="sxs-lookup"><span data-stu-id="df40d-153">Consequently, this flag compares instance-related information only.</span></span> <span data-ttu-id="df40d-154">Utilisez cet indicateur pour optimiser les performances.</span><span class="sxs-lookup"><span data-stu-id="df40d-154">Use this flags to optimize performance.</span></span> <span data-ttu-id="df40d-155">Si les objets ne sont pas de la même classe, les résultats ne sont pas définis.</span><span class="sxs-lookup"><span data-stu-id="df40d-155">If the objects are not of the same class, the results are undefined.</span></span> |

<span data-ttu-id="df40d-156">Vous pouvez aussi spécifier un seul indicateur composite comme suit :</span><span class="sxs-lookup"><span data-stu-id="df40d-156">Or you can specify a single composite flag as follows:</span></span>

|<span data-ttu-id="df40d-157">Constante</span><span class="sxs-lookup"><span data-stu-id="df40d-157">Constant</span></span>  |<span data-ttu-id="df40d-158">`Value`</span><span class="sxs-lookup"><span data-stu-id="df40d-158">Value</span></span>  |<span data-ttu-id="df40d-159">Description</span><span class="sxs-lookup"><span data-stu-id="df40d-159">Description</span></span>  |
|---------|---------|---------|
|`WBEM_COMPARISON_INCLUDE_ALL` | <span data-ttu-id="df40d-160">0</span><span class="sxs-lookup"><span data-stu-id="df40d-160">0</span></span> | <span data-ttu-id="df40d-161">Examinez toutes les fonctionnalités de la comparaison.</span><span class="sxs-lookup"><span data-stu-id="df40d-161">Consider all features in the comparison.</span></span> |

## <a name="requirements"></a><span data-ttu-id="df40d-162">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="df40d-162">Requirements</span></span>

<span data-ttu-id="df40d-163">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df40d-163">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="df40d-164">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="df40d-164">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="df40d-165">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="df40d-165">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="df40d-166">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df40d-166">See also</span></span>

- [<span data-ttu-id="df40d-167">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="df40d-167">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
