---
title: Fonction PutMethod (référence API non managérisée)
description: La fonction PutMethod crée une méthode.
ms.date: 11/06/2017
api_name:
- PutMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutMethod
helpviewer_keywords:
- PutMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 93347b7290211b5d62829604678261fdf4da1ec3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174912"
---
# <a name="putmethod-function"></a><span data-ttu-id="7b2c5-103">PutMethod, fonction</span><span class="sxs-lookup"><span data-stu-id="7b2c5-103">PutMethod function</span></span>
<span data-ttu-id="7b2c5-104">Crée une méthode.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="7b2c5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b2c5-105">Syntax</span></span>  
  
```cpp  
HRESULT PutMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*  ptr,
   [in] LPCWSTR            wszName,
   [in] LONG               lFlags,
   [in] IWbemClassObject*  pInSignature,
   [in] IWbemClassObject*  pOutSignature
);
```  

## <a name="parameters"></a><span data-ttu-id="7b2c5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7b2c5-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="7b2c5-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="7b2c5-108">[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="7b2c5-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="7b2c5-109">[dans] Le nom de la méthode à créer.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-109">[in] The name of the method to create.</span></span>

`lFlags`  
<span data-ttu-id="7b2c5-110">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-110">[in] Reserved.</span></span> <span data-ttu-id="7b2c5-111">Ce paramètre doit être de 0.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="7b2c5-112">[dans] Un pointeur à une copie de la classe `in` __Parameters [système](/windows/desktop/WmiSdk/--parameters) qui contient les paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="7b2c5-113">Ce paramètre est `null`ignoré si défini à .</span><span class="sxs-lookup"><span data-stu-id="7b2c5-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="7b2c5-114">[dans]  Un pointeur à une copie de la classe `out` __Parameters [système](/windows/desktop/WmiSdk/--parameters) qui contient les paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="7b2c5-115">Ce paramètre est `null`ignoré si défini à .</span><span class="sxs-lookup"><span data-stu-id="7b2c5-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="7b2c5-116">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7b2c5-116">Return value</span></span>

<span data-ttu-id="7b2c5-117">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="7b2c5-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7b2c5-118">Constant</span><span class="sxs-lookup"><span data-stu-id="7b2c5-118">Constant</span></span>  |<span data-ttu-id="7b2c5-119">Valeur</span><span class="sxs-lookup"><span data-stu-id="7b2c5-119">Value</span></span>  |<span data-ttu-id="7b2c5-120">Description</span><span class="sxs-lookup"><span data-stu-id="7b2c5-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7b2c5-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7b2c5-121">0x80041008</span></span> | <span data-ttu-id="7b2c5-122">Un ou plusieurs paramètres ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="7b2c5-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="7b2c5-123">0x80041043</span></span> | <span data-ttu-id="7b2c5-124">Le `[in, out]` paramètre de méthode spécifié dans les objets *pInSignature* et *pOutSignature* ont des qualificatifs différents.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="7b2c5-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="7b2c5-125">0x80041036</span></span> | <span data-ttu-id="7b2c5-126">Un paramètre de méthode manque la spécification du qualificatif **d’identification.**</span><span class="sxs-lookup"><span data-stu-id="7b2c5-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="7b2c5-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="7b2c5-127">0x80041038</span></span> | <span data-ttu-id="7b2c5-128">La série ID qui est attribuée aux paramètres de la méthode n’est pas consécutive ou ne commence pas à 0.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="7b2c5-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="7b2c5-129">0x80041039</span></span> | <span data-ttu-id="7b2c5-130">La valeur de retour d’une méthode a un qualificatif **d’identification.**</span><span class="sxs-lookup"><span data-stu-id="7b2c5-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="7b2c5-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="7b2c5-131">0x80041034</span></span> | <span data-ttu-id="7b2c5-132">On a tenté de réutiliser un nom de méthode existant d’une classe de parents, et les signatures ne correspondaient pas.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="7b2c5-133">0</span><span class="sxs-lookup"><span data-stu-id="7b2c5-133">0</span></span> | <span data-ttu-id="7b2c5-134">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="7b2c5-135">Notes </span><span class="sxs-lookup"><span data-stu-id="7b2c5-135">Remarks</span></span>

<span data-ttu-id="7b2c5-136">Cette fonction enveloppe un appel à la méthode [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)</span><span class="sxs-lookup"><span data-stu-id="7b2c5-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="7b2c5-137">Cet appel de méthode `ptr` n’est pris en charge que s’il s’agit d’une définition de classe de l’ICM.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="7b2c5-138">La manipulation de la méthode n’est pas disponible à partir des pointeurs [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui pointent vers les instances de l’ICM.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="7b2c5-139">Les utilisateurs ne peuvent pas créer des méthodes avec des noms qui commencent ou se terminent par un soulignement.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="7b2c5-140">Ceci est réservé aux classes et aux propriétés du système.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="7b2c5-141">Pour une méthode, `out` les paramètres et les `in` paramètres sont décrits comme des propriétés dans les objets [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="7b2c5-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="7b2c5-142">Un `[in/out]` paramètre peut être défini en ajoutant la `pInSignature` même `pOutSignature` propriété aux deux objets pointés par les paramètres et les paramètres.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="7b2c5-143">Dans ce cas, les propriétés partagent la même valeur de qualification **d’identification.**</span><span class="sxs-lookup"><span data-stu-id="7b2c5-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="7b2c5-144">Chaque propriété dans un objet de `ReturnValue` classe [__Parameters](/windows/desktop/WmiSdk/--parameters) autre que doit avoir un qualificatif **d’identification,** une valeur numérique à base de zéro qui identifie l’ordre dans lequel les paramètres apparaissent.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="7b2c5-145">Aucun des deux paramètres ne peut avoir la même valeur **d’identification,** et aucune valeur **d’identification** ne peut être ignorée.</span><span class="sxs-lookup"><span data-stu-id="7b2c5-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="7b2c5-146">Si l’une `PutMethod` ou `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`l’autre condition se produit, la fonction revient .</span><span class="sxs-lookup"><span data-stu-id="7b2c5-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="7b2c5-147"> Exemple</span><span class="sxs-lookup"><span data-stu-id="7b2c5-147">Example</span></span>

<span data-ttu-id="7b2c5-148">Par exemple, voir la méthode [IWbemClassObject::PutMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod)</span><span class="sxs-lookup"><span data-stu-id="7b2c5-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7b2c5-149">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7b2c5-149">Requirements</span></span>  
 <span data-ttu-id="7b2c5-150">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b2c5-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b2c5-151">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7b2c5-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7b2c5-152">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7b2c5-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b2c5-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7b2c5-153">See also</span></span>

- [<span data-ttu-id="7b2c5-154">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="7b2c5-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
