---
title: Put, fonction (référence des API non managées)
description: La fonction put assigne une nouvelle valeur à une propriété nommée.
ms.date: 11/06/2017
api_name:
- Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Put
helpviewer_keywords:
- Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5aa629c2d07fb25db035cd80aba3c74413070e6e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798398"
---
# <a name="put-function"></a><span data-ttu-id="3160f-103">Put, fonction</span><span class="sxs-lookup"><span data-stu-id="3160f-103">Put function</span></span>

<span data-ttu-id="3160f-104">Affecte une nouvelle valeur à une propriété nommée.</span><span class="sxs-lookup"><span data-stu-id="3160f-104">Sets a named property to a new value.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="3160f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3160f-105">Syntax</span></span>

```cpp
HRESULT Put (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName,
   [in] LONG              lFlags,
   [in] VARIANT*          pVal,
   [in] CIMTYPE           vtType
);
```

## <a name="parameters"></a><span data-ttu-id="3160f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3160f-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="3160f-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="3160f-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="3160f-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="3160f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="3160f-109">dans Nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="3160f-109">[in] The name of the property.</span></span> <span data-ttu-id="3160f-110">Ce paramètre ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="3160f-110">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="3160f-111">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="3160f-111">[in] Reserved.</span></span> <span data-ttu-id="3160f-112">Ce paramètre doit avoir la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="3160f-112">This parameter must be 0.</span></span>

`pVal`\
<span data-ttu-id="3160f-113">dans Pointeur vers un valide `VARIANT` qui devient la nouvelle valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="3160f-113">[in] A pointer to a valid `VARIANT` that becomes the new property value.</span></span> <span data-ttu-id="3160f-114">Si `pVal` `VARIANT` `VT_NULL`est oupointe`null`vers un de type, la propriété a la valeur. `null`</span><span class="sxs-lookup"><span data-stu-id="3160f-114">If `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`, the property is set to `null`.</span></span>

