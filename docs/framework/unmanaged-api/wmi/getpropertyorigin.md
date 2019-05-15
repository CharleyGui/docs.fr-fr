---
title: Getpropertyorigin, fonction (référence des API non managées)
description: Getpropertyorigin, de la fonction détermine la classe dans laquelle une propriété est déclarée.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 542c4a01a9fd56587d51421709ffb990707f2ae0
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636783"
---
# <a name="getpropertyorigin-function"></a><span data-ttu-id="806b4-103">GetPropertyOrigin, fonction</span><span class="sxs-lookup"><span data-stu-id="806b4-103">GetPropertyOrigin function</span></span>

<span data-ttu-id="806b4-104">Détermine la classe dans laquelle une propriété est déclarée.</span><span class="sxs-lookup"><span data-stu-id="806b4-104">Determines the class in which a property is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="806b4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="806b4-105">Syntax</span></span>

```cpp
HRESULT GetPropertyOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```

## <a name="parameters"></a><span data-ttu-id="806b4-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="806b4-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="806b4-107">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="806b4-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="806b4-108">[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="806b4-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`\
<span data-ttu-id="806b4-109">[in] Le nom de la propriété de l’objet dont la classe propriétaire est demandée.</span><span class="sxs-lookup"><span data-stu-id="806b4-109">[in] The name of the property for the object whose owning class is being requested.</span></span>

`pstrClassName`\
<span data-ttu-id="806b4-110">[out] Reçoit le nom de la classe qui possède la propriété.</span><span class="sxs-lookup"><span data-stu-id="806b4-110">[out] Receives the name of the class that owns the property.</span></span>

## <a name="return-value"></a><span data-ttu-id="806b4-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="806b4-111">Return value</span></span>

<span data-ttu-id="806b4-112">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="806b4-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="806b4-113">Constante</span><span class="sxs-lookup"><span data-stu-id="806b4-113">Constant</span></span>  |<span data-ttu-id="806b4-114">Value</span><span class="sxs-lookup"><span data-stu-id="806b4-114">Value</span></span>  |<span data-ttu-id="806b4-115">Description</span><span class="sxs-lookup"><span data-stu-id="806b4-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="806b4-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="806b4-116">0x80041001</span></span> | <span data-ttu-id="806b4-117">Il y a eu une défaillance générale.</span><span class="sxs-lookup"><span data-stu-id="806b4-117">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="806b4-118">0x80041002</span><span class="sxs-lookup"><span data-stu-id="806b4-118">0x80041002</span></span> | <span data-ttu-id="806b4-119">La propriété spécifiée est introuvable.</span><span class="sxs-lookup"><span data-stu-id="806b4-119">The specified property was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="806b4-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="806b4-120">0x80041008</span></span> | <span data-ttu-id="806b4-121">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="806b4-121">A parameter is not valid.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="806b4-122">0x80041006</span><span class="sxs-lookup"><span data-stu-id="806b4-122">0x80041006</span></span> | <span data-ttu-id="806b4-123">Mémoire est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="806b4-123">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="806b4-124">0</span><span class="sxs-lookup"><span data-stu-id="806b4-124">0</span></span> | <span data-ttu-id="806b4-125">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="806b4-125">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="806b4-126">Notes</span><span class="sxs-lookup"><span data-stu-id="806b4-126">Remarks</span></span>

<span data-ttu-id="806b4-127">Cette fonction encapsule un appel à la [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) (méthode).</span><span class="sxs-lookup"><span data-stu-id="806b4-127">This function wraps a call to the [IWbemClassObject::GetPropertyOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getpropertyorigin) method.</span></span>

<span data-ttu-id="806b4-128">Car une classe peut hériter des propriétés d’une ou plusieurs classes de base, les développeurs souhaitent souvent de déterminer la propriété dans lequel une méthode donnée est définie.</span><span class="sxs-lookup"><span data-stu-id="806b4-128">Because a class can inherit properties from one or more base classes, developers often want to determine the property in which a given method is defined.</span></span>

<span data-ttu-id="806b4-129">Le `pstrClassName` paramètre ne doit pas pointer vers un valide `BSTR` avant que la fonction est appelée, car il s’agit d’un `out` paramètre ; ce pointeur n’est pas libéré une fois que la fonction retourne.</span><span class="sxs-lookup"><span data-stu-id="806b4-129">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="806b4-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="806b4-130">Requirements</span></span>

<span data-ttu-id="806b4-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="806b4-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="806b4-132">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="806b4-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="806b4-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="806b4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="806b4-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="806b4-134">See also</span></span>

- [<span data-ttu-id="806b4-135">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="806b4-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
