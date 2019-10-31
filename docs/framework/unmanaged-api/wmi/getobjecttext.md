---
title: Fonction GetObjectText (référence des API non managées)
description: La fonction GetObjectText retourne un rendu textuel d’un objet dans la syntaxe MOF.
ms.date: 11/06/2017
api_name:
- GetObjectText
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetObjectText
helpviewer_keywords:
- GetObjectText function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 412e1ad503fa0e0b4f813298c0ac96ae80098c06
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102452"
---
# <a name="getobjecttext-function"></a><span data-ttu-id="2f768-103">GetObjectText, fonction</span><span class="sxs-lookup"><span data-stu-id="2f768-103">GetObjectText function</span></span>
<span data-ttu-id="2f768-104">Retourne un rendu textuel de l’objet dans la syntaxe du format MOF (MOF).</span><span class="sxs-lookup"><span data-stu-id="2f768-104">Returns a textual rendering of the object in the Managed Object Format (MOF) syntax.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="2f768-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f768-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectText (
   [in] int                vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pstrObjectText
); 
```  

## <a name="parameters"></a><span data-ttu-id="2f768-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2f768-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2f768-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="2f768-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2f768-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="2f768-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="2f768-109">dans Normalement 0.</span><span class="sxs-lookup"><span data-stu-id="2f768-109">[in] Normally 0.</span></span> <span data-ttu-id="2f768-110">Si `WBEM_FLAG_NO_FLAVORS` (ou 0x1) est spécifié, les qualificateurs sont inclus sans propagation ni informations de version.</span><span class="sxs-lookup"><span data-stu-id="2f768-110">If `WBEM_FLAG_NO_FLAVORS` (or 0x1) is specified, qualifiers are included without propagation or flavor information.</span></span>

`pstrObjectText`   
<span data-ttu-id="2f768-111">à Pointeur vers une `null` à l’entrée.</span><span class="sxs-lookup"><span data-stu-id="2f768-111">[out] A pointer to a `null` on entry.</span></span> <span data-ttu-id="2f768-112">Au retour, `BSTR` qui vient d’être allouée, contient un rendu de syntaxe MOF de l’objet.</span><span class="sxs-lookup"><span data-stu-id="2f768-112">On return, a newly allocated `BSTR` that contains a MOF syntax rendering of the object.</span></span>  

## <a name="return-value"></a><span data-ttu-id="2f768-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2f768-113">Return value</span></span>

<span data-ttu-id="2f768-114">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="2f768-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2f768-115">Constante</span><span class="sxs-lookup"><span data-stu-id="2f768-115">Constant</span></span>  |<span data-ttu-id="2f768-116">valeur</span><span class="sxs-lookup"><span data-stu-id="2f768-116">Value</span></span>  |<span data-ttu-id="2f768-117">Description</span><span class="sxs-lookup"><span data-stu-id="2f768-117">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="2f768-118">0x80041001</span><span class="sxs-lookup"><span data-stu-id="2f768-118">0x80041001</span></span> | <span data-ttu-id="2f768-119">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="2f768-119">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2f768-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2f768-120">0x80041008</span></span> | <span data-ttu-id="2f768-121">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="2f768-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2f768-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2f768-122">0x80041006</span></span> | <span data-ttu-id="2f768-123">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="2f768-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2f768-124">0</span><span class="sxs-lookup"><span data-stu-id="2f768-124">0</span></span> | <span data-ttu-id="2f768-125">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="2f768-125">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2f768-126">Notes</span><span class="sxs-lookup"><span data-stu-id="2f768-126">Remarks</span></span>

<span data-ttu-id="2f768-127">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) .</span><span class="sxs-lookup"><span data-stu-id="2f768-127">This function wraps a call to the [IWbemClassObject::GetObjectText](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getobjecttext) method.</span></span>

<span data-ttu-id="2f768-128">Le texte MOF retourné ne contient pas toutes les informations relatives à l’objet, mais uniquement les informations nécessaires au compilateur MOF pour pouvoir recréer l’objet d’origine.</span><span class="sxs-lookup"><span data-stu-id="2f768-128">The MOF text returned does not contain all the information about the object, but only enough information for the MOF compiler to be able to recreate the original object.</span></span> <span data-ttu-id="2f768-129">Par exemple, aucun qualificateur propagé ou propriété de classe parente n’est inclus.</span><span class="sxs-lookup"><span data-stu-id="2f768-129">For instance, no propagated qualifiers or parent class properties are included.</span></span>

<span data-ttu-id="2f768-130">L’algorithme suivant est utilisé pour reconstruire le texte des paramètres d’une méthode :</span><span class="sxs-lookup"><span data-stu-id="2f768-130">The following algorithm is used to reconstruct the text of the parameters of a method:</span></span>

1. <span data-ttu-id="2f768-131">Les paramètres sont reséquencés dans l’ordre de leurs valeurs d’identificateur.</span><span class="sxs-lookup"><span data-stu-id="2f768-131">Parameters are resequenced in the order of their identifier values.</span></span>
1. <span data-ttu-id="2f768-132">Les paramètres spécifiés en tant que `[in]` et `[out]` sont combinés en un seul paramètre.</span><span class="sxs-lookup"><span data-stu-id="2f768-132">Parameters that are specified as `[in]` and `[out]` are combined into a single parameter.</span></span>
 
<span data-ttu-id="2f768-133">`pstrObjectText` doit être un pointeur vers un `null` lorsque la fonction est appelée ; elle ne doit pas pointer vers une chaîne valide avant l’appel de la méthode, car le pointeur n’est pas libéré.</span><span class="sxs-lookup"><span data-stu-id="2f768-133">`pstrObjectText` must be a pointer to a `null` when the function is called; it must not point to a string that is valid before the method call, because the pointer will not be deallocated.</span></span>

## <a name="requirements"></a><span data-ttu-id="2f768-134">spécifications</span><span class="sxs-lookup"><span data-stu-id="2f768-134">Requirements</span></span>  
<span data-ttu-id="2f768-135">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f768-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f768-136">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="2f768-136">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2f768-137">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2f768-137">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f768-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f768-138">See also</span></span>

- [<span data-ttu-id="2f768-139">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="2f768-139">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
