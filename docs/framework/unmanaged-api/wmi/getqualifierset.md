---
title: Fonction GetQualifierSet (référence des API non managées)
description: La fonction GetQualifierSet récupère le qualificateur défini pour une classe ou une instance.
ms.date: 11/06/2017
api_name:
- GetQualifierSet
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetQualifierSet
helpviewer_keywords:
- GetQualifierSet function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f9bb882a0f62499167b79bf3e6691d05e394720f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671341"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="d959d-103">GetQualifierSet, fonction</span><span class="sxs-lookup"><span data-stu-id="d959d-103">GetQualifierSet function</span></span>

<span data-ttu-id="d959d-104">Récupère le jeu de qualificateurs pour une instance de classe ou une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="d959d-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="d959d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d959d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [out] IWbemQualifierSet  **ppQualSet
);
```  

## <a name="parameters"></a><span data-ttu-id="d959d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d959d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d959d-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="d959d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d959d-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="d959d-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="d959d-109">à Reçoit le pointeur d’interface qui autorise l’accès aux qualificateurs de l’objet de classe.</span><span class="sxs-lookup"><span data-stu-id="d959d-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="d959d-110">`ppQualSet` ne peut pas avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="d959d-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="d959d-111">Si une erreur se produit, aucun nouvel objet n’est retourné et le pointeur reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="d959d-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="d959d-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d959d-112">Return value</span></span>

<span data-ttu-id="d959d-113">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="d959d-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d959d-114">Constante</span><span class="sxs-lookup"><span data-stu-id="d959d-114">Constant</span></span>  |<span data-ttu-id="d959d-115">Value</span><span class="sxs-lookup"><span data-stu-id="d959d-115">Value</span></span>  |<span data-ttu-id="d959d-116">Description</span><span class="sxs-lookup"><span data-stu-id="d959d-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="d959d-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="d959d-117">0x80041001</span></span> | <span data-ttu-id="d959d-118">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d959d-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="d959d-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="d959d-119">0x80041002</span></span> | <span data-ttu-id="d959d-120">La méthode spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="d959d-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d959d-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d959d-121">0x80041006</span></span> | <span data-ttu-id="d959d-122">La mémoire n'est pas suffisante pour terminer cette opération.</span><span class="sxs-lookup"><span data-stu-id="d959d-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d959d-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d959d-123">0x80041008</span></span> | <span data-ttu-id="d959d-124">Un paramètre est `null` .</span><span class="sxs-lookup"><span data-stu-id="d959d-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d959d-125">0</span><span class="sxs-lookup"><span data-stu-id="d959d-125">0</span></span> | <span data-ttu-id="d959d-126">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="d959d-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d959d-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="d959d-127">Remarks</span></span>

<span data-ttu-id="d959d-128">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="d959d-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span>

<span data-ttu-id="d959d-129">Le [pointeur IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) permet à l’appelant d’ajouter, de modifier ou de supprimer ces qualificateurs.</span><span class="sxs-lookup"><span data-stu-id="d959d-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="d959d-130">Les qualificateurs ajoutés, modifiés ou supprimés s’appliquent à l’ensemble de la définition de la classe ou de l’instance.</span><span class="sxs-lookup"><span data-stu-id="d959d-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="d959d-131">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d959d-131">Requirements</span></span>  

<span data-ttu-id="d959d-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d959d-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d959d-133">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="d959d-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d959d-134">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d959d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d959d-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d959d-135">See also</span></span>

- [<span data-ttu-id="d959d-136">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="d959d-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
