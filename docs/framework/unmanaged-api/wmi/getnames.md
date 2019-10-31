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
ms.openlocfilehash: 5b03ed6a68fbe288e93dedb4f425f1511563dfeb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102522"
---
# <a name="getnames-function"></a><span data-ttu-id="c5f5b-103">GetNames, fonction</span><span class="sxs-lookup"><span data-stu-id="c5f5b-103">GetNames function</span></span>
<span data-ttu-id="c5f5b-104">Récupère une partie ou l’ensemble des noms des propriétés d’un objet.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-104">Retrieves either a subset or all of the names of the properties of an object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="c5f5b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5f5b-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="c5f5b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5f5b-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c5f5b-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="c5f5b-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="c5f5b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszQualifierName`  
<span data-ttu-id="c5f5b-109">dans Pointeur vers un `LPCWSTR` valide qui spécifie un nom de qualificateur qui opère dans le cadre d’un filtre.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-109">[in] A pointer to a valid `LPCWSTR` that specifies a qualifier name that operates as part of a filter.</span></span> <span data-ttu-id="c5f5b-110">Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="c5f5b-110">For more information, see the [Remarks](#remarks) section.</span></span> <span data-ttu-id="c5f5b-111">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-111">This parameter can be `null`.</span></span> 

`lFlags`  
<span data-ttu-id="c5f5b-112">dans Combinaison de champs de bits.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-112">[in] A combination of bit fields.</span></span> <span data-ttu-id="c5f5b-113">Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="c5f5b-113">For more information, see the [Remarks](#remarks) section.</span></span>

`pQualifierValue`   
<span data-ttu-id="c5f5b-114">dans Pointeur vers une structure de `VARIANT` valide initialisée à une valeur de filtre.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-114">[in] A pointer to a valid `VARIANT` structure initialized to a filter value.</span></span> <span data-ttu-id="c5f5b-115">Ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-115">This parameter can be `null`.</span></span> 

`pstrNames`  
<span data-ttu-id="c5f5b-116">à Structure `SAFEARRAY` qui contient des noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-116">[out] A `SAFEARRAY` structure that contains property names.</span></span> <span data-ttu-id="c5f5b-117">Dans l’entrée, ce paramètre doit toujours être un pointeur vers `null`.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-117">On entry, this parameter must always be a pointer to `null`.</span></span> <span data-ttu-id="c5f5b-118">Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="c5f5b-118">See the [Remarks](#remarks) section for more information.</span></span> 

## <a name="return-value"></a><span data-ttu-id="c5f5b-119">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c5f5b-119">Return value</span></span>

<span data-ttu-id="c5f5b-120">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="c5f5b-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c5f5b-121">Constante</span><span class="sxs-lookup"><span data-stu-id="c5f5b-121">Constant</span></span>  |<span data-ttu-id="c5f5b-122">valeur</span><span class="sxs-lookup"><span data-stu-id="c5f5b-122">Value</span></span>  |<span data-ttu-id="c5f5b-123">Description</span><span class="sxs-lookup"><span data-stu-id="c5f5b-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="c5f5b-124">0x80041001</span><span class="sxs-lookup"><span data-stu-id="c5f5b-124">0x80041001</span></span> | <span data-ttu-id="c5f5b-125">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-125">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c5f5b-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c5f5b-126">0x80041008</span></span> | <span data-ttu-id="c5f5b-127">Un ou plusieurs paramètres ne sont pas valides ou une combinaison incorrecte d’indicateurs et de paramètres a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-127">One or more parameters are not valid, or an incorrect combination of flags and parameters was specified.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c5f5b-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c5f5b-128">0x80041006</span></span> | <span data-ttu-id="c5f5b-129">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-129">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c5f5b-130">0</span><span class="sxs-lookup"><span data-stu-id="c5f5b-130">0</span></span> | <span data-ttu-id="c5f5b-131">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-131">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c5f5b-132">Notes</span><span class="sxs-lookup"><span data-stu-id="c5f5b-132">Remarks</span></span>

<span data-ttu-id="c5f5b-133">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) .</span><span class="sxs-lookup"><span data-stu-id="c5f5b-133">This function wraps a call to the [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames) method.</span></span>

