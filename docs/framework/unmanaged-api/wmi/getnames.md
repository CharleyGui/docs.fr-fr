---
title: Fonction GetNames (référence des API non managées)
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
ms.openlocfilehash: fd889158e61b86f42d88bcf86eda7d816277e6ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687656"
---
# <a name="getnames-function"></a><span data-ttu-id="aa981-103">GetNames, fonction</span><span class="sxs-lookup"><span data-stu-id="aa981-103">GetNames function</span></span>

<span data-ttu-id="aa981-104">Récupère une partie ou l’ensemble des noms des propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="aa981-104">Retrieves either a subset or all of the names of the properties of an object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="aa981-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aa981-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="aa981-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="aa981-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="aa981-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="aa981-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="aa981-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="aa981-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="aa981-109">dans Pointeur vers un valide `LPCWSTR` qui spécifie un nom de qualificateur qui opère dans le cadre d’un filtre.</span><span class="sxs-lookup"><span data-stu-id="aa981-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="aa981-110">Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="aa981-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="aa981-111">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="aa981-111">This parameter can be `null`.</span></span>

`lFlags`  
<span data-ttu-id="aa981-112">dans Combinaison de champs de bits.</span><span class="sxs-lookup"><span data-stu-id="aa981-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="aa981-113">Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="aa981-113">For more information, see the [Remarks](#remarks) section.</span></span>

<span data-ttu-id="aa981-114">`pQualifierValue` dans Pointeur vers une structure valide `VARIANT` initialisée à une valeur de filtre.</span><span class="sxs-lookup"><span data-stu-id="aa981-114">`pQualifierValue` [in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="aa981-115">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="aa981-115">This parameter can be `null`.</span></span>

`pstrNames`  
<span data-ttu-id="aa981-116">à `SAFEARRAY` Structure qui contient des noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="aa981-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="aa981-117">Dans l’entrée, ce paramètre doit toujours être un pointeur vers `null` .</span><span class="sxs-lookup"><span data-stu-id="aa981-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="aa981-118">Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="aa981-118">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="aa981-119">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="aa981-119">Return value</span></span>

<span data-ttu-id="aa981-120">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="aa981-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="aa981-121">Constante</span><span class="sxs-lookup"><span data-stu-id="aa981-121">Constant</span></span>  |<span data-ttu-id="aa981-122">Value</span><span class="sxs-lookup"><span data-stu-id="aa981-122">Value</span></span>  |<span data-ttu-id="aa981-123">Description</span><span class="sxs-lookup"><span data-stu-id="aa981-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="aa981-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="aa981-124">0x80041001</span></span> | <span data-ttu-id="aa981-125">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="aa981-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="aa981-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="aa981-126">0x80041008</span></span> | <span data-ttu-id="aa981-127">Un ou plusieurs paramètres ne sont pas valides ou une combinaison incorrecte d’indicateurs et de paramètres a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="aa981-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="aa981-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="aa981-128">0x80041006</span></span> | <span data-ttu-id="aa981-129">La mémoire n'est pas suffisante pour terminer cette opération.</span><span class="sxs-lookup"><span data-stu-id="aa981-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="aa981-130">0</span><span class="sxs-lookup"><span data-stu-id="aa981-130">0</span></span> | <span data-ttu-id="aa981-131">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="aa981-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="aa981-132">Remarques</span><span class="sxs-lookup"><span data-stu-id="aa981-132">Remarks</span></span>

<span data-ttu-id="aa981-133">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) .</span><span class="sxs-lookup"><span data-stu-id="aa981-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="aa981-134">Le nommé retourné est contrôlé par une combinaison d’indicateurs et de paramètres.</span><span class="sxs-lookup"><span data-stu-id="aa981-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="aa981-135">Par exemple, la fonction peut retourner les noms de toutes les propriétés ou uniquement les noms des propriétés de clé.</span><span class="sxs-lookup"><span data-stu-id="aa981-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="aa981-136">Le filtre principal est spécifié dans le `lFlags` paramètre, et les autres paramètres varient en fonction de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="aa981-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="aa981-137">Les valeurs d’indicateur dans `lFlags` sont des champs de bits</span><span class="sxs-lookup"><span data-stu-id="aa981-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="aa981-138">Les indicateurs qui peuvent être passés en tant qu' `lEnumFlags` argument sont des champs de bits définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="aa981-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="aa981-139">Vous pouvez associer un indicateur de chaque groupe à n’importe quel indicateur de n’importe quel autre groupe.</span><span class="sxs-lookup"><span data-stu-id="aa981-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="aa981-140">Toutefois, les indicateurs du même groupe s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="aa981-140">However, flags from the same group are mutually exclusive.</span></span>

