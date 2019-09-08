---
title: Fonction Delete (référence des API non managées)
description: La fonction Delete supprime la propriété spécifiée et tous ses qualificateurs d’une définition de classe CIM.
ms.date: 11/06/2017
api_name:
- Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Delete
helpviewer_keywords:
- Delete function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1bf9bd5d93d1affee649588138456269411d280
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798671"
---
# <a name="delete-function"></a><span data-ttu-id="d6b95-103">Delete, fonction</span><span class="sxs-lookup"><span data-stu-id="d6b95-103">Delete function</span></span>

<span data-ttu-id="d6b95-104">Supprime la propriété spécifiée et tous ses qualificateurs d’une définition de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="d6b95-104">Deletes the specified property and all of its qualifiers from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="d6b95-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6b95-105">Syntax</span></span>

```cpp
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```

## <a name="parameters"></a><span data-ttu-id="d6b95-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d6b95-106">Parameters</span></span>

`vFunc`\
<span data-ttu-id="d6b95-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="d6b95-107">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="d6b95-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="d6b95-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`\
<span data-ttu-id="d6b95-109">dans Nom de la propriété à supprimer.</span><span class="sxs-lookup"><span data-stu-id="d6b95-109">[in] The name of the property to delete.</span></span> <span data-ttu-id="d6b95-110">`wszName`doit être un pointeur vers un valide `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="d6b95-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="d6b95-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d6b95-111">Return value</span></span>

<span data-ttu-id="d6b95-112">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="d6b95-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d6b95-113">Constante</span><span class="sxs-lookup"><span data-stu-id="d6b95-113">Constant</span></span>  |<span data-ttu-id="d6b95-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="d6b95-114">Value</span></span>  |<span data-ttu-id="d6b95-115">Description</span><span class="sxs-lookup"><span data-stu-id="d6b95-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="d6b95-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="d6b95-116">0x80041001</span></span> | <span data-ttu-id="d6b95-117">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d6b95-117">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="d6b95-118">0x80041016</span><span class="sxs-lookup"><span data-stu-id="d6b95-118">0x80041016</span></span> | <span data-ttu-id="d6b95-119">La propriété ne peut pas être supprimée.</span><span class="sxs-lookup"><span data-stu-id="d6b95-119">The property cannot be deleted.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d6b95-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d6b95-120">0x80041008</span></span> | <span data-ttu-id="d6b95-121">`wszName` n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="d6b95-121">`wszName` is invalid.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="d6b95-122">0x80041002</span><span class="sxs-lookup"><span data-stu-id="d6b95-122">0x80041002</span></span> | <span data-ttu-id="d6b95-123">La propriété spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="d6b95-123">The specified property does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d6b95-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d6b95-124">0x80041006</span></span> | <span data-ttu-id="d6b95-125">La mémoire est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="d6b95-125">There is not enough memory to complete the operation.</span></span> |
| `WBEM_E_PROPAGATED_PROPERTY` | <span data-ttu-id="d6b95-126">0x8004101c</span><span class="sxs-lookup"><span data-stu-id="d6b95-126">0x8004101c</span></span> | <span data-ttu-id="d6b95-127">La propriété est héritée d’une classe de base.</span><span class="sxs-lookup"><span data-stu-id="d6b95-127">The property is inherited from a base class.</span></span> |
| `WBEM_E_SYSTEM_PROPERTY` | | <span data-ttu-id="d6b95-128">La propriété est une propriété système.</span><span class="sxs-lookup"><span data-stu-id="d6b95-128">The property is a system property.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d6b95-129">0</span><span class="sxs-lookup"><span data-stu-id="d6b95-129">0</span></span> | <span data-ttu-id="d6b95-130">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="d6b95-130">The function call was successful.</span></span>  |
| `WBEM_E_RESET_TO_DEFAULT` | <span data-ttu-id="d6b95-131">0x80041030</span><span class="sxs-lookup"><span data-stu-id="d6b95-131">0x80041030</span></span> | <span data-ttu-id="d6b95-132">La fonction a supprimé une valeur par défaut de remplacement pour la classe actuelle.</span><span class="sxs-lookup"><span data-stu-id="d6b95-132">The function deleted an override default value for the current class.</span></span> <span data-ttu-id="d6b95-133">La valeur par défaut de cette propriété dans la classe parente a été réactivée.</span><span class="sxs-lookup"><span data-stu-id="d6b95-133">The default value for this property in the parent class has been reactivated.</span></span> |

## <a name="remarks"></a><span data-ttu-id="d6b95-134">Notes</span><span class="sxs-lookup"><span data-stu-id="d6b95-134">Remarks</span></span>

<span data-ttu-id="d6b95-135">Cette fonction encapsule un appel à la méthode [IWbemClassObject ::D supprim](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) .</span><span class="sxs-lookup"><span data-stu-id="d6b95-135">This function wraps a call to the [IWbemClassObject::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-delete) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d6b95-136">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d6b95-136">Requirements</span></span>

<span data-ttu-id="d6b95-137">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6b95-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d6b95-138">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d6b95-138">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="d6b95-139">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d6b95-139">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d6b95-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6b95-140">See also</span></span>

- [<span data-ttu-id="d6b95-141">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="d6b95-141">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