<span data-ttu-id="c5f5b-134">Le nommé retourné est contrôlé par une combinaison d’indicateurs et de paramètres.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-134">The named returned are controlled by a combination of flags and parameters.</span></span> <span data-ttu-id="c5f5b-135">Par exemple, la fonction peut retourner les noms de toutes les propriétés ou uniquement les noms des propriétés de clé.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-135">For example, the function can return the names of all properties or only the names of the key properties.</span></span>  <span data-ttu-id="c5f5b-136">Le filtre principal est spécifié dans le paramètre `lFlags`, et les autres paramètres varient en fonction de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-136">The primary filter is specified in the `lFlags` parameter, and the other parameters vary depending on it.</span></span>

<span data-ttu-id="c5f5b-137">Les valeurs d’indicateur dans `lFlags` sont des champs de bits</span><span class="sxs-lookup"><span data-stu-id="c5f5b-137">The flag values in `lFlags` are bit fields</span></span>

<span data-ttu-id="c5f5b-138">Les indicateurs qui peuvent être passés en tant qu’argument `lEnumFlags` sont des champs de bits qui sont définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-138">The flags that can be passed as the `lEnumFlags` argument are bit fields that are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>  <span data-ttu-id="c5f5b-139">Vous pouvez associer un indicateur de chaque groupe à n’importe quel indicateur de n’importe quel autre groupe.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-139">You can combine one flag from each group with any flag from any other group.</span></span> <span data-ttu-id="c5f5b-140">Toutefois, les indicateurs du même groupe s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-140">However, flags from the same group are mutually exclusive.</span></span> 

| <span data-ttu-id="c5f5b-141">Indicateurs du groupe 1</span><span class="sxs-lookup"><span data-stu-id="c5f5b-141">Group 1 flags</span></span> |<span data-ttu-id="c5f5b-142">valeur</span><span class="sxs-lookup"><span data-stu-id="c5f5b-142">Value</span></span>  |<span data-ttu-id="c5f5b-143">Description</span><span class="sxs-lookup"><span data-stu-id="c5f5b-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | <span data-ttu-id="c5f5b-144">0</span><span class="sxs-lookup"><span data-stu-id="c5f5b-144">0</span></span> | <span data-ttu-id="c5f5b-145">Retourne tous les noms de propriété.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-145">Return all property names.</span></span> <span data-ttu-id="c5f5b-146">les `strQualifierName` et les `pQualifierVal` ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-146">`strQualifierName` and `pQualifierVal` are unused.</span></span> |
| `WBEM_FLAG_ONLY_IF_TRUE` | <span data-ttu-id="c5f5b-147">1</span><span class="sxs-lookup"><span data-stu-id="c5f5b-147">1</span></span> | <span data-ttu-id="c5f5b-148">Retourne uniquement les propriétés qui ont un qualificateur du nom spécifié par le paramètre `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-148">Return only properties that have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="c5f5b-149">Si cet indicateur est utilisé, vous devez spécifier `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-149">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_FALSE` | <span data-ttu-id="c5f5b-150">2</span><span class="sxs-lookup"><span data-stu-id="c5f5b-150">2</span></span> |  <span data-ttu-id="c5f5b-151">Retourne uniquement les propriétés qui n’ont pas de qualificateur du nom spécifié par le paramètre `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-151">Return only properties that do not have a qualifier of the name specified by the `strQualifierName` parameter.</span></span> <span data-ttu-id="c5f5b-152">Si cet indicateur est utilisé, vous devez spécifier `strQualifierName`.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-152">If this flag is used, you must specify `strQualifierName`.</span></span> |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | <span data-ttu-id="c5f5b-153">3</span><span class="sxs-lookup"><span data-stu-id="c5f5b-153">3</span></span> | <span data-ttu-id="c5f5b-154">Retourne uniquement les propriétés qui ont un qualificateur du nom spécifié par le paramètre `wszQualifierName` et ont également une valeur identique à celle spécifiée par la structure `pQualifierVal`.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-154">Return only properties that have a qualifier of the name specified by the `wszQualifierName` parameter and also have a value identical to that specified by the `pQualifierVal` structure.</span></span> <span data-ttu-id="c5f5b-155">Si cet indicateur est utilisé, vous devez spécifier à la fois un `wszQualifierName` et un `pQualifierValue`.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-155">If this flag is used, you must specify both a `wszQualifierName` and a `pQualifierValue`.</span></span> |

