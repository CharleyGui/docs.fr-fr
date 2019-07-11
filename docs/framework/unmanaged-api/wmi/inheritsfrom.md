---
title: InheritsFrom (fonction) (référence des API non managées)
description: La fonction InheritsFrom détermine si une classe ou instance dérive d’une classe parente particulier.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c04a08c9712359453b9c5a9d136e22e1de8648a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746509"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="4c903-103">InheritsFrom (fonction)</span><span class="sxs-lookup"><span data-stu-id="4c903-103">InheritsFrom function</span></span>
<span data-ttu-id="4c903-104">Détermine si l’instance ou la classe active dérive d’une classe parente spécifié.</span><span class="sxs-lookup"><span data-stu-id="4c903-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="4c903-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c903-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="4c903-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4c903-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="4c903-107">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="4c903-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="4c903-108">[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="4c903-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="4c903-109">[in] Le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="4c903-109">[in] The name of the class.</span></span> <span data-ttu-id="4c903-110">`wszAncestor` doit pointer vers un valide `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="4c903-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="4c903-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4c903-111">Return value</span></span>

<span data-ttu-id="4c903-112">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="4c903-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="4c903-113">Constante</span><span class="sxs-lookup"><span data-stu-id="4c903-113">Constant</span></span>  |<span data-ttu-id="4c903-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="4c903-114">Value</span></span>  |<span data-ttu-id="4c903-115">Description</span><span class="sxs-lookup"><span data-stu-id="4c903-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="4c903-116">0</span><span class="sxs-lookup"><span data-stu-id="4c903-116">0</span></span> | <span data-ttu-id="4c903-117">L’objet actuel hérite `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="4c903-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="4c903-118">1</span><span class="sxs-lookup"><span data-stu-id="4c903-118">1</span></span> | <span data-ttu-id="4c903-119">L’objet en cours n’hérite pas de `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="4c903-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="4c903-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="4c903-120">0x80041008</span></span> | <span data-ttu-id="4c903-121">`wszAncestor` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="4c903-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="4c903-122">Notes</span><span class="sxs-lookup"><span data-stu-id="4c903-122">Remarks</span></span>

<span data-ttu-id="4c903-123">Cette fonction encapsule un appel à la [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) (méthode).</span><span class="sxs-lookup"><span data-stu-id="4c903-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4c903-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4c903-124">Requirements</span></span>  
 <span data-ttu-id="4c903-125">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c903-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c903-126">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="4c903-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="4c903-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4c903-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c903-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c903-128">See also</span></span>

- [<span data-ttu-id="4c903-129">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="4c903-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
