---
title: fonction QualifierSet_Delete (Référence API non gestion)
description: La fonction QualifierSet_Delete supprime un qualificatif par nom.
ms.date: 11/06/2017
api_name:
- QualifierSet_Delete
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Delete
helpviewer_keywords:
- QualifierSet_Delete function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 0d2a02ba9d89ba16e776bb73563eaebf8a92f1fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174899"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="c790d-103">QualifierSet_Delete, fonction</span><span class="sxs-lookup"><span data-stu-id="c790d-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="c790d-104">Supprime un qualificateur spécifié par nom.</span><span class="sxs-lookup"><span data-stu-id="c790d-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="c790d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c790d-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="c790d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c790d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c790d-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="c790d-107">[in] This parameter is unused.</span></span>

<span data-ttu-id="c790d-108">`ptr`[dans] Un pointeur à une instance [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="c790d-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="c790d-109">`wszName`[dans] Le nom du qualificatif à supprimer.</span><span class="sxs-lookup"><span data-stu-id="c790d-109">`wszName` [in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="c790d-110">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="c790d-110">Return value</span></span>

<span data-ttu-id="c790d-111">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="c790d-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c790d-112">Constant</span><span class="sxs-lookup"><span data-stu-id="c790d-112">Constant</span></span>  |<span data-ttu-id="c790d-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="c790d-113">Value</span></span>  |<span data-ttu-id="c790d-114">Description</span><span class="sxs-lookup"><span data-stu-id="c790d-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c790d-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c790d-115">0x80041008</span></span> | <span data-ttu-id="c790d-116">Le paramètre `wszName` n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="c790d-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="c790d-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="c790d-117">0x80041016</span></span> | <span data-ttu-id="c790d-118">Supprimer ce qualificatif est illégal.</span><span class="sxs-lookup"><span data-stu-id="c790d-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="c790d-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="c790d-119">0x80041002</span></span> | <span data-ttu-id="c790d-120">Le qualificatif spécifié n’a pas été trouvé.</span><span class="sxs-lookup"><span data-stu-id="c790d-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c790d-121">0</span><span class="sxs-lookup"><span data-stu-id="c790d-121">0</span></span> | <span data-ttu-id="c790d-122">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="c790d-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="c790d-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="c790d-123">0x40002</span></span> | <span data-ttu-id="c790d-124">Le remplacement local a été supprimé et le qualificatif original de l’objet parent a repris la portée.</span><span class="sxs-lookup"><span data-stu-id="c790d-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="c790d-125">Notes </span><span class="sxs-lookup"><span data-stu-id="c790d-125">Remarks</span></span>

<span data-ttu-id="c790d-126">Cette fonction enveloppe un appel à la méthode [IWbemQualifierSet::Delete.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete)</span><span class="sxs-lookup"><span data-stu-id="c790d-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="c790d-127">En raison des règles de propagation qualificatives, un qualificatif particulier peut avoir été hérité d’un autre objet et simplement remplacé dans la classe ou l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="c790d-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="c790d-128">Dans ce cas, la `QualifierSet_Delete` méthode réinitialise le qualificatif à sa valeur héritée originale.</span><span class="sxs-lookup"><span data-stu-id="c790d-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="c790d-129">La fonction dans ce cas `WBEM_S_RESET_TO_DEFAULT`renvoie le code d’état .</span><span class="sxs-lookup"><span data-stu-id="c790d-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="c790d-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c790d-130">Requirements</span></span>  
 <span data-ttu-id="c790d-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c790d-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c790d-132">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c790d-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c790d-133">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c790d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c790d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c790d-134">See also</span></span>

- [<span data-ttu-id="c790d-135">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="c790d-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