| <span data-ttu-id="c5f5b-156">Indicateurs du groupe 2</span><span class="sxs-lookup"><span data-stu-id="c5f5b-156">Group 2 flags</span></span> |<span data-ttu-id="c5f5b-157">valeur</span><span class="sxs-lookup"><span data-stu-id="c5f5b-157">Value</span></span>  |<span data-ttu-id="c5f5b-158">Description</span><span class="sxs-lookup"><span data-stu-id="c5f5b-158">Description</span></span>  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | <span data-ttu-id="c5f5b-159">0x4</span><span class="sxs-lookup"><span data-stu-id="c5f5b-159">0x4</span></span> | <span data-ttu-id="c5f5b-160">Retourne uniquement les noms des propriétés qui définissent les clés.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-160">Return only the names of properties that define the keys.</span></span> |
|`WBEM_FLAG_REFS_ONLY` | <span data-ttu-id="c5f5b-161">0x8</span><span class="sxs-lookup"><span data-stu-id="c5f5b-161">0x8</span></span> | <span data-ttu-id="c5f5b-162">Retourne uniquement les noms de propriété qui sont des références d’objet.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-162">Return only property names that are object references.</span></span> |

| <span data-ttu-id="c5f5b-163">Indicateurs du groupe 3</span><span class="sxs-lookup"><span data-stu-id="c5f5b-163">Group 3 flags</span></span> |<span data-ttu-id="c5f5b-164">valeur</span><span class="sxs-lookup"><span data-stu-id="c5f5b-164">Value</span></span>  |<span data-ttu-id="c5f5b-165">Description</span><span class="sxs-lookup"><span data-stu-id="c5f5b-165">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="c5f5b-166">0x10</span><span class="sxs-lookup"><span data-stu-id="c5f5b-166">0x10</span></span> | <span data-ttu-id="c5f5b-167">Retourne uniquement les noms de propriété qui appartiennent à la classe la plus dérivée.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-167">Return only property names that belong to the most derived class.</span></span> <span data-ttu-id="c5f5b-168">Excluez les propriétés des classes parentes.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-168">Exclude properties from the parent classes.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="c5f5b-169">0x20</span><span class="sxs-lookup"><span data-stu-id="c5f5b-169">0x20</span></span> | <span data-ttu-id="c5f5b-170">Retourne uniquement les noms de propriété qui appartiennent aux classes parentes.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-170">Return only property names that belong to the parent classes.</span></span> |
|`WBEM_FLAG_SYSTEM_ONLY` | <span data-ttu-id="c5f5b-171">0x30</span><span class="sxs-lookup"><span data-stu-id="c5f5b-171">0x30</span></span> | <span data-ttu-id="c5f5b-172">Retourne uniquement les noms des propriétés système.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-172">Return only the names of system properties.</span></span> |
|`WBEM_FLAG_NONSYSTEM_ONLY` | <span data-ttu-id="c5f5b-173">0x40</span><span class="sxs-lookup"><span data-stu-id="c5f5b-173">0x40</span></span> | <span data-ttu-id="c5f5b-174">Retourne uniquement les noms des propriétés non-système.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-174">Return only the names of non-system properties.</span></span> |

<span data-ttu-id="c5f5b-175">La fonction alloue toujours une nouvelle `SAFEARRAY` si elle retourne `WBEM_S_NO_ERROR`, et `pstrNames` est toujours définie pour pointer sur elle.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-175">The function always allocates a new `SAFEARRAY` if it returns `WBEM_S_NO_ERROR`, and `pstrNames` is always set to point to it.</span></span> <span data-ttu-id="c5f5b-176">Le tableau retourné peut avoir 0 élément si aucune propriété ne correspond aux filtres spécifiés.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-176">The returned array can have 0 elements if no properties match the specified filters.</span></span> <span data-ttu-id="c5f5b-177">Si la fonction retourne une valeur autre que `WBM_S_NO_ERROR`, une nouvelle structure de `SAFEARRAY` n’est pas retournée.</span><span class="sxs-lookup"><span data-stu-id="c5f5b-177">If the function returns an value other than `WBM_S_NO_ERROR`, a new `SAFEARRAY` structure is not returned.</span></span>
 
## <a name="requirements"></a><span data-ttu-id="c5f5b-178">spécifications</span><span class="sxs-lookup"><span data-stu-id="c5f5b-178">Requirements</span></span>  
 <span data-ttu-id="c5f5b-179">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5f5b-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5f5b-180">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="c5f5b-180">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c5f5b-181">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c5f5b-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5f5b-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5f5b-182">See also</span></span>

- [<span data-ttu-id="c5f5b-183">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="c5f5b-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
