---
title: Fonction PutMethod (référence des API non managées)
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
ms.openlocfilehash: 1d409507de593cf198fe87340eece6820eaefc63
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127336"
---
# <a name="putmethod-function"></a><span data-ttu-id="d726f-103">PutMethod fonction)</span><span class="sxs-lookup"><span data-stu-id="d726f-103">PutMethod function</span></span>
<span data-ttu-id="d726f-104">Crée une méthode.</span><span class="sxs-lookup"><span data-stu-id="d726f-104">Creates a method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="d726f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d726f-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="d726f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d726f-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d726f-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="d726f-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d726f-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="d726f-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="d726f-109">dans Nom de la méthode à créer.</span><span class="sxs-lookup"><span data-stu-id="d726f-109">[in] The name of the method to create.</span></span> 

`lFlags`  
<span data-ttu-id="d726f-110">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="d726f-110">[in] Reserved.</span></span> <span data-ttu-id="d726f-111">Ce paramètre doit avoir la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="d726f-111">This parameter must be 0.</span></span>

`pSignatureIn`  
<span data-ttu-id="d726f-112">dans Pointeur vers une copie de la [classe système __Parameters](/windows/desktop/WmiSdk/--parameters) qui contient les paramètres de `in` de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d726f-112">[in] A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `in` parameters for the method.</span></span> <span data-ttu-id="d726f-113">Ce paramètre est ignoré s’il est défini sur `null`.</span><span class="sxs-lookup"><span data-stu-id="d726f-113">This parameter is ignored if set to `null`.</span></span>  

`pSignatureOut`  
<span data-ttu-id="d726f-114">dans  Pointeur vers une copie de la [classe système __Parameters](/windows/desktop/WmiSdk/--parameters) qui contient les paramètres de `out` de la méthode.</span><span class="sxs-lookup"><span data-stu-id="d726f-114">[in]  A pointer to a copy of the [__Parameters system class](/windows/desktop/WmiSdk/--parameters) that contains the `out` parameters for the method.</span></span> <span data-ttu-id="d726f-115">Ce paramètre est ignoré s’il est défini sur `null`.</span><span class="sxs-lookup"><span data-stu-id="d726f-115">This parameter is ignored if set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="d726f-116">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d726f-116">Return value</span></span>

<span data-ttu-id="d726f-117">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="d726f-117">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d726f-118">Constante</span><span class="sxs-lookup"><span data-stu-id="d726f-118">Constant</span></span>  |<span data-ttu-id="d726f-119">valeur</span><span class="sxs-lookup"><span data-stu-id="d726f-119">Value</span></span>  |<span data-ttu-id="d726f-120">Description</span><span class="sxs-lookup"><span data-stu-id="d726f-120">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d726f-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d726f-121">0x80041008</span></span> | <span data-ttu-id="d726f-122">Un ou plusieurs paramètres ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="d726f-122">One or more parameters are not valid.</span></span> |
| `WBEM_E_INVALID_DUPLICATE_PARAMETER` | <span data-ttu-id="d726f-123">0x80041043</span><span class="sxs-lookup"><span data-stu-id="d726f-123">0x80041043</span></span> | <span data-ttu-id="d726f-124">Le paramètre de méthode `[in, out]` spécifié dans les objets *pInSignature* et *pOutSignature* ont des qualificateurs différents.</span><span class="sxs-lookup"><span data-stu-id="d726f-124">The `[in, out]` method parameter specified in both the *pInSignature* and *pOutSignature* objects have different qualifiers.</span></span>
| `WBEM_E_MISSING_PARAMETER_ID` | <span data-ttu-id="d726f-125">0x80041036</span><span class="sxs-lookup"><span data-stu-id="d726f-125">0x80041036</span></span> | <span data-ttu-id="d726f-126">Il manque un paramètre de méthode dans la spécification du qualificateur d' **ID** .</span><span class="sxs-lookup"><span data-stu-id="d726f-126">A method parameter is missing the specification of the **ID** qualifier.</span></span> |
| `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS` | <span data-ttu-id="d726f-127">0x80041038</span><span class="sxs-lookup"><span data-stu-id="d726f-127">0x80041038</span></span> | <span data-ttu-id="d726f-128">La série d’ID qui est assignée aux paramètres de méthode n’est pas consécutive ou ne commence pas à 0.</span><span class="sxs-lookup"><span data-stu-id="d726f-128">The ID series that is assigned to the method parameters is not consecutive or does not start at 0.</span></span> |
| `WBEM_E_PARAMETER_ID_ON_RETVAL` | <span data-ttu-id="d726f-129">0x80041039</span><span class="sxs-lookup"><span data-stu-id="d726f-129">0x80041039</span></span> | <span data-ttu-id="d726f-130">La valeur de retour d’une méthode a un qualificateur d' **ID** .</span><span class="sxs-lookup"><span data-stu-id="d726f-130">The return value for a method has an **ID** qualifier.</span></span> |
| `WBEM_E_PROPAGATED_METHOD` | <span data-ttu-id="d726f-131">0x80041034</span><span class="sxs-lookup"><span data-stu-id="d726f-131">0x80041034</span></span> | <span data-ttu-id="d726f-132">Une tentative de réutilisation d’un nom de méthode existant à partir d’une classe parente a été effectuée et les signatures ne correspondent pas.</span><span class="sxs-lookup"><span data-stu-id="d726f-132">An attempt was made to reuse an existing method name from a parent class, and the signatures did not match.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="d726f-133">0</span><span class="sxs-lookup"><span data-stu-id="d726f-133">0</span></span> | <span data-ttu-id="d726f-134">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="d726f-134">The function call was successful.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="d726f-135">Notes</span><span class="sxs-lookup"><span data-stu-id="d726f-135">Remarks</span></span>

