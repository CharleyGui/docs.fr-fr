---
title: Fonction GetPropertyOrigin (référence des API non managées)
description: La fonction GetPropertyOrigin détermine la classe dans laquelle une propriété est déclarée.
ms.date: 11/06/2017
api_name:
- GetPropertyOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyOrigin
helpviewer_keywords:
- GetPropertyOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6cab3765f0359f5dd18831acaaa1aefce3fe1081
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101853"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="a58a5-103">GetPropertyOrigin, fonction</span><span class="sxs-lookup"><span data-stu-id="a58a5-103">GetPropertyOrigin function</span></span>

<span data-ttu-id="a58a5-104">Détermine la classe dans laquelle une propriété est déclarée.</span><span class="sxs-lookup"><span data-stu-id="a58a5-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="a58a5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a58a5-105">Syntax</span></span>

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a><span data-ttu-id="a58a5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a58a5-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="a58a5-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="a58a5-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="a58a5-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="a58a5-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`\
<span data-ttu-id="a58a5-109">dans Nom de la propriété pour l’objet dont la classe propriétaire est demandée.</span><span class="sxs-lookup"><span data-stu-id="a58a5-109">[in] The name of the property for the object whose owning class is being requested.</span></span>

`pstrClassName`\
<span data-ttu-id="a58a5-110">à Reçoit le nom de la classe qui possède la propriété.</span><span class="sxs-lookup"><span data-stu-id="a58a5-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="a58a5-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a58a5-111">Return value</span></span>

<span data-ttu-id="a58a5-112">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="a58a5-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a58a5-113">Constante</span><span class="sxs-lookup"><span data-stu-id="a58a5-113">Constant</span></span>  |<span data-ttu-id="a58a5-114">valeur</span><span class="sxs-lookup"><span data-stu-id="a58a5-114">Value</span></span>  |<span data-ttu-id="a58a5-115">Description</span><span class="sxs-lookup"><span data-stu-id="a58a5-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="a58a5-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="a58a5-116">0x80041001</span></span> | <span data-ttu-id="a58a5-117">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="a58a5-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="a58a5-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="a58a5-118">0x80041002</span></span> | <span data-ttu-id="a58a5-119">La propriété spécifiée est introuvable.</span><span class="sxs-lookup"><span data-stu-id="a58a5-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="a58a5-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="a58a5-120">0x80041008</span></span> | <span data-ttu-id="a58a5-121">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="a58a5-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="a58a5-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="a58a5-122">0x80041006</span></span> | <span data-ttu-id="a58a5-123">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="a58a5-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="a58a5-124">0</span><span class="sxs-lookup"><span data-stu-id="a58a5-124">0</span></span> | <span data-ttu-id="a58a5-125">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="a58a5-125">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="a58a5-126">Notes</span><span class="sxs-lookup"><span data-stu-id="a58a5-126">Remarks</span></span>

<span data-ttu-id="a58a5-127">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) .</span><span class="sxs-lookup"><span data-stu-id="a58a5-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="a58a5-128">Étant donné qu’une classe peut hériter des propriétés d’une ou de plusieurs classes de base, les développeurs veulent souvent déterminer la propriété dans laquelle une méthode donnée est définie.</span><span class="sxs-lookup"><span data-stu-id="a58a5-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="a58a5-129">Le paramètre `pstrClassName` ne doit pas pointer vers un `BSTR` valide avant que la fonction soit appelée, car il s’agit d’un paramètre `out` ; ce pointeur n’est pas libéré après le retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="a58a5-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="a58a5-130">spécifications</span><span class="sxs-lookup"><span data-stu-id="a58a5-130">Requirements</span></span>

<span data-ttu-id="a58a5-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a58a5-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="a58a5-132">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="a58a5-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="a58a5-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a58a5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="a58a5-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a58a5-134">See also</span></span>

- [<span data-ttu-id="a58a5-135">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="a58a5-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
