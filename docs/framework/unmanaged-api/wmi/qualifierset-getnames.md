---
title: Fonction QualifierSet_GetNames (référence des API non managées)
description: La fonction QualifierSet_GetNames récupère les noms des qualificateurs d’un objet ou d’une propriété.
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
ms.openlocfilehash: bd0a67987dd8ffa825114726d066249aed40cf05
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141693"
---
# <a name="qualifierset_getnames-function"></a><span data-ttu-id="0b4b0-103">QualifierSet_GetNames fonction)</span><span class="sxs-lookup"><span data-stu-id="0b4b0-103">QualifierSet_GetNames function</span></span>

<span data-ttu-id="0b4b0-104">Récupère les noms de tous les qualificateurs ou de certains qualificateurs disponibles à partir de la propriété ou de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-104">Retrieves the names of all the qualifiers or of certain qualifiers that are available from the current object or property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0b4b0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b4b0-105">Syntax</span></span>

```cpp
HRESULT QualifierSet_GetNames (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LONG                 lFlags,
   [out] SAFEARRAY (BSTR)**  pstrNames
);
```

## <a name="parameters"></a><span data-ttu-id="0b4b0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0b4b0-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="0b4b0-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="0b4b0-108">dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="0b4b0-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`\
<span data-ttu-id="0b4b0-109">dans L’un des indicateurs ou valeurs suivants qui spécifient les noms à inclure dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-109">[in] One of the following flags or values that specifies which names to include in the enumeration.</span></span>

|<span data-ttu-id="0b4b0-110">Constante</span><span class="sxs-lookup"><span data-stu-id="0b4b0-110">Constant</span></span>  |<span data-ttu-id="0b4b0-111">valeur</span><span class="sxs-lookup"><span data-stu-id="0b4b0-111">Value</span></span>  |<span data-ttu-id="0b4b0-112">Description</span><span class="sxs-lookup"><span data-stu-id="0b4b0-112">Description</span></span>  |
|---------|---------|---------|
|  | <span data-ttu-id="0b4b0-113">0</span><span class="sxs-lookup"><span data-stu-id="0b4b0-113">0</span></span> | <span data-ttu-id="0b4b0-114">Retourne les noms de tous les qualificateurs.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-114">Return the names of all qualifiers.</span></span> |
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="0b4b0-115">0x10</span><span class="sxs-lookup"><span data-stu-id="0b4b0-115">0x10</span></span> | <span data-ttu-id="0b4b0-116">Retourne uniquement les noms des qualificateurs spécifiques à la propriété ou à l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-116">Return only the names of qualifiers specific to the current property or object.</span></span> <br/> <span data-ttu-id="0b4b0-117">Pour une propriété : retourner uniquement les qualificateurs spécifiques à la propriété (y compris les substitutions), et non les qualificateurs propagés à partir de la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-117">For a property: Return only the qualifiers specific to the property (including overrides), and not those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="0b4b0-118">Pour une instance : retourner uniquement des noms de qualificateurs spécifiques à l’instance.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-118">For an instance: Return only instance-specific qualifier names.</span></span> <br/> <span data-ttu-id="0b4b0-119">Pour une classe : retourne uniquement les qualificateurs spécifiques à la classe qui est dérivée.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-119">For a class: Return only qualifiers specific to the class being derived.</span></span>
|`WBEM_FLAG_PROPAGATED_ONLY` | <span data-ttu-id="0b4b0-120">0x20</span><span class="sxs-lookup"><span data-stu-id="0b4b0-120">0x20</span></span> | <span data-ttu-id="0b4b0-121">Retourne uniquement les noms des qualificateurs propagés à partir d’un autre objet.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-121">Return only the names of qualifiers propagated from another object.</span></span> <br/> <span data-ttu-id="0b4b0-122">Pour une propriété : Retournez uniquement les qualificateurs propagés à cette propriété à partir de la définition de classe, et non ceux de la propriété elle-même.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-122">For a property: Return only the qualifiers propagated to this property from the class definition, and not those from the property itself.</span></span> <br/> <span data-ttu-id="0b4b0-123">Pour une instance : retourner uniquement les qualificateurs propagés à partir de la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-123">For an instance: Return only those qualifiers propagated from the class definition.</span></span> <br/> <span data-ttu-id="0b4b0-124">Pour une classe : Retournez uniquement les noms de qualificateur hérités des classes parentes.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-124">For a class: Return only those qualifier names inherited from the parent classes.</span></span> |

