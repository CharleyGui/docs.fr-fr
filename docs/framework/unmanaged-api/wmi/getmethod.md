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
ms.openlocfilehash: 48986f5ff1cbbb45840ec1a059aa86711848d717
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102586"
---
# <a name="getmethod-function"></a><span data-ttu-id="94820-103">GetMethod, fonction</span><span class="sxs-lookup"><span data-stu-id="94820-103">GetMethod function</span></span>

<span data-ttu-id="94820-104">Récupère les informations sur la méthode spécifiée.</span><span class="sxs-lookup"><span data-stu-id="94820-104">Retrieves information about the specified method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="94820-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94820-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="94820-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="94820-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="94820-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="94820-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="94820-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="94820-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="94820-109">dans Nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="94820-109">[in] The method name.</span></span> <span data-ttu-id="94820-110">Ce paramètre ne peut pas être `null` et doit pointer vers un `LPCWSTR`valide.</span><span class="sxs-lookup"><span data-stu-id="94820-110">This parameter cannot be `null` and must point to a valid `LPCWSTR`.</span></span>

`lFlags`\
<span data-ttu-id="94820-111">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="94820-111">[in] Reserved.</span></span> <span data-ttu-id="94820-112">Ce paramètre doit avoir la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="94820-112">This parameter must be 0.</span></span>

`ppInSignature`\
<span data-ttu-id="94820-113">à Pointeur vers l’adresse d’une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui décrit les paramètres in de la méthode.</span><span class="sxs-lookup"><span data-stu-id="94820-113">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the in parameters to the method.</span></span> <span data-ttu-id="94820-114">Ce paramètre est ignoré s’il est défini sur `null`.</span><span class="sxs-lookup"><span data-stu-id="94820-114">This parameter is ignored if it is set to `null`.</span></span>

`ppOutSignature`\
<span data-ttu-id="94820-115">à Pointeur vers l’adresse d’une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui décrit les paramètres de sortie de la méthode.</span><span class="sxs-lookup"><span data-stu-id="94820-115">[out] A pointer to the address of an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance that describes the out parameters to the method.</span></span> <span data-ttu-id="94820-116">Ce paramètre est ignoré s’il est défini sur `null`.</span><span class="sxs-lookup"><span data-stu-id="94820-116">This parameter is ignored if it is set to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="94820-117">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="94820-117">Return value</span></span>

<span data-ttu-id="94820-118">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="94820-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="94820-119">Constante</span><span class="sxs-lookup"><span data-stu-id="94820-119">Constant</span></span>  |<span data-ttu-id="94820-120">valeur</span><span class="sxs-lookup"><span data-stu-id="94820-120">Value</span></span>  |<span data-ttu-id="94820-121">Description</span><span class="sxs-lookup"><span data-stu-id="94820-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="94820-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="94820-122">0x80041002</span></span> | <span data-ttu-id="94820-123">La propriété spécifiée est introuvable.</span><span class="sxs-lookup"><span data-stu-id="94820-123">The specified property was not found.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="94820-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="94820-124">0x80041006</span></span> | <span data-ttu-id="94820-125">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="94820-125">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="94820-126">0</span><span class="sxs-lookup"><span data-stu-id="94820-126">0</span></span> | <span data-ttu-id="94820-127">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="94820-127">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="94820-128">Notes</span><span class="sxs-lookup"><span data-stu-id="94820-128">Remarks</span></span>

<span data-ttu-id="94820-129">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .</span><span class="sxs-lookup"><span data-stu-id="94820-129">This function wraps a call to the [IWbemClassObject::GetMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="94820-130">La gestion Windows peut définir le pointeur [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) sur `null` si la méthode n’a pas de paramètres in.</span><span class="sxs-lookup"><span data-stu-id="94820-130">Windows Management can set the [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointer to `null` if the method has no in parameters.</span></span>

<span data-ttu-id="94820-131">Dans `ppInSignature` et `ppOutSignature` décrivent les paramètres in et out, respectivement, en tant que propriétés dans une instance `IWbemClassObject` de la classe système [_Parameters](/windows/desktop/WmiSdk/--parameters).</span><span class="sxs-lookup"><span data-stu-id="94820-131">In `ppInSignature` and `ppOutSignature` describe in and out parameters, respectively, as properties in a `IWbemClassObject` instance of the system class [_Parameters](/windows/desktop/WmiSdk/--parameters).</span></span> <span data-ttu-id="94820-132">Les propriétés de `ppInSignature` sont nommées `Param`*n*, où *n* est la position du paramètre dans la signature de la méthode (par exemple, `Param1`, `Param2`, etc.).</span><span class="sxs-lookup"><span data-stu-id="94820-132">The properties in `ppInSignature` are named `Param`*n*, where *n* is the position of the parameter in the method signature (such as `Param1`, `Param2`, etc.).</span></span> <span data-ttu-id="94820-133">Les propriétés de `ppOutSignature` sont également nommées `Param`*n*, et la valeur de retour est nommée `ReturnValue`.</span><span class="sxs-lookup"><span data-stu-id="94820-133">The properties in `ppOutSignature` are also named `Param`*n*, and the return value is named `ReturnValue`.</span></span> <span data-ttu-id="94820-134">Pour plus d’informations et pour obtenir un exemple, consultez [IWbemClassObject :: GetMethod, méthode](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span><span class="sxs-lookup"><span data-stu-id="94820-134">For more information and an example, see [IWbemClassObject::GetMethod method](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod).</span></span>

## <a name="requirements"></a><span data-ttu-id="94820-135">spécifications</span><span class="sxs-lookup"><span data-stu-id="94820-135">Requirements</span></span>

<span data-ttu-id="94820-136">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94820-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="94820-137">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="94820-137">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="94820-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="94820-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="94820-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94820-139">See also</span></span>

- [<span data-ttu-id="94820-140">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="94820-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
