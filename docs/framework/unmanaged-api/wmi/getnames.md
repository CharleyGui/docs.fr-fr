---
title: Fonction GetNames (référence API non gestion)
description: La fonction GetNames récupère les noms des propriétés d’un objet.
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 449f0ce9c291d4bbcad4947214e56ff46f55beed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174951"
---
# <a name="getnames-function"></a><span data-ttu-id="0950f-103">GetNames, fonction</span><span class="sxs-lookup"><span data-stu-id="0950f-103">GetNames function</span></span>
<span data-ttu-id="0950f-104">Récupère une partie ou l’ensemble des noms des propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="0950f-104">Retrieves either a subset or all of the names of the properties of an object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="0950f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0950f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
);
```  

## <a name="parameters"></a><span data-ttu-id="0950f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0950f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="0950f-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="0950f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="0950f-108">[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="0950f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="0950f-109">[dans] Un pointeur `LPCWSTR` à un valide qui spécifie un nom qualificatif qui fonctionne dans le cadre d’un filtre.</span><span class="sxs-lookup"><span data-stu-id="0950f-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="0950f-110">Pour plus d’informations, consultez la section [Remarques.](#remarks)</span><span class="sxs-lookup"><span data-stu-id="0950f-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="0950f-111">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="0950f-111">This parameter can be `null`.</span></span>

`lFlags`  
<span data-ttu-id="0950f-112">[dans] Une combinaison de champs de bits.</span><span class="sxs-lookup"><span data-stu-id="0950f-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="0950f-113">Pour plus d’informations, consultez la section [Remarques.](#remarks)</span><span class="sxs-lookup"><span data-stu-id="0950f-113">For more information, see the [Remarks](#remarks) section.</span></span>

<span data-ttu-id="0950f-114">`pQualifierValue`[dans] Un pointeur `VARIANT` vers une structure valide paralysée à une valeur de filtre.</span><span class="sxs-lookup"><span data-stu-id="0950f-114">`pQualifierValue` [in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="0950f-115">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="0950f-115">This parameter can be `null`.</span></span>

`pstrNames`  
<span data-ttu-id="0950f-116">[out] Une `SAFEARRAY` structure qui contient des noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="0950f-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="0950f-117">À l’entrée, ce paramètre `null`doit toujours être un pointeur à .</span><span class="sxs-lookup"><span data-stu-id="0950f-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="0950f-118">Consultez la section [Remarques](#remarks) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="0950f-118">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="0950f-119">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="0950f-119">Return value</span></span>

<span data-ttu-id="0950f-120">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="0950f-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="0950f-121">Constant</span><span class="sxs-lookup"><span data-stu-id="0950f-121">Constant</span></span>  |<span data-ttu-id="0950f-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="0950f-122">Value</span></span>  |<span data-ttu-id="0950f-123">Description</span><span class="sxs-lookup"><span data-stu-id="0950f-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="0950f-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="0950f-124">0x80041001</span></span> | <span data-ttu-id="0950f-125">Il y a eu un échec général.</span><span class="sxs-lookup"><span data-stu-id="0950f-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="0950f-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="0950f-126">0x80041008</span></span> | <span data-ttu-id="0950f-127">Un ou plusieurs paramètres ne sont pas valides, ou une combinaison incorrecte de drapeaux et de paramètres a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0950f-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="0950f-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="0950f-128">0x80041006</span></span> | <span data-ttu-id="0950f-129">La mémoire n'est pas suffisante pour terminer cette opération.</span><span class="sxs-lookup"><span data-stu-id="0950f-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="0950f-130">0</span><span class="sxs-lookup"><span data-stu-id="0950f-130">0</span></span> | <span data-ttu-id="0950f-131">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="0950f-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="0950f-132">Notes </span><span class="sxs-lookup"><span data-stu-id="0950f-132">Remarks</span></span>

<span data-ttu-id="0950f-133">Cette fonction enveloppe un appel à [l’IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) méthode.</span><span class="sxs-lookup"><span data-stu-id="0950f-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="0950f-134">Les personnes nommées sont contrôlées par une combinaison de drapeaux et de paramètres.</span><span class="sxs-lookup"><span data-stu-id="0950f-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="0950f-135">Par exemple, la fonction peut retourner les noms de toutes les propriétés ou seulement les noms des propriétés clés.</span><span class="sxs-lookup"><span data-stu-id="0950f-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="0950f-136">Le filtre principal est `lFlags` spécifié dans le paramètre, et les autres paramètres varient en fonction de lui.</span><span class="sxs-lookup"><span data-stu-id="0950f-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="0950f-137">Les valeurs `lFlags` du drapeau sont des champs bits</span><span class="sxs-lookup"><span data-stu-id="0950f-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="0950f-138">Les drapeaux qui peuvent `lEnumFlags` être passés comme l’argument sont des champs bit qui sont définis dans le fichier *d’en-tête WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="0950f-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="0950f-139">Vous pouvez combiner un drapeau de chaque groupe avec n’importe quel drapeau de n’importe quel autre groupe.</span><span class="sxs-lookup"><span data-stu-id="0950f-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="0950f-140">Cependant, les drapeaux du même groupe s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="0950f-140">However, flags from the same group are mutually exclusive.</span></span>

| <span data-ttu-id="0950f-141">Drapeaux du groupe 1</span><span class="sxs-lookup"><span data-stu-id="0950f-141">Group 1 flags</span></span> |<span data-ttu-id="0950f-142">Valeur</span><span class="sxs-lookup"><span data-stu-id="0950f-142">Value</span></span>  |<span data-ttu-id="0950f-143">Description</span><span class="sxs-lookup"><span data-stu-id="0950f-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="0950f-144">0</span><span class="sxs-lookup"><span data-stu-id="0950f-144">0</span></span> | <span data-ttu-id="0950f-145">Retournez tous les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="0950f-145">Return all property names.</span></span> <span data-ttu-id="0950f-146">`strQualifierName`et `pQualifierVal` sont inutilisés.</span><span class="sxs-lookup"><span data-stu-id="0950f-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="0950f-147">1</span><span class="sxs-lookup"><span data-stu-id="0950f-147">1</span></span> | <span data-ttu-id="0950f-148">Retournez uniquement les propriétés qui ont `strQualifierName` un qualificatif du nom spécifié par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="0950f-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="0950f-149">Si ce drapeau est utilisé, vous devez spécifier `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="0950f-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="0950f-150">2</span><span class="sxs-lookup"><span data-stu-id="0950f-150">2</span></span> |  <span data-ttu-id="0950f-151">Retournez uniquement les propriétés qui n’ont `strQualifierName` pas de qualification du nom spécifiée par le paramètre.</span><span class="sxs-lookup"><span data-stu-id="0950f-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="0950f-152">Si ce drapeau est utilisé, vous devez spécifier `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="0950f-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="0950f-153">3</span><span class="sxs-lookup"><span data-stu-id="0950f-153">3</span></span> | <span data-ttu-id="0950f-154">Retournez uniquement les propriétés qui ont `wszQualifierName` un qualificatif du nom `pQualifierVal` spécifié par le paramètre et ont également une valeur identique à celle spécifiée par la structure.</span><span class="sxs-lookup"><span data-stu-id="0950f-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="0950f-155">Si ce drapeau est utilisé, `wszQualifierName` vous `pQualifierValue`devez spécifier à la fois un et un .</span><span class="sxs-lookup"><span data-stu-id="0950f-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="0950f-156">Drapeaux du groupe 2</span><span class="sxs-lookup"><span data-stu-id="0950f-156">Group 2 flags</span></span> |<span data-ttu-id="0950f-157">Valeur</span><span class="sxs-lookup"><span data-stu-id="0950f-157">Value</span></span>  |<span data-ttu-id="0950f-158">Description</span><span class="sxs-lookup"><span data-stu-id="0950f-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="0950f-159">0x4</span><span class="sxs-lookup"><span data-stu-id="0950f-159">0x4</span></span> | <span data-ttu-id="0950f-160">Ne retournez que les noms des propriétés qui définissent les clés.</span><span class="sxs-lookup"><span data-stu-id="0950f-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="0950f-161">0x8</span><span class="sxs-lookup"><span data-stu-id="0950f-161">0x8</span></span> | <span data-ttu-id="0950f-162">Ne retournez que les noms de propriété qui sont des références d’objet.</span><span class="sxs-lookup"><span data-stu-id="0950f-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="0950f-163">Drapeaux du groupe 3</span><span class="sxs-lookup"><span data-stu-id="0950f-163">Group 3 flags</span></span> |<span data-ttu-id="0950f-164">Valeur</span><span class="sxs-lookup"><span data-stu-id="0950f-164">Value</span></span>  |<span data-ttu-id="0950f-165">Description</span><span class="sxs-lookup"><span data-stu-id="0950f-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="0950f-166">0x10</span><span class="sxs-lookup"><span data-stu-id="0950f-166">0x10</span></span> | <span data-ttu-id="0950f-167">Ne retournez que les noms de propriété qui appartiennent à la classe la plus dérivée.</span><span class="sxs-lookup"><span data-stu-id="0950f-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="0950f-168">Exclure les propriétés des classes parentales.</span><span class="sxs-lookup"><span data-stu-id="0950f-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="0950f-169">0x20</span><span class="sxs-lookup"><span data-stu-id="0950f-169">0x20</span></span> | <span data-ttu-id="0950f-170">Ne retournez que les noms de propriété qui appartiennent aux classes de parents.</span><span class="sxs-lookup"><span data-stu-id="0950f-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="0950f-171">0x30</span><span class="sxs-lookup"><span data-stu-id="0950f-171">0x30</span></span> | <span data-ttu-id="0950f-172">Ne retournez que les noms des propriétés du système.</span><span class="sxs-lookup"><span data-stu-id="0950f-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="0950f-173">0x40</span><span class="sxs-lookup"><span data-stu-id="0950f-173">0x40</span></span> | <span data-ttu-id="0950f-174">Ne retournez que les noms des propriétés non système.</span><span class="sxs-lookup"><span data-stu-id="0950f-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="0950f-175">La fonction alloue `SAFEARRAY` toujours `WBEM_S_NO_ERROR`un `pstrNames` nouveau si elle revient, et est toujours mis à lui pointer du point.</span><span class="sxs-lookup"><span data-stu-id="0950f-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="0950f-176">Le tableau retourné peut avoir 0 éléments si aucune propriété ne correspond aux filtres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="0950f-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="0950f-177">Si la fonction retourne `WBM_S_NO_ERROR`une valeur `SAFEARRAY` autre que , une nouvelle structure n’est pas retournée.</span><span class="sxs-lookup"><span data-stu-id="0950f-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="0950f-178">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0950f-178">Requirements</span></span>  
 <span data-ttu-id="0950f-179">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0950f-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0950f-180">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="0950f-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="0950f-181">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0950f-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0950f-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0950f-182">See also</span></span>

- [<span data-ttu-id="0950f-183">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="0950f-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
