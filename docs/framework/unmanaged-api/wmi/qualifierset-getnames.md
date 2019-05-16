---
title: QualifierSet_GetNames (fonction) (référence des API non managées)
description: La fonction QualifierSet_GetNames récupère les noms des qualificateurs à partir d’un objet ou une propriété.
ms.date: 11/06/2017
api_name:
- QualifierSet_GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_GetNames
helpviewer_keywords:
- QualifierSet_GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 402d56b44c2b6f53f901e35c6d7b965811a40344
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636593"
---
# <a name="qualifiersetgetnames-function"></a><span data-ttu-id="791ee-103">QualifierSet_GetNames function</span><span class="sxs-lookup"><span data-stu-id="791ee-103">QualifierSet_GetNames function</span></span>

<span data-ttu-id="791ee-104">Récupère les noms de tous les qualificateurs ou de certains qualificateurs qui sont disponibles à partir de l’objet en cours ou de la propriété.</span><span class="sxs-lookup"><span data-stu-id="791ee-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="791ee-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="791ee-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a><span data-ttu-id="791ee-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="791ee-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="791ee-107">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="791ee-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="791ee-108">[in] Un pointeur vers un [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="791ee-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="791ee-109">[in] Un des indicateurs ou des valeurs qui spécifie les noms à inclure dans l’énumération suivante.</span><span class="sxs-lookup"><span data-stu-id="791ee-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="791ee-110">Constante</span><span class="sxs-lookup"><span data-stu-id="791ee-110">Constant</span></span>  |<span data-ttu-id="791ee-111">Value</span><span class="sxs-lookup"><span data-stu-id="791ee-111">Value</span></span>  |<span data-ttu-id="791ee-112">Description</span><span class="sxs-lookup"><span data-stu-id="791ee-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="791ee-113">0</span><span class="sxs-lookup"><span data-stu-id="791ee-113">0</span></span> | <span data-ttu-id="791ee-114">Retourner les noms de tous les qualificateurs.</span><span class="sxs-lookup"><span data-stu-id="791ee-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="791ee-115">0x10</span><span class="sxs-lookup"><span data-stu-id="791ee-115">0x10</span></span> | <span data-ttu-id="791ee-116">Retourner uniquement les noms des qualificateurs spécifiques à l’objet ou la propriété actuelle.</span><span class="sxs-lookup"><span data-stu-id="791ee-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="791ee-117">Pour une propriété : Retourner uniquement les qualificateurs spécifiques à la propriété (y compris les substitutions) et pas ces qualificateurs propagés à partir de la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="791ee-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="791ee-118">Pour une instance : Retourner uniquement les noms d’un qualificateur de nom spécifique à l’instance.</span><span class="sxs-lookup"><span data-stu-id="791ee-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="791ee-119">Pour une classe : Retourner uniquement des qualificateurs spécifiques à la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="791ee-119">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="791ee-120">0x20</span><span class="sxs-lookup"><span data-stu-id="791ee-120">0x20</span></span> | <span data-ttu-id="791ee-121">Retour uniquement les noms des qualificateurs propagés à partir d’un autre objet.</span><span class="sxs-lookup"><span data-stu-id="791ee-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="791ee-122">Pour une propriété : Retour uniquement les qualificateurs propagées à cette propriété à partir de la définition de classe et non celles de la propriété proprement dite.</span><span class="sxs-lookup"><span data-stu-id="791ee-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="791ee-123">Pour une instance : Retour uniquement ces qualificateurs propagés à partir de la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="791ee-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="791ee-124">Pour une classe : Retour uniquement les noms de qualificateur héritées des classes parentes.</span><span class="sxs-lookup"><span data-stu-id="791ee-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

`pstrNames`\
<span data-ttu-id="791ee-125">[out] Un nouveau `SAFEARRAY` qui contient les noms demandés.</span><span class="sxs-lookup"><span data-stu-id="791ee-125">[out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="791ee-126">Le tableau peut avoir 0 éléments.</span><span class="sxs-lookup"><span data-stu-id="791ee-126">The array can have 0 elements.</span></span> <span data-ttu-id="791ee-127">Si une erreur se produit, un nouveau `SAFEARRAY` n’est pas retournée.</span><span class="sxs-lookup"><span data-stu-id="791ee-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="791ee-128">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="791ee-128">Return value</span></span>

<span data-ttu-id="791ee-129">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="791ee-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="791ee-130">Constante</span><span class="sxs-lookup"><span data-stu-id="791ee-130">Constant</span></span>  |<span data-ttu-id="791ee-131">Value</span><span class="sxs-lookup"><span data-stu-id="791ee-131">Value</span></span>  |<span data-ttu-id="791ee-132">Description</span><span class="sxs-lookup"><span data-stu-id="791ee-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="791ee-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="791ee-133">0x80041008</span></span> | <span data-ttu-id="791ee-134">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="791ee-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="791ee-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="791ee-135">0x80041006</span></span> | <span data-ttu-id="791ee-136">Pas assez de mémoire est disponible pour commencer une nouvelle énumération.</span><span class="sxs-lookup"><span data-stu-id="791ee-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="791ee-137">0</span><span class="sxs-lookup"><span data-stu-id="791ee-137">0</span></span> | <span data-ttu-id="791ee-138">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="791ee-138">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="791ee-139">Notes</span><span class="sxs-lookup"><span data-stu-id="791ee-139">Remarks</span></span>

<span data-ttu-id="791ee-140">Cette fonction encapsule un appel à la [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) (méthode).</span><span class="sxs-lookup"><span data-stu-id="791ee-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="791ee-141">Une fois que vous avez extrait les noms de qualificateur, vous pouvez accéder à chaque qualificateur par nom, en appelant le [QualifierSet_Get](qualifierset-get.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="791ee-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span>

<span data-ttu-id="791ee-142">Il n’est pas une erreur pour un objet donné pour que les qualificateurs de zéro, par conséquent, le nombre de chaînes dans `pstrNames` en retour peut être 0, même si la fonction retourne `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="791ee-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="791ee-143">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="791ee-143">Requirements</span></span>

<span data-ttu-id="791ee-144">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="791ee-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="791ee-145">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="791ee-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="791ee-146">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="791ee-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="791ee-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="791ee-147">See also</span></span>

- [<span data-ttu-id="791ee-148">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="791ee-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
