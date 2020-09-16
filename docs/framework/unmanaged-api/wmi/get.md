---
title: Fonction d’extraction (référence des API non managées)
description: La fonction obtenir récupère la valeur de propriété spécifiée.
ms.date: 11/06/2017
api_name:
- Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Get
helpviewer_keywords:
- Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 7cc0c285f79b2791863fce251e4683aa7b55341b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553686"
---
# <a name="get-function"></a><span data-ttu-id="3448b-103">Get, fonction</span><span class="sxs-lookup"><span data-stu-id="3448b-103">Get function</span></span>

<span data-ttu-id="3448b-104">Récupère la valeur de propriété spécifiée, si elle existe.</span><span class="sxs-lookup"><span data-stu-id="3448b-104">Retrieves the specified property value if it exists.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="3448b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3448b-105">Syntax</span></span>

```cpp
HRESULT Get (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="3448b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3448b-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="3448b-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="3448b-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="3448b-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="3448b-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="3448b-109">[in] Nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="3448b-109">[in] The name of the property.</span></span>

`lFlags`\
<span data-ttu-id="3448b-110">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="3448b-110">[in] Reserved.</span></span> <span data-ttu-id="3448b-111">Ce paramètre doit avoir la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="3448b-111">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="3448b-112">à Si la fonction est correctement retournée, contient la valeur de la `wszName` propriété.</span><span class="sxs-lookup"><span data-stu-id="3448b-112">[out] If the function returns successfully, contains the value of the `wszName` property.</span></span> <span data-ttu-id="3448b-113">Le `pval` type et la valeur corrects pour le qualificateur sont assignés à l’argument.</span><span class="sxs-lookup"><span data-stu-id="3448b-113">The `pval` argument is assigned the correct type and value for the qualifier.</span></span>

`pvtType`\
<span data-ttu-id="3448b-114">à Si la fonction est correctement retournée, contient une [constante de type CIM](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) qui indique le type de propriété.</span><span class="sxs-lookup"><span data-stu-id="3448b-114">[out] If the function returns successfully, contains a [CIM-type constant](/windows/win32/api/wbemcli/ne-wbemcli-cimtype_enumeration) that indicates the property type.</span></span> <span data-ttu-id="3448b-115">Sa valeur peut également être `null` .</span><span class="sxs-lookup"><span data-stu-id="3448b-115">Its value can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="3448b-116">à Si la fonction est correctement retournée, reçoit des informations sur l’origine de la propriété.</span><span class="sxs-lookup"><span data-stu-id="3448b-116">[out] If the function returns successfully, receives information about the origin of the property.</span></span> <span data-ttu-id="3448b-117">Sa valeur peut être `null` , ou l’une des constantes de WBEM_FLAVOR_TYPE suivantes définies dans le fichier d’en-tête *WbemCli. h* :</span><span class="sxs-lookup"><span data-stu-id="3448b-117">Its value can be `null`, or one of the following WBEM_FLAVOR_TYPE constants defined in the *WbemCli.h* header file:</span></span>

|<span data-ttu-id="3448b-118">Constante</span><span class="sxs-lookup"><span data-stu-id="3448b-118">Constant</span></span>  |<span data-ttu-id="3448b-119">Valeur</span><span class="sxs-lookup"><span data-stu-id="3448b-119">Value</span></span>  |<span data-ttu-id="3448b-120">Description</span><span class="sxs-lookup"><span data-stu-id="3448b-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="3448b-121">0x40</span><span class="sxs-lookup"><span data-stu-id="3448b-121">0x40</span></span> | <span data-ttu-id="3448b-122">La propriété est une propriété système standard.</span><span class="sxs-lookup"><span data-stu-id="3448b-122">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="3448b-123">0x20</span><span class="sxs-lookup"><span data-stu-id="3448b-123">0x20</span></span> | <span data-ttu-id="3448b-124">Pour une classe : la propriété est héritée de la classe parente.</span><span class="sxs-lookup"><span data-stu-id="3448b-124">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="3448b-125">Pour une instance : la propriété, alors qu’elle est héritée de la classe parente, n’a pas été modifiée par l’instance.</span><span class="sxs-lookup"><span data-stu-id="3448b-125">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="3448b-126">0</span><span class="sxs-lookup"><span data-stu-id="3448b-126">0</span></span> | <span data-ttu-id="3448b-127">Pour une classe : la propriété appartient à la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="3448b-127">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="3448b-128">Pour une instance : la propriété est modifiée par l’instance ; autrement dit, une valeur a été fournie ou un qualificateur a été ajouté ou modifié.</span><span class="sxs-lookup"><span data-stu-id="3448b-128">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="return-value"></a><span data-ttu-id="3448b-129">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="3448b-129">Return value</span></span>

<span data-ttu-id="3448b-130">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="3448b-130">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3448b-131">Constante</span><span class="sxs-lookup"><span data-stu-id="3448b-131">Constant</span></span>  |<span data-ttu-id="3448b-132">Valeur</span><span class="sxs-lookup"><span data-stu-id="3448b-132">Value</span></span>  |<span data-ttu-id="3448b-133">Description</span><span class="sxs-lookup"><span data-stu-id="3448b-133">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="3448b-134">0x80041001</span><span class="sxs-lookup"><span data-stu-id="3448b-134">0x80041001</span></span> | <span data-ttu-id="3448b-135">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3448b-135">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3448b-136">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3448b-136">0x80041008</span></span> | <span data-ttu-id="3448b-137">Un ou plusieurs paramètres ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="3448b-137">One or more parameters are not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="3448b-138">0x80041002</span><span class="sxs-lookup"><span data-stu-id="3448b-138">0x80041002</span></span> | <span data-ttu-id="3448b-139">La propriété spécifiée est introuvable.</span><span class="sxs-lookup"><span data-stu-id="3448b-139">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3448b-140">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3448b-140">0x80041006</span></span> | <span data-ttu-id="3448b-141">La mémoire n'est pas suffisante pour terminer cette opération.</span><span class="sxs-lookup"><span data-stu-id="3448b-141">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3448b-142">0</span><span class="sxs-lookup"><span data-stu-id="3448b-142">0</span></span> | <span data-ttu-id="3448b-143">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="3448b-143">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="3448b-144">Notes</span><span class="sxs-lookup"><span data-stu-id="3448b-144">Remarks</span></span>

<span data-ttu-id="3448b-145">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: obtenir](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) .</span><span class="sxs-lookup"><span data-stu-id="3448b-145">This function wraps a call to the [IWbemClassObject::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-get) method.</span></span>

<span data-ttu-id="3448b-146">La `Get` fonction peut également retourner des propriétés système.</span><span class="sxs-lookup"><span data-stu-id="3448b-146">The `Get` function can also return system properties.</span></span>

<span data-ttu-id="3448b-147">Le `pVal` type et la valeur corrects pour le qualificateur et la fonction com [VariantInit](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) sont assignés à l’argument</span><span class="sxs-lookup"><span data-stu-id="3448b-147">The `pVal` argument is assigned the correct type and value for the qualifier and the COM [VariantInit](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-variantinit) function</span></span>

## <a name="requirements"></a><span data-ttu-id="3448b-148">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3448b-148">Requirements</span></span>

 <span data-ttu-id="3448b-149">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3448b-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="3448b-150">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="3448b-150">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="3448b-151">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3448b-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3448b-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3448b-152">See also</span></span>

- [<span data-ttu-id="3448b-153">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="3448b-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