<span data-ttu-id="d726f-136">Cette fonction encapsule un appel à la méthode [IWbemClassObject ::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .</span><span class="sxs-lookup"><span data-stu-id="d726f-136">This function wraps a call to the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

<span data-ttu-id="d726f-137">Cet appel de méthode est pris en charge uniquement si `ptr` est une définition de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="d726f-137">This method call is only supported if `ptr` is a CIM class definition.</span></span> <span data-ttu-id="d726f-138">La manipulation de méthode n’est pas disponible à partir de pointeurs [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui pointent vers des instances CIM.</span><span class="sxs-lookup"><span data-stu-id="d726f-138">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="d726f-139">Les utilisateurs ne peuvent pas créer de méthodes avec des noms commençant ou se terminant par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="d726f-139">Users cannot create methods with names that begin or end with an underscore.</span></span> <span data-ttu-id="d726f-140">Cela est réservé aux classes système et aux propriétés.</span><span class="sxs-lookup"><span data-stu-id="d726f-140">This is reserved for system classes and properties.</span></span>

<span data-ttu-id="d726f-141">Pour une méthode, les paramètres `in` et `out` sont décrits comme propriétés dans les objets [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="d726f-141">For a method, the `in` and `out` parameters are described as properties in [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) objects.</span></span>

<span data-ttu-id="d726f-142">Vous pouvez définir un paramètre `[in/out]` en ajoutant la même propriété aux objets pointés par les paramètres `pInSignature` et `pOutSignature`.</span><span class="sxs-lookup"><span data-stu-id="d726f-142">An `[in/out]` parameter can be defined by adding the same property to both objects pointed to by the `pInSignature` and `pOutSignature` parameters.</span></span> <span data-ttu-id="d726f-143">Dans ce cas, les propriétés partagent la même valeur de qualificateur d' **ID** .</span><span class="sxs-lookup"><span data-stu-id="d726f-143">In this case, the properties share the same **ID** qualifier value.</span></span>

<span data-ttu-id="d726f-144">Chaque propriété d’un objet de classe [__Parameters](/windows/desktop/WmiSdk/--parameters) autre que `ReturnValue` doit avoir un qualificateur d' **ID** , une valeur numérique de base zéro qui identifie l’ordre dans lequel les paramètres apparaissent.</span><span class="sxs-lookup"><span data-stu-id="d726f-144">Each property in a [__Parameters](/windows/desktop/WmiSdk/--parameters) class object other than `ReturnValue` must have an **ID** qualifier, a zero-based numeric value that identifies the order in which the parameters appear.</span></span> <span data-ttu-id="d726f-145">Deux paramètres ne peuvent pas avoir la même valeur d' **ID** , et aucune valeur d' **ID** ne peut être ignorée.</span><span class="sxs-lookup"><span data-stu-id="d726f-145">No two parameters can have the same **ID** value, and no **ID** value can be skipped.</span></span> <span data-ttu-id="d726f-146">Si l’une des conditions se produit, la fonction `PutMethod` retourne `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span><span class="sxs-lookup"><span data-stu-id="d726f-146">If either condition occurs, the `PutMethod` function returns `WBEM_E_NONCONSECUTIVE_PARAMETER_IDS`.</span></span>

## <a name="example"></a><span data-ttu-id="d726f-147">Exemple</span><span class="sxs-lookup"><span data-stu-id="d726f-147">Example</span></span>

<span data-ttu-id="d726f-148">Pour obtenir un exemple, consultez la méthode [IWbemClassObject ::P utmethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) .</span><span class="sxs-lookup"><span data-stu-id="d726f-148">For an example, see the [IWbemClassObject::PutMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-putmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d726f-149">spécifications</span><span class="sxs-lookup"><span data-stu-id="d726f-149">Requirements</span></span>  
 <span data-ttu-id="d726f-150">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d726f-150">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d726f-151">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="d726f-151">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d726f-152">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d726f-152">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d726f-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d726f-153">See also</span></span>

- [<span data-ttu-id="d726f-154">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="d726f-154">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