`vtType`\
<span data-ttu-id="3160f-115">dans Type de `VARIANT` pointé par `pVal`.</span><span class="sxs-lookup"><span data-stu-id="3160f-115">[in] The type of `VARIANT` pointed to by `pVal`.</span></span> <span data-ttu-id="3160f-116">Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="3160f-116">See the [Remarks](#remarks) section for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="3160f-117">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3160f-117">Return value</span></span>

<span data-ttu-id="3160f-118">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="3160f-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="3160f-119">Constante</span><span class="sxs-lookup"><span data-stu-id="3160f-119">Constant</span></span>  |<span data-ttu-id="3160f-120">`Value`</span><span class="sxs-lookup"><span data-stu-id="3160f-120">Value</span></span>  |<span data-ttu-id="3160f-121">Description</span><span class="sxs-lookup"><span data-stu-id="3160f-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="3160f-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="3160f-122">0x80041001</span></span> | <span data-ttu-id="3160f-123">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="3160f-123">There has been a general failure.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="3160f-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="3160f-124">0x80041008</span></span> | <span data-ttu-id="3160f-125">Un ou plusieurs paramètres ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="3160f-125">One or more parameters are not valid.</span></span> |
|`WBEM_E_INVALID_PROPERTY_TYPE` | <span data-ttu-id="3160f-126">0x8004102a</span><span class="sxs-lookup"><span data-stu-id="3160f-126">0x8004102a</span></span> | <span data-ttu-id="3160f-127">Le type de propriété n’est pas reconnu.</span><span class="sxs-lookup"><span data-stu-id="3160f-127">The property type is not recognized.</span></span> <span data-ttu-id="3160f-128">Cette valeur est retournée lors de la création d’instances de classe si la classe existe déjà.</span><span class="sxs-lookup"><span data-stu-id="3160f-128">This value is returned when creating class instances if the class already exists.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="3160f-129">0x80041006</span><span class="sxs-lookup"><span data-stu-id="3160f-129">0x80041006</span></span> | <span data-ttu-id="3160f-130">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="3160f-130">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_TYPE_MISMATCH` | <span data-ttu-id="3160f-131">0x80041005</span><span class="sxs-lookup"><span data-stu-id="3160f-131">0x80041005</span></span> | <span data-ttu-id="3160f-132">Pour les instances : Indique que `pVal` pointe vers un `VARIANT` de type incorrect pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="3160f-132">For instances: Indicates that `pVal` points to a `VARIANT` of an incorrect type for the property.</span></span> <br/> <span data-ttu-id="3160f-133">Pour les définitions de classe : La propriété existe déjà dans la classe parente et le nouveau type COM est différent de l’ancien type COM.</span><span class="sxs-lookup"><span data-stu-id="3160f-133">For class definitions: The property already exists in the parent class, and the new COM type is different from the old COM type.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="3160f-134">0</span><span class="sxs-lookup"><span data-stu-id="3160f-134">0</span></span> | <span data-ttu-id="3160f-135">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="3160f-135">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="3160f-136">Notes</span><span class="sxs-lookup"><span data-stu-id="3160f-136">Remarks</span></span>

<span data-ttu-id="3160f-137">Cette fonction encapsule un appel à la méthode [IWbemClassObject ::P ut](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .</span><span class="sxs-lookup"><span data-stu-id="3160f-137">This function wraps a call to the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

<span data-ttu-id="3160f-138">Cette fonction remplace toujours la valeur de la propriété actuelle par une nouvelle.</span><span class="sxs-lookup"><span data-stu-id="3160f-138">This function always overwrites the current property value with a new one.</span></span> <span data-ttu-id="3160f-139">Si le [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointe vers une définition de classe `Put` , crée ou met à jour la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="3160f-139">If the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a class definition, `Put` creates or updates the property value.</span></span> <span data-ttu-id="3160f-140">Quand [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointe vers une instance CIM, `Put` met à jour la valeur de la propriété uniquement. `Put` impossible de créer une valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="3160f-140">When [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) points to a CIM instance, `Put` updates the property value only; `Put` cannot create a property value.</span></span>

<span data-ttu-id="3160f-141">La `__CLASS` propriété système est accessible en écriture uniquement lors de la création de la classe, lorsqu’elle ne peut pas être laissée vide.</span><span class="sxs-lookup"><span data-stu-id="3160f-141">The `__CLASS` system property is only writable during class creation, when it may not be left blank.</span></span> <span data-ttu-id="3160f-142">Toutes les autres propriétés système sont en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="3160f-142">All other system properties are read-only.</span></span>

<span data-ttu-id="3160f-143">Un utilisateur ne peut pas créer de propriétés dont le nom commence ou se termine par un trait de soulignement (« _ »).</span><span class="sxs-lookup"><span data-stu-id="3160f-143">A user cannot create properties with names that begin or end with an underscore ("_").</span></span> <span data-ttu-id="3160f-144">Cela est réservé aux classes système et aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="3160f-144">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="3160f-145">Si la propriété définie par la `Put` fonction existe dans la classe parente, la valeur par défaut de la propriété est modifiée, à moins que le type de la propriété ne corresponde pas au type de la classe parente.</span><span class="sxs-lookup"><span data-stu-id="3160f-145">If the property set by the `Put` function exists in the parent class, the default value of the property is changed unless the property type does not match the parent class type.</span></span> <span data-ttu-id="3160f-146">Si la propriété n’existe pas et qu’il ne s’agit pas d’une incompatibilité de type, la propriété est créée.</span><span class="sxs-lookup"><span data-stu-id="3160f-146">If the property does not exist and it is not a type mismatch, the property is created.</span></span>

<span data-ttu-id="3160f-147">Utilisez le `vtType` paramètre uniquement lors de la création de nouvelles propriétés dans une définition `pVal` de `null` classe CIM et est `VARIANT` ou pointe `VT_NULL`vers un de type.</span><span class="sxs-lookup"><span data-stu-id="3160f-147">Use the `vtType` parameter only when creating new properties in a CIM class definition and `pVal` is `null` or points to a `VARIANT` of type `VT_NULL`.</span></span> <span data-ttu-id="3160f-148">Dans ce cas, le `vType` paramètre spécifie le type CIM de la propriété.</span><span class="sxs-lookup"><span data-stu-id="3160f-148">In this case, the `vType` parameter specifies the CIM type of the property.</span></span> <span data-ttu-id="3160f-149">Dans tous les autres cas `vtType` , doit avoir la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="3160f-149">In every other case, `vtType` must be 0.</span></span> <span data-ttu-id="3160f-150">`vtType`doit également avoir la valeur 0 si l’objet sous-jacent est une `Val` instance `null`(même si a la valeur), car le type de la propriété est fixe et ne peut pas être modifié.</span><span class="sxs-lookup"><span data-stu-id="3160f-150">`vtType` must also be 0 if the underlying object is an instance (even if `Val` is `null`) because the type of the property is fixed and cannot be changed.</span></span>

## <a name="example"></a><span data-ttu-id="3160f-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="3160f-151">Example</span></span>

<span data-ttu-id="3160f-152">Pour obtenir un exemple, consultez la méthode [IWbemClassObject ::P ut](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) .</span><span class="sxs-lookup"><span data-stu-id="3160f-152">For an example, see the [IWbemClassObject::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3160f-153">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3160f-153">Requirements</span></span>

<span data-ttu-id="3160f-154">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3160f-154">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3160f-155">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="3160f-155">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="3160f-156">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3160f-156">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3160f-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3160f-157">See also</span></span>

- [<span data-ttu-id="3160f-158">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="3160f-158">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
