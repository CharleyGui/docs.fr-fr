---
title: Fonction GetMethodQualifierSet (référence des API non managées)
description: La fonction GetMethodQualifierSet récupère l’ensemble de qualificateurs d’une méthode.
ms.date: 11/06/2017
api_name:
- GetMethodQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodQualifierSet
helpviewer_keywords:
- GetMethodQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86a7788736c3c12cfcfd405de88dfadfb14c1eca
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798530"
---
# <a name="getmethodqualifierset-function"></a><span data-ttu-id="96981-103">GetMethodQualifierSet, fonction</span><span class="sxs-lookup"><span data-stu-id="96981-103">GetMethodQualifierSet function</span></span>

<span data-ttu-id="96981-104">Récupère le jeu de qualificateurs pour une méthode particulière.</span><span class="sxs-lookup"><span data-stu-id="96981-104">Retrieves the qualifier set for a particular method.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="96981-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="96981-105">Syntax</span></span>

```cpp
HRESULT GetMethodQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethod,
   [out] IWbemQualifierSet  **ppQualSet
);
```

## <a name="parameters"></a><span data-ttu-id="96981-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="96981-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="96981-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="96981-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="96981-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="96981-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethod`\
<span data-ttu-id="96981-109">dans Nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="96981-109">[in] The method  name.</span></span> <span data-ttu-id="96981-110">`wszMethod`doit pointer vers un `LPCWSTR`valide.</span><span class="sxs-lookup"><span data-stu-id="96981-110">`wszMethod` must point to a valid `LPCWSTR`.</span></span>

`ppQualSet`\
<span data-ttu-id="96981-111">à Reçoit le pointeur d’interface qui autorise l’accès aux qualificateurs de la méthode.</span><span class="sxs-lookup"><span data-stu-id="96981-111">[out] Receives the interface pointer that allows access to the qualifiers of the method.</span></span> <span data-ttu-id="96981-112">`ppQualSet` ne peut pas avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="96981-112">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="96981-113">Si une erreur se produit, un nouvel objet n’est pas retourné et le pointeur est défini pour pointer vers `null`.</span><span class="sxs-lookup"><span data-stu-id="96981-113">If an error occurs, a new object is not returned, and the pointer is set to point to `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="96981-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="96981-114">Return value</span></span>

<span data-ttu-id="96981-115">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="96981-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="96981-116">Constante</span><span class="sxs-lookup"><span data-stu-id="96981-116">Constant</span></span>  |<span data-ttu-id="96981-117">`Value`</span><span class="sxs-lookup"><span data-stu-id="96981-117">Value</span></span>  |<span data-ttu-id="96981-118">Description</span><span class="sxs-lookup"><span data-stu-id="96981-118">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="96981-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="96981-119">0x80041002</span></span> | <span data-ttu-id="96981-120">La méthode spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="96981-120">The specified method does not exist.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="96981-121">0x80041008</span><span class="sxs-lookup"><span data-stu-id="96981-121">0x80041008</span></span> | <span data-ttu-id="96981-122">Un paramètre est `null`.</span><span class="sxs-lookup"><span data-stu-id="96981-122">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="96981-123">0</span><span class="sxs-lookup"><span data-stu-id="96981-123">0</span></span> | <span data-ttu-id="96981-124">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="96981-124">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="96981-125">Notes</span><span class="sxs-lookup"><span data-stu-id="96981-125">Remarks</span></span>

<span data-ttu-id="96981-126">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="96981-126">This function wraps a call to the [IWbemClassObject::GetMethodQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethodqualifierset) method.</span></span>

<span data-ttu-id="96981-127">Un appel à cette fonction est pris en charge uniquement si l’objet actuel est une définition de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="96981-127">A call to this function is supported only if the current object is a CIM class definition.</span></span> <span data-ttu-id="96981-128">La manipulation de méthode n’est pas disponible pour les pointeurs [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui pointent vers des instances CIM.</span><span class="sxs-lookup"><span data-stu-id="96981-128">Method manipulation is not available for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

<span data-ttu-id="96981-129">Étant donné que chaque méthode peut avoir ses propres qualificateurs, le [pointeur IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) permet à l’appelant d’ajouter, de modifier ou de supprimer ces qualificateurs.</span><span class="sxs-lookup"><span data-stu-id="96981-129">Because each method may have its own qualifiers, the [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span>

## <a name="requirements"></a><span data-ttu-id="96981-130">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="96981-130">Requirements</span></span>

<span data-ttu-id="96981-131">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96981-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="96981-132">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="96981-132">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="96981-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="96981-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="96981-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96981-134">See also</span></span>

- [<span data-ttu-id="96981-135">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="96981-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
