---
title: Getpropertyhandle, fonction (référence des API non managées)
description: Getpropertyhandle, de la fonction retourne un handle unique qui identifie une propriété.
ms.date: 11/06/2017
api_name:
- GetPropertyHandle
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetPropertyHandle
helpviewer_keywords:
- GetPropertyHandle function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d1397188b38066bac6375da0c76e7d66724a75d7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636243"
---
# <a name="getpropertyhandle-function"></a><span data-ttu-id="2d01d-103">GetPropertyHandle, fonction</span><span class="sxs-lookup"><span data-stu-id="2d01d-103">GetPropertyHandle function</span></span>

<span data-ttu-id="2d01d-104">Retourne un handle unique qui identifie une propriété.</span><span class="sxs-lookup"><span data-stu-id="2d01d-104">Returns a unique handle that identifies a property.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="2d01d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d01d-105">Syntax</span></span>

```cpp
HRESULT GetPropertyHandle (
   [in] int                  vFunc,
   [in] IWbemObjectAccess*   ptr,
   [in] LPCWSTR              wszPropertyName,
   [out] CIMTYPE*            pType,
   [out] long*               pHandle
);
```

## <a name="parameters"></a><span data-ttu-id="2d01d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d01d-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="2d01d-107">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="2d01d-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="2d01d-108">[in] Un pointeur vers un [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span><span class="sxs-lookup"><span data-stu-id="2d01d-108">[in] A pointer to an [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) instance.</span></span>

`wszPropertyName`\
<span data-ttu-id="2d01d-109">[in] Se terminant par null chaîne de caractères encodés UTF16 qui contient le nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="2d01d-109">[in] A null-terminated string of UTF16-encoded characters that contains the property name.</span></span>

`pType`\
<span data-ttu-id="2d01d-110">[out] Un pointeur vers un [ `CIMTYPE` ](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) membre d’énumération qui représente le type CIM de la propriété.</span><span class="sxs-lookup"><span data-stu-id="2d01d-110">[out] A pointer to a [`CIMTYPE`](/windows/desktop/api/wbemcli/ne-wbemcli-tag_cimtype_enumeration) enumeration member that represents the CIM type of the property.</span></span>

`pHandle`\
<span data-ttu-id="2d01d-111">[out] Pointeur vers un entier qui contient le descripteur de propriété.</span><span class="sxs-lookup"><span data-stu-id="2d01d-111">[out] A pointer to an integer that contains the property handle.</span></span>

## <a name="return-value"></a><span data-ttu-id="2d01d-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2d01d-112">Return value</span></span>

<span data-ttu-id="2d01d-113">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="2d01d-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2d01d-114">Constante</span><span class="sxs-lookup"><span data-stu-id="2d01d-114">Constant</span></span>  |<span data-ttu-id="2d01d-115">Value</span><span class="sxs-lookup"><span data-stu-id="2d01d-115">Value</span></span>  |<span data-ttu-id="2d01d-116">Description</span><span class="sxs-lookup"><span data-stu-id="2d01d-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="2d01d-117">0x80041002</span><span class="sxs-lookup"><span data-stu-id="2d01d-117">0x80041002</span></span> | <span data-ttu-id="2d01d-118">Le nom de la propriété spécifiée est introuvable.</span><span class="sxs-lookup"><span data-stu-id="2d01d-118">The specified property name was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2d01d-119">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2d01d-119">0x80041008</span></span> | <span data-ttu-id="2d01d-120">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="2d01d-120">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_SUPPORTED` | <span data-ttu-id="2d01d-121">0x8004100c</span><span class="sxs-lookup"><span data-stu-id="2d01d-121">0x8004100c</span></span> | <span data-ttu-id="2d01d-122">La propriété demandée est de type sont `CIM_OBJECT` ou `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="2d01d-122">The requested property is of type are `CIM_OBJECT` or `CIM_ARRAY`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2d01d-123">0</span><span class="sxs-lookup"><span data-stu-id="2d01d-123">0</span></span> | <span data-ttu-id="2d01d-124">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="2d01d-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="2d01d-125">Notes</span><span class="sxs-lookup"><span data-stu-id="2d01d-125">Remarks</span></span>

<span data-ttu-id="2d01d-126">Cette fonction encapsule un appel à la [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) (méthode).</span><span class="sxs-lookup"><span data-stu-id="2d01d-126">This function wraps a call to the [IWbemClassObject::GetPropertyHandle](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemobjectaccess-getpropertyhandle) method.</span></span>

<span data-ttu-id="2d01d-127">Vous pouvez utiliser ce handle pour identifier les propriétés lorsque vous utilisez [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) méthodes pour lire ou écrire des valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="2d01d-127">You can use this handle to identify properties when using  [IWbemObjectAccess](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemobjectaccess) methods to read or write property values.</span></span>

<span data-ttu-id="2d01d-128">Handles peuvent être récupérées pour les propriétés de tous les types de données autre que `CIM_OBJECT` et `CIM_ARRAY`.</span><span class="sxs-lookup"><span data-stu-id="2d01d-128">Handles can be retrieved for properties of all data types other than `CIM_OBJECT` and `CIM_ARRAY`.</span></span> <span data-ttu-id="2d01d-129">Retourné handles travail sur toutes les instances d’une classe.</span><span class="sxs-lookup"><span data-stu-id="2d01d-129">Returned handles work across all instances of a class.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d01d-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2d01d-130">Requirements</span></span>

<span data-ttu-id="2d01d-131">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d01d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="2d01d-132">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2d01d-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="2d01d-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2d01d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2d01d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d01d-134">See also</span></span>

- [<span data-ttu-id="2d01d-135">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="2d01d-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
