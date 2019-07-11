---
title: QualifierSet_Next (fonction) (référence des API non managées)
description: La fonction QualifierSet_Next récupère le qualificateur suivant dans une énumération.
ms.date: 11/06/2017
api_name:
- QualifierSet_Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Next
helpviewer_keywords:
- QualifierSet_Next function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ac5cc8633881749bdc167e1b3925a83f7adf3b3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760304"
---
# <a name="qualifiersetnext-function"></a><span data-ttu-id="ccf16-103">QualifierSet_Next (fonction)</span><span class="sxs-lookup"><span data-stu-id="ccf16-103">QualifierSet_Next function</span></span>
<span data-ttu-id="ccf16-104">Récupère le qualificateur suivant dans une énumération commencée avec un appel à la fonction [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="ccf16-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>   

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ccf16-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccf16-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Next (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LONG                 lFlags,
   [out] BSTR*               pstrName,        
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="ccf16-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ccf16-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="ccf16-107">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="ccf16-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="ccf16-108">[in] Un pointeur vers un [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="ccf16-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`lFlags`   
<span data-ttu-id="ccf16-109">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="ccf16-109">[in] Reserved.</span></span> <span data-ttu-id="ccf16-110">Ce paramètre doit être 0.</span><span class="sxs-lookup"><span data-stu-id="ccf16-110">This parameter must be 0.</span></span>

`pstrName`   
<span data-ttu-id="ccf16-111">[out] Le nom du qualificateur.</span><span class="sxs-lookup"><span data-stu-id="ccf16-111">[out] The name of the qualifier.</span></span> <span data-ttu-id="ccf16-112">Si `null`, ce paramètre est ignoré ; sinon, `pstrName` ne doit pas pointer vers un valide `BSTR` ou une fuite de mémoire se produit.</span><span class="sxs-lookup"><span data-stu-id="ccf16-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="ccf16-113">Si non null, la fonction alloue toujours un nouveau `BSTR` quand il renvoie `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="ccf16-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

`pVal`   
<span data-ttu-id="ccf16-114">[out] Cas de réussite, la valeur du qualificateur.</span><span class="sxs-lookup"><span data-stu-id="ccf16-114">[out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="ccf16-115">Si la fonction échoue, le `VARIANT` vers lequel pointe `pVal` n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="ccf16-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="ccf16-116">Si ce paramètre est `null`, le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="ccf16-116">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="ccf16-117">[out] Pointeur vers un entier LONG qui reçoit le type de qualificateur.</span><span class="sxs-lookup"><span data-stu-id="ccf16-117">[out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="ccf16-118">Si les informations de version ne sont pas souhaitées, ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="ccf16-118">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="ccf16-119">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ccf16-119">Return value</span></span>

<span data-ttu-id="ccf16-120">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="ccf16-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ccf16-121">Constante</span><span class="sxs-lookup"><span data-stu-id="ccf16-121">Constant</span></span>  |<span data-ttu-id="ccf16-122">`Value`</span><span class="sxs-lookup"><span data-stu-id="ccf16-122">Value</span></span>  |<span data-ttu-id="ccf16-123">Description</span><span class="sxs-lookup"><span data-stu-id="ccf16-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ccf16-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ccf16-124">0x80041008</span></span> | <span data-ttu-id="ccf16-125">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="ccf16-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="ccf16-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="ccf16-126">0x8004101d</span></span> | <span data-ttu-id="ccf16-127">L’appelant n’a pas appelé [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="ccf16-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ccf16-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ccf16-128">0x80041006</span></span> | <span data-ttu-id="ccf16-129">Pas assez de mémoire est disponible pour commencer une nouvelle énumération.</span><span class="sxs-lookup"><span data-stu-id="ccf16-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="ccf16-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="ccf16-130">0x40005</span></span> | <span data-ttu-id="ccf16-131">Aucuns plus de qualificateurs ne sont laissées dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="ccf16-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ccf16-132">0</span><span class="sxs-lookup"><span data-stu-id="ccf16-132">0</span></span> | <span data-ttu-id="ccf16-133">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="ccf16-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ccf16-134">Notes</span><span class="sxs-lookup"><span data-stu-id="ccf16-134">Remarks</span></span>

<span data-ttu-id="ccf16-135">Cette fonction encapsule un appel à la [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) (méthode).</span><span class="sxs-lookup"><span data-stu-id="ccf16-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="ccf16-136">Vous appelez le `QualifierSet_Next` fonction à plusieurs reprises pour énumérer tous les qualificateurs jusqu'à ce que le retour de fonction `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="ccf16-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="ccf16-137">Pour terminer l’énumération au début, appelez le [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="ccf16-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="ccf16-138">L’ordre des qualificateurs retourné lors de l’énumération n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="ccf16-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="ccf16-139">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ccf16-139">Requirements</span></span>  
 <span data-ttu-id="ccf16-140">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccf16-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccf16-141">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ccf16-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ccf16-142">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ccf16-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccf16-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ccf16-143">See also</span></span>

- [<span data-ttu-id="ccf16-144">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="ccf16-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
