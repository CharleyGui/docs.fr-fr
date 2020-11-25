---
title: Fonction QualifierSet_Next (référence des API non managées)
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
ms.openlocfilehash: 54d79a3dc081e9cdcb42153b6f7aa457557e3399
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721125"
---
# <a name="qualifierset_next-function"></a><span data-ttu-id="7a3fd-103">QualifierSet_Next, fonction</span><span class="sxs-lookup"><span data-stu-id="7a3fd-103">QualifierSet_Next function</span></span>

<span data-ttu-id="7a3fd-104">Récupère le qualificateur suivant dans une énumération commencée avec un appel à la fonction [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="7a3fd-104">Retrieves the next qualifier in an enumeration that started with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7a3fd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7a3fd-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="7a3fd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7a3fd-106">Parameters</span></span>

<span data-ttu-id="7a3fd-107">`vFunc` dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="7a3fd-108">`ptr` dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="7a3fd-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="7a3fd-109">`lFlags` dans Réservé.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-109">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="7a3fd-110">Ce paramètre doit avoir la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-110">This parameter must be 0.</span></span>

<span data-ttu-id="7a3fd-111">`pstrName` à Nom du qualificateur.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-111">`pstrName` [out] The name of the qualifier.</span></span> <span data-ttu-id="7a3fd-112">Si `null` la valeur est, ce paramètre est ignoré ; sinon, `pstrName` ne doit pas pointer vers un valide `BSTR` ou une fuite de mémoire se produit.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-112">If `null`, this parameter is ignored; otherwise, `pstrName` should not point to a valid `BSTR` or a memory leak occurs.</span></span> <span data-ttu-id="7a3fd-113">Si la valeur n’est pas null, la fonction alloue toujours une nouvelle `BSTR` quand elle retourne `WBEM_S_NO_ERROR` .</span><span class="sxs-lookup"><span data-stu-id="7a3fd-113">If not null, the function always allocates a new `BSTR` when it returns `WBEM_S_NO_ERROR`.</span></span>

<span data-ttu-id="7a3fd-114">`pVal` à En cas de réussite, il s’agit de la valeur du qualificateur.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-114">`pVal` [out] When successful, the value for the qualifier.</span></span> <span data-ttu-id="7a3fd-115">Si la fonction échoue, le `VARIANT` pointé par `pVal` n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-115">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="7a3fd-116">Si ce paramètre est `null` , le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-116">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="7a3fd-117">`plFlavor` à Pointeur vers une valeur de type LONG qui reçoit la version du qualificateur.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-117">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor.</span></span> <span data-ttu-id="7a3fd-118">Si les informations de version ne sont pas souhaitées, ce paramètre peut avoir la la `null` .</span><span class="sxs-lookup"><span data-stu-id="7a3fd-118">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="7a3fd-119">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7a3fd-119">Return value</span></span>

<span data-ttu-id="7a3fd-120">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="7a3fd-120">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7a3fd-121">Constante</span><span class="sxs-lookup"><span data-stu-id="7a3fd-121">Constant</span></span>  |<span data-ttu-id="7a3fd-122">Value</span><span class="sxs-lookup"><span data-stu-id="7a3fd-122">Value</span></span>  |<span data-ttu-id="7a3fd-123">Description</span><span class="sxs-lookup"><span data-stu-id="7a3fd-123">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7a3fd-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7a3fd-124">0x80041008</span></span> | <span data-ttu-id="7a3fd-125">Un paramètre n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-125">A parameter is not valid.</span></span> |
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="7a3fd-126">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="7a3fd-126">0x8004101d</span></span> | <span data-ttu-id="7a3fd-127">L’appelant n’a pas appelé [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="7a3fd-127">The caller did not call [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md).</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="7a3fd-128">0x80041006</span><span class="sxs-lookup"><span data-stu-id="7a3fd-128">0x80041006</span></span> | <span data-ttu-id="7a3fd-129">Mémoire disponible insuffisante pour commencer une nouvelle énumération.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-129">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="7a3fd-130">0x40005</span><span class="sxs-lookup"><span data-stu-id="7a3fd-130">0x40005</span></span> | <span data-ttu-id="7a3fd-131">Aucun qualificateur supplémentaire n’est laissé dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-131">No more qualifiers are left in the enumeration.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7a3fd-132">0</span><span class="sxs-lookup"><span data-stu-id="7a3fd-132">0</span></span> | <span data-ttu-id="7a3fd-133">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-133">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="7a3fd-134">Remarques</span><span class="sxs-lookup"><span data-stu-id="7a3fd-134">Remarks</span></span>

<span data-ttu-id="7a3fd-135">Cette fonction encapsule un appel à la méthode [IWbemQualifierSet :: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) .</span><span class="sxs-lookup"><span data-stu-id="7a3fd-135">This function wraps a call to the [IWbemQualifierSet::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-next) method.</span></span>

<span data-ttu-id="7a3fd-136">Vous appelez la `QualifierSet_Next` fonction à plusieurs reprises pour énumérer tous les qualificateurs jusqu’à ce que la fonction retourne `WBEM_S_NO_MORE_DATA` .</span><span class="sxs-lookup"><span data-stu-id="7a3fd-136">You call the `QualifierSet_Next` function repeatedly to enumerate all the qualifiers until the function return `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="7a3fd-137">Pour terminer l’énumération tôt, appelez la fonction [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="7a3fd-137">To terminate the enumeration early, call the [QualifierSet_EndEnumeration](qualifierset-endenumeration.md) function.</span></span>

<span data-ttu-id="7a3fd-138">L’ordre des qualificateurs retournés pendant l’énumération n’est pas défini.</span><span class="sxs-lookup"><span data-stu-id="7a3fd-138">The order of the qualifiers returned during the enumeration is undefined.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a3fd-139">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7a3fd-139">Requirements</span></span>  

 <span data-ttu-id="7a3fd-140">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a3fd-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a3fd-141">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="7a3fd-141">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7a3fd-142">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7a3fd-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a3fd-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a3fd-143">See also</span></span>

- [<span data-ttu-id="7a3fd-144">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="7a3fd-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
