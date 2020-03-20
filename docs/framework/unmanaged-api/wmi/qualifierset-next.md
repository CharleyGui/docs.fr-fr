---
title: fonction QualifierSet_Next (référence API non gestion)
description: La fonction QualifierSet_Next récupère le prochain qualificatif dans un recensement.
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
ms.openlocfilehash: d3702426bc409d601ccfc6b7a8e93e8d9729c64e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174873"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="da33e-103">QualifierSet_Next, fonction</span><span class="sxs-lookup"><span data-stu-id="da33e-103">QualifierSet_Next function</span></span>
<span data-ttu-id="da33e-104">Récupère le qualificateur suivant dans une énumération commencée avec un appel à la fonction [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="da33e-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="da33e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da33e-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="da33e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="da33e-106">Parameters</span></span>

<span data-ttu-id="da33e-107">`vFunc`[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="da33e-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="da33e-108">`ptr`[dans] Un pointeur à une instance [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="da33e-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="da33e-109">`lFlags`[dans] Réservés au.</span><span class="sxs-lookup"><span data-stu-id="da33e-109">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="da33e-110">Ce paramètre doit être de 0.</span><span class="sxs-lookup"><span data-stu-id="da33e-110">This parameter must be 0.</span></span>

<span data-ttu-id="da33e-111">`pstrName`[out] Le nom du qualificatif.</span><span class="sxs-lookup"><span data-stu-id="da33e-111">`pstrName` [out] The name of the qualifier.</span></span> <span data-ttu-id="da33e-112">Si `null`, ce paramètre est ignoré; autrement, `pstrName` ne doit pas `BSTR` indiquer une fuite valide ou une fuite de mémoire se produit.</span><span class="sxs-lookup"><span data-stu-id="da33e-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="da33e-113">Si elle n’est pas nulle, la fonction alloue toujours un nouveau `BSTR` quand il revient `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="da33e-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

<span data-ttu-id="da33e-114">`pVal`[out] En cas de succès, la valeur pour le qualificatif.</span><span class="sxs-lookup"><span data-stu-id="da33e-114">`pVal` [out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="da33e-115">Si la fonction `VARIANT` échoue, `pVal` le pointé vers par n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="da33e-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="da33e-116">Si ce `null`paramètre est , le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="da33e-116">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="da33e-117">`plFlavor`[out] Un pointeur à un LONG qui reçoit la saveur qualificative.</span><span class="sxs-lookup"><span data-stu-id="da33e-117">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="da33e-118">Si l’information de saveur n’est pas désirée, ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="da33e-118">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="da33e-119">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="da33e-119">Return value</span></span>

<span data-ttu-id="da33e-120">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="da33e-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="da33e-121">Constant</span><span class="sxs-lookup"><span data-stu-id="da33e-121">Constant</span></span>  |<span data-ttu-id="da33e-122">Valeur</span><span class="sxs-lookup"><span data-stu-id="da33e-122">Value</span></span>  |<span data-ttu-id="da33e-123">Description</span><span class="sxs-lookup"><span data-stu-id="da33e-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="da33e-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="da33e-124">0x80041008</span></span> | <span data-ttu-id="da33e-125">Un paramètre n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="da33e-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="da33e-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="da33e-126">0x8004101d</span></span> | <span data-ttu-id="da33e-127">L’appelant n’a pas appelé [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="da33e-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="da33e-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="da33e-128">0x80041006</span></span> | <span data-ttu-id="da33e-129">Pas assez de mémoire est disponible pour commencer une nouvelle énumération.</span><span class="sxs-lookup"><span data-stu-id="da33e-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="da33e-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="da33e-130">0x40005</span></span> | <span data-ttu-id="da33e-131">Il ne reste plus de qualificatifs dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="da33e-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="da33e-132">0</span><span class="sxs-lookup"><span data-stu-id="da33e-132">0</span></span> | <span data-ttu-id="da33e-133">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="da33e-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="da33e-134">Notes </span><span class="sxs-lookup"><span data-stu-id="da33e-134">Remarks</span></span>

<span data-ttu-id="da33e-135">Cette fonction enveloppe un appel à [l’IWbemQualifierSet::Méthode suivante.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next)</span><span class="sxs-lookup"><span data-stu-id="da33e-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="da33e-136">Vous appelez `QualifierSet_Next` la fonction à plusieurs reprises pour énumérer tous les qualificatifs jusqu’à ce que la fonction de retour `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="da33e-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="da33e-137">Pour mettre fin à l’énumération tôt, appelez la [fonction QualifierSet_EndEnumeration.](qualifierset-endenumeration.md)</span><span class="sxs-lookup"><span data-stu-id="da33e-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="da33e-138">L’ordre des qualificatifs retournés pendant l’énumération n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="da33e-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="da33e-139">Spécifications</span><span class="sxs-lookup"><span data-stu-id="da33e-139">Requirements</span></span>  
 <span data-ttu-id="da33e-140">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da33e-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da33e-141">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="da33e-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="da33e-142">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="da33e-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da33e-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da33e-143">See also</span></span>

- [<span data-ttu-id="da33e-144">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="da33e-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