`pstrNames`\
<span data-ttu-id="0b4b0-125">à Nouvelle `SAFEARRAY` qui contient les noms demandés.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-125">[out] A new `SAFEARRAY` that contains the requested names.</span></span> <span data-ttu-id="0b4b0-126">Le tableau peut avoir 0 élément.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-126">The array can have 0 elements.</span></span> <span data-ttu-id="0b4b0-127">Si une erreur se produit, une nouvelle `SAFEARRAY` n’est pas retournée.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-127">If an error occurs, a new `SAFEARRAY` is not returned.</span></span>

## <a name="return-value"></a><span data-ttu-id="0b4b0-128">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="0b4b0-128">Return value</span></span>

<span data-ttu-id="0b4b0-129">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="0b4b0-129">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0b4b0-130">Constante</span><span class="sxs-lookup"><span data-stu-id="0b4b0-130">Constant</span></span>  |<span data-ttu-id="0b4b0-131">valeur</span><span class="sxs-lookup"><span data-stu-id="0b4b0-131">Value</span></span>  |<span data-ttu-id="0b4b0-132">Description</span><span class="sxs-lookup"><span data-stu-id="0b4b0-132">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0b4b0-133">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0b4b0-133">0x80041008</span></span> | <span data-ttu-id="0b4b0-134">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-134">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0b4b0-135">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0b4b0-135">0x80041006</span></span> | <span data-ttu-id="0b4b0-136">Mémoire disponible insuffisante pour commencer une nouvelle énumération.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-136">Not enough memory is available to begin a new enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0b4b0-137">0</span><span class="sxs-lookup"><span data-stu-id="0b4b0-137">0</span></span> | <span data-ttu-id="0b4b0-138">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-138">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="0b4b0-139">Notes</span><span class="sxs-lookup"><span data-stu-id="0b4b0-139">Remarks</span></span>

<span data-ttu-id="0b4b0-140">Cette fonction encapsule un appel à la méthode [IWbemQualifierSet :: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) .</span><span class="sxs-lookup"><span data-stu-id="0b4b0-140">This function wraps a call to the [IWbemQualifierSet::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-getnames) method.</span></span>

<span data-ttu-id="0b4b0-141">Une fois que vous avez récupéré les noms de qualificateurs, vous pouvez accéder à chaque qualificateur par son nom en appelant la fonction [QualifierSet_Get](qualifierset-get.md) .</span><span class="sxs-lookup"><span data-stu-id="0b4b0-141">Once you've retrieved the qualifier names, you can access each qualifier by name by calling the [QualifierSet_Get](qualifierset-get.md) function.</span></span>

<span data-ttu-id="0b4b0-142">Il n’y a pas d’erreur pour un objet donné à avoir des qualificateurs nuls, donc le nombre de chaînes dans `pstrNames` au retour peut être 0, même si la fonction retourne `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="0b4b0-142">It is not an error for a given object to have zero qualifiers, so the number of strings in `pstrNames` on return can be 0, even though the function returns `WBEM_S_NO_ERROR`.</span></span>

## <a name="requirements"></a><span data-ttu-id="0b4b0-143">spécifications</span><span class="sxs-lookup"><span data-stu-id="0b4b0-143">Requirements</span></span>

<span data-ttu-id="0b4b0-144">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b4b0-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="0b4b0-145">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="0b4b0-145">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="0b4b0-146">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0b4b0-146">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0b4b0-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0b4b0-147">See also</span></span>

- [<span data-ttu-id="0b4b0-148">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="0b4b0-148">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
