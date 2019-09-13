---
title: GetMethod, fonction (référence des API non managées)
description: La fonction GetMethod récupère des informations sur une méthode.
ms.date: 11/06/2017
api_name:
- GetMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethod
helpviewer_keywords:
- GetMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9cc185bf8cccb8ed3c24e28954afd86464602d7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798568"
---
# <a name="getmethod-function"></a><span data-ttu-id="ef707-103">GetMethod, fonction</span><span class="sxs-lookup"><span data-stu-id="ef707-103">GetMethod function</span></span>

<span data-ttu-id="ef707-104">Récupère les informations sur la méthode spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ef707-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ef707-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ef707-105">Syntax</span></span>

```cpp
HRESULT GetMethod (
   [in] int                vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszName,
   [in] LONG                lFlags,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature
);
```

## <a name="parameters"></a><span data-ttu-id="ef707-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ef707-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="ef707-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="ef707-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="ef707-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="ef707-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="ef707-109">dans Nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ef707-109">[in] The method name.</span></span> <span data-ttu-id="ef707-110">Ce paramètre ne peut `null` pas avoir la valeur et doit `LPCWSTR`pointer vers un valide.</span><span class="sxs-lookup"><span data-stu-id="ef707-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`\
<span data-ttu-id="ef707-111">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="ef707-111">[in] Reserved.</span></span> <span data-ttu-id="ef707-112">Ce paramètre doit avoir la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="ef707-112">This parameter must be 0.</span></span>

`ppInSignature`\
<span data-ttu-id="ef707-113">à Pointeur vers l’adresse d’une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui décrit les paramètres in de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ef707-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in parameters to the method.</span></span> <span data-ttu-id="ef707-114">Ce paramètre est ignoré s’il est défini sur `null`.</span><span class="sxs-lookup"><span data-stu-id="ef707-114">This parameter is ignored if it is set to `null`.</span></span>

`ppOutSignature`\
<span data-ttu-id="ef707-115">à Pointeur vers l’adresse d’une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui décrit les paramètres de sortie de la méthode.</span><span class="sxs-lookup"><span data-stu-id="ef707-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="ef707-116">Ce paramètre est ignoré s’il est défini sur `null`.</span><span class="sxs-lookup"><span data-stu-id="ef707-116">This parameter is ignored if it is set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="ef707-117">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ef707-117">Return value</span></span>

<span data-ttu-id="ef707-118">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="ef707-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ef707-119">Constante</span><span class="sxs-lookup"><span data-stu-id="ef707-119">Constant</span></span>  |<span data-ttu-id="ef707-120">`Value`</span><span class="sxs-lookup"><span data-stu-id="ef707-120">Value</span></span>  |<span data-ttu-id="ef707-121">Description</span><span class="sxs-lookup"><span data-stu-id="ef707-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="ef707-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="ef707-122">0x80041002</span></span> | <span data-ttu-id="ef707-123">La propriété spécifiée est introuvable.</span><span class="sxs-lookup"><span data-stu-id="ef707-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ef707-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ef707-124">0x80041006</span></span> | <span data-ttu-id="ef707-125">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="ef707-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="ef707-126">0</span><span class="sxs-lookup"><span data-stu-id="ef707-126">0</span></span> | <span data-ttu-id="ef707-127">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="ef707-127">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ef707-128">Notes</span><span class="sxs-lookup"><span data-stu-id="ef707-128">Remarks</span></span>

<span data-ttu-id="ef707-129">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .</span><span class="sxs-lookup"><span data-stu-id="ef707-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="ef707-130">La gestion Windows peut définir le pointeur [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) sur `null` si la méthode n’a pas de paramètres in.</span><span class="sxs-lookup"><span data-stu-id="ef707-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="ef707-131">Dans `ppInSignature` `IWbemClassObject` et `ppOutSignature` décrivent les paramètres in et out, respectivement, en tant que propriétés dans une instance de la classe système [_Parameters](/windows/desktop/WmiSdk/--parameters).</span><span class="sxs-lookup"><span data-stu-id="ef707-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="ef707-132">Les propriétés de `ppInSignature` sont nommées `Param` *n*, où *n* est la position du paramètre dans la signature de la méthode ( `Param1`par `Param2`exemple,,, etc.).</span><span class="sxs-lookup"><span data-stu-id="ef707-132">The properties in `ppInSignature` are named `Param`*n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="ef707-133">Les propriétés de `ppOutSignature` sont également `Param`nommées *n*, et la valeur de retour `ReturnValue`est nommée.</span><span class="sxs-lookup"><span data-stu-id="ef707-133">The properties in `ppOutSignature` are also named `Param`*n*, and the return value is named `ReturnValue`.</span></span> <span data-ttu-id="ef707-134">Pour plus d’informations et pour obtenir un exemple, consultez [IWbemClassObject :: GetMethod, méthode](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span><span class="sxs-lookup"><span data-stu-id="ef707-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="ef707-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ef707-135">Requirements</span></span>

<span data-ttu-id="ef707-136">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef707-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="ef707-137">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="ef707-137">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="ef707-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ef707-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ef707-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef707-139">See also</span></span>

- [<span data-ttu-id="ef707-140">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="ef707-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
