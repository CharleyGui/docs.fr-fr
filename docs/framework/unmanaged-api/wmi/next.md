---
title: Fonction Next (référence des API non managées)
description: La fonction Next récupère la propriété Next dans une énumération.
ms.date: 11/06/2017
api_name:
- Next
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Next
helpviewer_keywords:
- Next function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 587e085f6fe9f6c19d3605c673cd3bd6f68162f1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127376"
---
# <a name="next-function"></a><span data-ttu-id="bcbc3-103">Fonction Next</span><span class="sxs-lookup"><span data-stu-id="bcbc3-103">Next function</span></span>
<span data-ttu-id="bcbc3-104">Récupère la propriété suivante dans une énumération qui commence par un appel à [BeginEnumeration](beginenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="bcbc3-104">Retrieves the next property in an enumeration that begins with a call to [BeginEnumeration](beginenumeration.md).</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="bcbc3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bcbc3-105">Syntax</span></span>

```cpp
HRESULT Next (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lFlags,
   [out] BSTR*            pstrName,
   [out] VARIANT*         pVal,
   [out] CIMTYPE*         pvtType,
   [out] LONG*            plFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="bcbc3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bcbc3-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="bcbc3-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="bcbc3-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="bcbc3-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`\
<span data-ttu-id="bcbc3-109">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-109">[in] Reserved.</span></span> <span data-ttu-id="bcbc3-110">Ce paramètre doit avoir la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-110">This parameter must be 0.</span></span>

`pstrName`\
<span data-ttu-id="bcbc3-111">à Nouvelle `BSTR` qui contient le nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-111">[out] A new `BSTR` that contains the property name.</span></span> <span data-ttu-id="bcbc3-112">Vous pouvez définir ce paramètre sur `null` si le nom n’est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-112">You can set this parameter to `null` if the name is not required.</span></span>

`pVal`\
<span data-ttu-id="bcbc3-113">à `VARIANT` rempli avec la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-113">[out] A `VARIANT` filled with the value of the property.</span></span> <span data-ttu-id="bcbc3-114">Vous pouvez définir ce paramètre sur `null` si la valeur n’est pas requise.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-114">You can set this parameter to `null` if the value is not required.</span></span> <span data-ttu-id="bcbc3-115">Si la fonction retourne un code d’erreur, le `VARIANT` passé à `pVal` n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-115">If the function returns an error code, the `VARIANT` passed to `pVal` is left unmodified.</span></span>

`pvtType`\
<span data-ttu-id="bcbc3-116">à Pointeur vers une variable `CIMTYPE` (une `LONG` dans laquelle le type de la propriété est placé).</span><span class="sxs-lookup"><span data-stu-id="bcbc3-116">[out] A pointer to a `CIMTYPE` variable (a `LONG` into which the type of the property is placed).</span></span> <span data-ttu-id="bcbc3-117">La valeur de cette propriété peut être un `VT_NULL_VARIANT`, auquel cas il est nécessaire de déterminer le type réel de la propriété.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-117">The value of this property can be a `VT_NULL_VARIANT`, in which case it is necessary to determine the actual type of the property.</span></span> <span data-ttu-id="bcbc3-118">Ce paramètre peut également être `null`.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-118">This parameter can also be `null`.</span></span>

`plFlavor`\
<span data-ttu-id="bcbc3-119">[out] `null`, ou une valeur qui reçoit des informations sur l’origine de la propriété.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-119">[out] `null`, or a value that receives information on the origin of the property.</span></span> <span data-ttu-id="bcbc3-120">Pour connaître les valeurs possibles, consultez la section [remarques].</span><span class="sxs-lookup"><span data-stu-id="bcbc3-120">See the [Remarks] section for possible values.</span></span>

## <a name="return-value"></a><span data-ttu-id="bcbc3-121">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bcbc3-121">Return value</span></span>

<span data-ttu-id="bcbc3-122">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="bcbc3-122">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bcbc3-123">Constante</span><span class="sxs-lookup"><span data-stu-id="bcbc3-123">Constant</span></span>  |<span data-ttu-id="bcbc3-124">valeur</span><span class="sxs-lookup"><span data-stu-id="bcbc3-124">Value</span></span>  |<span data-ttu-id="bcbc3-125">Description</span><span class="sxs-lookup"><span data-stu-id="bcbc3-125">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="bcbc3-126">0x80041001</span><span class="sxs-lookup"><span data-stu-id="bcbc3-126">0x80041001</span></span> | <span data-ttu-id="bcbc3-127">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-127">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bcbc3-128">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bcbc3-128">0x80041008</span></span> | <span data-ttu-id="bcbc3-129">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-129">A parameter is invalid.</span></span> |
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="bcbc3-130">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="bcbc3-130">0x8004101d</span></span> | <span data-ttu-id="bcbc3-131">Aucun appel à la fonction [`BeginEnumeration`](beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="bcbc3-131">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bcbc3-132">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bcbc3-132">0x80041006</span></span> | <span data-ttu-id="bcbc3-133">Mémoire disponible insuffisante pour commencer une nouvelle énumération.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-133">Not enough memory is available to begin a new enumeration.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="bcbc3-134">0x80041015</span><span class="sxs-lookup"><span data-stu-id="bcbc3-134">0x80041015</span></span> | <span data-ttu-id="bcbc3-135">L’appel de procédure distante entre le processus en cours et l’administration de Windows a échoué.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-135">The remote procedure call between the current process and Windows Management failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="bcbc3-136">0</span><span class="sxs-lookup"><span data-stu-id="bcbc3-136">0</span></span> | <span data-ttu-id="bcbc3-137">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-137">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="bcbc3-138">0x40005</span><span class="sxs-lookup"><span data-stu-id="bcbc3-138">0x40005</span></span> | <span data-ttu-id="bcbc3-139">Il n’y a plus de propriétés dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-139">There are no more properties in the enumeration.</span></span> |

## <a name="remarks"></a><span data-ttu-id="bcbc3-140">Notes</span><span class="sxs-lookup"><span data-stu-id="bcbc3-140">Remarks</span></span>

<span data-ttu-id="bcbc3-141">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) .</span><span class="sxs-lookup"><span data-stu-id="bcbc3-141">This function wraps a call to the [IWbemClassObject::Next](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-next) method.</span></span>

<span data-ttu-id="bcbc3-142">Cette méthode retourne également les propriétés système.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-142">This method also returns system properties.</span></span>

<span data-ttu-id="bcbc3-143">Si le type sous-jacent de la propriété est un chemin d’accès d’objet, une date ou une heure, ou un autre type spécial, le type retourné ne contient pas suffisamment d’informations.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-143">If the underlying type of the property is an object path, a date or time, or another special type, then the returned type does not contain enough information.</span></span> <span data-ttu-id="bcbc3-144">L’appelant doit examiner la `CIMTYPE` pour la propriété spécifiée afin de déterminer si la propriété est une référence d’objet, une date ou une heure, ou un autre type spécial.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-144">The caller must examine the `CIMTYPE` for the specified property to determine if the property is an object reference, a date or time, or another special type.</span></span>

<span data-ttu-id="bcbc3-145">Si `plFlavor` n’est pas `null`, la valeur `LONG` reçoit des informations sur l’origine de la propriété, comme suit :</span><span class="sxs-lookup"><span data-stu-id="bcbc3-145">If `plFlavor` is not `null`, the `LONG` value receives information about the origin of the property, as follows:</span></span>

|<span data-ttu-id="bcbc3-146">Constante</span><span class="sxs-lookup"><span data-stu-id="bcbc3-146">Constant</span></span>  |<span data-ttu-id="bcbc3-147">valeur</span><span class="sxs-lookup"><span data-stu-id="bcbc3-147">Value</span></span>  |<span data-ttu-id="bcbc3-148">Description</span><span class="sxs-lookup"><span data-stu-id="bcbc3-148">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_ORIGIN_SYSTEM` | <span data-ttu-id="bcbc3-149">0x40</span><span class="sxs-lookup"><span data-stu-id="bcbc3-149">0x40</span></span> | <span data-ttu-id="bcbc3-150">La propriété est une propriété système standard.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-150">The property is a standard system property.</span></span> |
| `WBEM_FLAVOR_ORIGIN_PROPAGATED` | <span data-ttu-id="bcbc3-151">0x20</span><span class="sxs-lookup"><span data-stu-id="bcbc3-151">0x20</span></span> | <span data-ttu-id="bcbc3-152">Pour une classe : la propriété est héritée de la classe parente.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-152">For a class: The property is inherited from the parent class.</span></span> <br> <span data-ttu-id="bcbc3-153">Pour une instance : la propriété, alors qu’elle est héritée de la classe parente, n’a pas été modifiée par l’instance.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-153">For an instance: The property, while inherited from the parent class, has not been modified by the instance.</span></span>  |
| `WBEM_FLAVOR_ORIGIN_LOCAL` | <span data-ttu-id="bcbc3-154">0</span><span class="sxs-lookup"><span data-stu-id="bcbc3-154">0</span></span> | <span data-ttu-id="bcbc3-155">Pour une classe : la propriété appartient à la classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-155">For a class: The property belongs to the derived class.</span></span> <br> <span data-ttu-id="bcbc3-156">Pour une instance : la propriété est modifiée par l’instance ; autrement dit, une valeur a été fournie ou un qualificateur a été ajouté ou modifié.</span><span class="sxs-lookup"><span data-stu-id="bcbc3-156">For an instance: The property is modified by the instance; that is, a value was supplied, or a qualifier was added or modified.</span></span> |

## <a name="requirements"></a><span data-ttu-id="bcbc3-157">spécifications</span><span class="sxs-lookup"><span data-stu-id="bcbc3-157">Requirements</span></span>

<span data-ttu-id="bcbc3-158">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcbc3-158">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="bcbc3-159">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="bcbc3-159">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="bcbc3-160">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bcbc3-160">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bcbc3-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bcbc3-161">See also</span></span>

- [<span data-ttu-id="bcbc3-162">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="bcbc3-162">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
