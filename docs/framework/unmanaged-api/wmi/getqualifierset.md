---
title: Fonction GetQualifierSet (référence API non gestion)
description: La fonction GetQualifierSet récupère l’ensemble de qualification pour une classe ou une instance.
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
ms.openlocfilehash: 368f0a13871bd48780fa30b370d37157d2724bb8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176771"
---
# <a name="getqualifierset-function"></a><span data-ttu-id="2ecf7-103">GetQualifierSet, fonction</span><span class="sxs-lookup"><span data-stu-id="2ecf7-103">GetQualifierSet function</span></span>
<span data-ttu-id="2ecf7-104">Récupère le jeu de qualificateurs pour une instance de classe ou une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-104">Retrieves the qualifier set for a class instance or a class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="2ecf7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ecf7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetQualifierSet (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [out] IWbemQualifierSet  **ppQualSet
);
```  

## <a name="parameters"></a><span data-ttu-id="2ecf7-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ecf7-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="2ecf7-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="2ecf7-108">[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="2ecf7-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppQualSet`  
<span data-ttu-id="2ecf7-109">[out] Reçoit le pointeur d’interface qui permet l’accès aux qualificatifs de l’objet de classe.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-109">[out] Receives the interface pointer that allows access to the qualifiers of the class object.</span></span> <span data-ttu-id="2ecf7-110">`ppQualSet` ne peut pas avoir la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-110">`ppQualSet` cannot be `null`.</span></span> <span data-ttu-id="2ecf7-111">Si une erreur se produit, un nouvel objet n’est pas retourné, et le pointeur n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-111">If an error occurs, a new object is not returned, and the pointer is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="2ecf7-112">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="2ecf7-112">Return value</span></span>

<span data-ttu-id="2ecf7-113">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="2ecf7-113">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="2ecf7-114">Constant</span><span class="sxs-lookup"><span data-stu-id="2ecf7-114">Constant</span></span>  |<span data-ttu-id="2ecf7-115">Valeur</span><span class="sxs-lookup"><span data-stu-id="2ecf7-115">Value</span></span>  |<span data-ttu-id="2ecf7-116">Description</span><span class="sxs-lookup"><span data-stu-id="2ecf7-116">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_FAILED` | <span data-ttu-id="2ecf7-117">0x80041001</span><span class="sxs-lookup"><span data-stu-id="2ecf7-117">0x80041001</span></span> | <span data-ttu-id="2ecf7-118">Il y a eu un échec général.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-118">There has been a general failure.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="2ecf7-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="2ecf7-119">0x80041002</span></span> | <span data-ttu-id="2ecf7-120">La méthode spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-120">The specified method does not exist.</span></span> |
|`WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="2ecf7-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="2ecf7-121">0x80041006</span></span> | <span data-ttu-id="2ecf7-122">La mémoire n'est pas suffisante pour terminer cette opération.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-122">Not enough memory is available to complete the operation.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="2ecf7-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="2ecf7-123">0x80041008</span></span> | <span data-ttu-id="2ecf7-124">Un paramètre est `null`.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-124">A parameter is `null`.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="2ecf7-125">0</span><span class="sxs-lookup"><span data-stu-id="2ecf7-125">0</span></span> | <span data-ttu-id="2ecf7-126">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="2ecf7-127">Notes </span><span class="sxs-lookup"><span data-stu-id="2ecf7-127">Remarks</span></span>

<span data-ttu-id="2ecf7-128">Cette fonction enveloppe un appel à [l’IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) méthode.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-128">This function wraps a call to the [IWbemClassObject::GetQualifierSet](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getqualifierset) method.</span></span>

<span data-ttu-id="2ecf7-129">Le [pointeur IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) permet à l’appelant d’ajouter, de modifier ou de supprimer ces qualificatifs.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-129">The [IWbemQualifierSet pointer](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) lets the caller add, edit, or delete these qualifiers.</span></span> <span data-ttu-id="2ecf7-130">Ces qualificatifs ajoutés, édités ou supprimés s’appliquent à l’ensemble de l’instance ou de la définition de classe.</span><span class="sxs-lookup"><span data-stu-id="2ecf7-130">Such added, edited, or deleted qualifiers apply to the entire instance or class definition.</span></span>

## <a name="requirements"></a><span data-ttu-id="2ecf7-131">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2ecf7-131">Requirements</span></span>  
<span data-ttu-id="2ecf7-132">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ecf7-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ecf7-133">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="2ecf7-133">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="2ecf7-134">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2ecf7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ecf7-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ecf7-135">See also</span></span>

- [<span data-ttu-id="2ecf7-136">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="2ecf7-136">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
