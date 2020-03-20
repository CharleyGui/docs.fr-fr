---
title: Fonction Supprimermethod (référence API non managérisée)
description: La fonction DeleteMethod supprime la méthode spécifiée à partir d’une définition de classe CIM.
ms.date: 11/06/2017
api_name:
- DeleteMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- DeleteMethod
helpviewer_keywords:
- DeleteMethod function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 4059555d74c0b0f151332ddcf9faedecf238e795
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174990"
---
# <a name="deletemethod-function"></a><span data-ttu-id="51fe1-103">DeleteMethod, fonction</span><span class="sxs-lookup"><span data-stu-id="51fe1-103">DeleteMethod function</span></span>
<span data-ttu-id="51fe1-104">Supprime la méthode spécifiée à partir d’une définition de classe de l’ICM.</span><span class="sxs-lookup"><span data-stu-id="51fe1-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="51fe1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51fe1-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="51fe1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="51fe1-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="51fe1-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="51fe1-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="51fe1-108">[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="51fe1-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="51fe1-109">[dans] Le nom de la méthode à retirer de la table de classe.</span><span class="sxs-lookup"><span data-stu-id="51fe1-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="51fe1-110">`wszName`doit être un pointeur à un valide `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="51fe1-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="51fe1-111">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="51fe1-111">Return value</span></span>

<span data-ttu-id="51fe1-112">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="51fe1-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="51fe1-113">Constant</span><span class="sxs-lookup"><span data-stu-id="51fe1-113">Constant</span></span>  |<span data-ttu-id="51fe1-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="51fe1-114">Value</span></span>  |<span data-ttu-id="51fe1-115">Description</span><span class="sxs-lookup"><span data-stu-id="51fe1-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="51fe1-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="51fe1-116">0x80041002</span></span> | <span data-ttu-id="51fe1-117">La méthode spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="51fe1-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="51fe1-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="51fe1-118">0x80041006</span></span> | <span data-ttu-id="51fe1-119">La mémoire disponible est insuffisante pour terminer cette opération.</span><span class="sxs-lookup"><span data-stu-id="51fe1-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="51fe1-120">0</span><span class="sxs-lookup"><span data-stu-id="51fe1-120">0</span></span> | <span data-ttu-id="51fe1-121">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="51fe1-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="51fe1-122">Notes </span><span class="sxs-lookup"><span data-stu-id="51fe1-122">Remarks</span></span>

<span data-ttu-id="51fe1-123">Cette fonction enveloppe un appel à la méthode [IWbemClassObject::DeleteMethod.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod)</span><span class="sxs-lookup"><span data-stu-id="51fe1-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="51fe1-124">La suppression de la méthode n’est pas prise en charge pour les pointeurs [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui pointent vers les instances de l’ICM.</span><span class="sxs-lookup"><span data-stu-id="51fe1-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="51fe1-125">Spécifications</span><span class="sxs-lookup"><span data-stu-id="51fe1-125">Requirements</span></span>  
 <span data-ttu-id="51fe1-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51fe1-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51fe1-127">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="51fe1-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="51fe1-128">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="51fe1-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51fe1-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51fe1-129">See also</span></span>

- [<span data-ttu-id="51fe1-130">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="51fe1-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