| <span data-ttu-id="aa981-141">Indicateurs du groupe 1</span><span class="sxs-lookup"><span data-stu-id="aa981-141">Group 1 flags</span></span> |<span data-ttu-id="aa981-142">Value</span><span class="sxs-lookup"><span data-stu-id="aa981-142">Value</span></span>  |<span data-ttu-id="aa981-143">Description</span><span class="sxs-lookup"><span data-stu-id="aa981-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="aa981-144">0</span><span class="sxs-lookup"><span data-stu-id="aa981-144">0</span></span> | <span data-ttu-id="aa981-145">Retourne tous les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="aa981-145">Return all property names.</span></span> <span data-ttu-id="aa981-146">`strQualifierName` et `pQualifierVal` sont inutilisés.</span><span class="sxs-lookup"><span data-stu-id="aa981-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="aa981-147">1</span><span class="sxs-lookup"><span data-stu-id="aa981-147">1</span></span> | <span data-ttu-id="aa981-148">Retourne uniquement les propriétés qui ont un qualificateur du nom spécifié par le `strQualifierName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="aa981-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="aa981-149">Si cet indicateur est utilisé, vous devez spécifier `strQualifierName` .</span><span class="sxs-lookup"><span data-stu-id="aa981-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="aa981-150">2</span><span class="sxs-lookup"><span data-stu-id="aa981-150">2</span></span> |  <span data-ttu-id="aa981-151">Retourne uniquement les propriétés qui n’ont pas de qualificateur du nom spécifié par le `strQualifierName` paramètre.</span><span class="sxs-lookup"><span data-stu-id="aa981-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="aa981-152">Si cet indicateur est utilisé, vous devez spécifier `strQualifierName` .</span><span class="sxs-lookup"><span data-stu-id="aa981-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="aa981-153">3</span><span class="sxs-lookup"><span data-stu-id="aa981-153">3</span></span> | <span data-ttu-id="aa981-154">Retourne uniquement les propriétés qui ont un qualificateur du nom spécifié par le `wszQualifierName` paramètre et ont également une valeur identique à celle spécifiée par la `pQualifierVal` structure.</span><span class="sxs-lookup"><span data-stu-id="aa981-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="aa981-155">Si cet indicateur est utilisé, vous devez spécifier à la fois un `wszQualifierName` et un `pQualifierValue` .</span><span class="sxs-lookup"><span data-stu-id="aa981-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="aa981-156">Indicateurs du groupe 2</span><span class="sxs-lookup"><span data-stu-id="aa981-156">Group 2 flags</span></span> |<span data-ttu-id="aa981-157">Value</span><span class="sxs-lookup"><span data-stu-id="aa981-157">Value</span></span>  |<span data-ttu-id="aa981-158">Description</span><span class="sxs-lookup"><span data-stu-id="aa981-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="aa981-159">0x4</span><span class="sxs-lookup"><span data-stu-id="aa981-159">0x4</span></span> | <span data-ttu-id="aa981-160">Retourne uniquement les noms des propriétés qui définissent les clés.</span><span class="sxs-lookup"><span data-stu-id="aa981-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="aa981-161">0x8</span><span class="sxs-lookup"><span data-stu-id="aa981-161">0x8</span></span> | <span data-ttu-id="aa981-162">Retourne uniquement les noms de propriété qui sont des références d’objet.</span><span class="sxs-lookup"><span data-stu-id="aa981-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="aa981-163">Indicateurs du groupe 3</span><span class="sxs-lookup"><span data-stu-id="aa981-163">Group 3 flags</span></span> |<span data-ttu-id="aa981-164">Value</span><span class="sxs-lookup"><span data-stu-id="aa981-164">Value</span></span>  |<span data-ttu-id="aa981-165">Description</span><span class="sxs-lookup"><span data-stu-id="aa981-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="aa981-166">0x10</span><span class="sxs-lookup"><span data-stu-id="aa981-166">0x10</span></span> | <span data-ttu-id="aa981-167">Retourne uniquement les noms de propriété qui appartiennent à la classe la plus dérivée.</span><span class="sxs-lookup"><span data-stu-id="aa981-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="aa981-168">Excluez les propriétés des classes parentes.</span><span class="sxs-lookup"><span data-stu-id="aa981-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="aa981-169">0x20</span><span class="sxs-lookup"><span data-stu-id="aa981-169">0x20</span></span> | <span data-ttu-id="aa981-170">Retourne uniquement les noms de propriété qui appartiennent aux classes parentes.</span><span class="sxs-lookup"><span data-stu-id="aa981-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="aa981-171">0x30</span><span class="sxs-lookup"><span data-stu-id="aa981-171">0x30</span></span> | <span data-ttu-id="aa981-172">Retourne uniquement les noms des propriétés système.</span><span class="sxs-lookup"><span data-stu-id="aa981-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="aa981-173">0x40</span><span class="sxs-lookup"><span data-stu-id="aa981-173">0x40</span></span> | <span data-ttu-id="aa981-174">Retourne uniquement les noms des propriétés non-système.</span><span class="sxs-lookup"><span data-stu-id="aa981-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="aa981-175">La fonction alloue toujours un nouveau `SAFEARRAY` si elle retourne `WBEM_S_NO_ERROR` , et `pstrNames` est toujours définie pour pointer sur elle.</span><span class="sxs-lookup"><span data-stu-id="aa981-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="aa981-176">Le tableau retourné peut avoir 0 élément si aucune propriété ne correspond aux filtres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="aa981-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="aa981-177">Si la fonction retourne une valeur autre que `WBM_S_NO_ERROR` , une nouvelle `SAFEARRAY` structure n’est pas retournée.</span><span class="sxs-lookup"><span data-stu-id="aa981-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="aa981-178">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="aa981-178">Requirements</span></span>  

 <span data-ttu-id="aa981-179">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa981-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa981-180">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="aa981-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="aa981-181">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="aa981-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa981-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa981-182">See also</span></span>

- [<span data-ttu-id="aa981-183">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="aa981-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
