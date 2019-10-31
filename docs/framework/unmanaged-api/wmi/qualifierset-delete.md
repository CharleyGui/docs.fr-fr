---
title: Fonction QualifierSet_Delete (référence des API non managées)
description: La fonction QualifierSet_Delete supprime un qualificateur par son nom.
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
ms.openlocfilehash: e7bedcb5c56f9976f8dfd2619081971075d0d809
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127301"
---
# <a name="qualifierset_delete-function"></a><span data-ttu-id="cf43d-103">QualifierSet_Delete fonction)</span><span class="sxs-lookup"><span data-stu-id="cf43d-103">QualifierSet_Delete function</span></span>
<span data-ttu-id="cf43d-104">Supprime un qualificateur spécifié par nom.</span><span class="sxs-lookup"><span data-stu-id="cf43d-104">Deletes a specified qualifier by name.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="cf43d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf43d-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Delete (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName
); 
```  

## <a name="parameters"></a><span data-ttu-id="cf43d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf43d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="cf43d-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="cf43d-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="cf43d-108">dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="cf43d-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="cf43d-109">dans Nom du qualificateur à supprimer.</span><span class="sxs-lookup"><span data-stu-id="cf43d-109">[in] The name of the qualifier to delete.</span></span>

## <a name="return-value"></a><span data-ttu-id="cf43d-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="cf43d-110">Return value</span></span>

<span data-ttu-id="cf43d-111">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="cf43d-111">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="cf43d-112">Constante</span><span class="sxs-lookup"><span data-stu-id="cf43d-112">Constant</span></span>  |<span data-ttu-id="cf43d-113">valeur</span><span class="sxs-lookup"><span data-stu-id="cf43d-113">Value</span></span>  |<span data-ttu-id="cf43d-114">Description</span><span class="sxs-lookup"><span data-stu-id="cf43d-114">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="cf43d-115">0x80041008</span><span class="sxs-lookup"><span data-stu-id="cf43d-115">0x80041008</span></span> | <span data-ttu-id="cf43d-116">Le paramètre `wszName` n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="cf43d-116">The `wszName` parameter is not valid.</span></span> |
|`WBEM_E_INVALID_OPERATION` | <span data-ttu-id="cf43d-117">0x80041016</span><span class="sxs-lookup"><span data-stu-id="cf43d-117">0x80041016</span></span> | <span data-ttu-id="cf43d-118">La suppression de ce qualificateur n’est pas conforme.</span><span class="sxs-lookup"><span data-stu-id="cf43d-118">Deleting this qualifier is illegal.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="cf43d-119">0x80041002</span><span class="sxs-lookup"><span data-stu-id="cf43d-119">0x80041002</span></span> | <span data-ttu-id="cf43d-120">Le qualificateur spécifié est introuvable.</span><span class="sxs-lookup"><span data-stu-id="cf43d-120">The specified qualifier was not found.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="cf43d-121">0</span><span class="sxs-lookup"><span data-stu-id="cf43d-121">0</span></span> | <span data-ttu-id="cf43d-122">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="cf43d-122">The function call was successful.</span></span>  |
| `WBEM_S_RESET_TO_DEFAULT` | <span data-ttu-id="cf43d-123">0x40002</span><span class="sxs-lookup"><span data-stu-id="cf43d-123">0x40002</span></span> | <span data-ttu-id="cf43d-124">La substitution locale a été supprimée et le qualificateur d’origine de l’objet parent a repris la portée.</span><span class="sxs-lookup"><span data-stu-id="cf43d-124">The local override was deleted and the original qualifier from the parent object has resumed scope.</span></span> |

## <a name="remarks"></a><span data-ttu-id="cf43d-125">Notes</span><span class="sxs-lookup"><span data-stu-id="cf43d-125">Remarks</span></span>

<span data-ttu-id="cf43d-126">Cette fonction encapsule un appel à la méthode [IWbemQualifierSet ::D supprim](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) .</span><span class="sxs-lookup"><span data-stu-id="cf43d-126">This function wraps a call to the [IWbemQualifierSet::Delete](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-delete) method.</span></span>

<span data-ttu-id="cf43d-127">En raison des règles de propagation des qualificateurs, un qualificateur particulier peut avoir été hérité d’un autre objet et simplement substitué dans la classe ou l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="cf43d-127">Due to qualifier propagation rules, a particular qualifier may have been inherited from another object and merely overridden in the current class or instance.</span></span> <span data-ttu-id="cf43d-128">Dans ce cas, la méthode `QualifierSet_Delete` réinitialise le qualificateur à sa valeur héritée d’origine.</span><span class="sxs-lookup"><span data-stu-id="cf43d-128">In this case, the `QualifierSet_Delete` method resets the qualifier to its original inherited value.</span></span> <span data-ttu-id="cf43d-129">Dans ce cas, la fonction retourne le code d’État `WBEM_S_RESET_TO_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="cf43d-129">The function in this case returns the status code `WBEM_S_RESET_TO_DEFAULT`.</span></span>

## <a name="requirements"></a><span data-ttu-id="cf43d-130">spécifications</span><span class="sxs-lookup"><span data-stu-id="cf43d-130">Requirements</span></span>  
 <span data-ttu-id="cf43d-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf43d-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf43d-132">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="cf43d-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="cf43d-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cf43d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf43d-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cf43d-134">See also</span></span>

- [<span data-ttu-id="cf43d-135">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="cf43d-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
