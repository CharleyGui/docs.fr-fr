---
title: Endmethodenumeration, fonction (référence des API non managées)
description: Endmethodenumeration, de la fonction termine une séquence d’énumération de méthode.
ms.date: 11/06/2017
api_name:
- EndMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- EndMethodEnumeration
helpviewer_keywords:
- EndMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f62ea692c055b0537394ad5e16501d4162faef12
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746831"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="f9259-103">EndMethodEnumeration, fonction</span><span class="sxs-lookup"><span data-stu-id="f9259-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="f9259-104">Met fin à une séquence d’énumération démarrée avec un appel à la [beginmethodenumeration, fonction](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="f9259-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="f9259-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9259-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr 
); 
```  

## <a name="parameters"></a><span data-ttu-id="f9259-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f9259-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f9259-107">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="f9259-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f9259-108">[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="f9259-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="f9259-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f9259-109">Return value</span></span>

<span data-ttu-id="f9259-110">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="f9259-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f9259-111">Constante</span><span class="sxs-lookup"><span data-stu-id="f9259-111">Constant</span></span>  |<span data-ttu-id="f9259-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="f9259-112">Value</span></span>  |<span data-ttu-id="f9259-113">Description</span><span class="sxs-lookup"><span data-stu-id="f9259-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="f9259-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="f9259-114">0x8004101d</span></span> | <span data-ttu-id="f9259-115">Une erreur interne s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f9259-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="f9259-116">0</span><span class="sxs-lookup"><span data-stu-id="f9259-116">0</span></span> | <span data-ttu-id="f9259-117">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="f9259-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f9259-118">Notes</span><span class="sxs-lookup"><span data-stu-id="f9259-118">Remarks</span></span>

<span data-ttu-id="f9259-119">Cette fonction encapsule un appel à la [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) (méthode).</span><span class="sxs-lookup"><span data-stu-id="f9259-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="f9259-120">L’appelant commence la séquence d’énumération à l’aide [beginmethodenumeration, fonction](beginmethodenumeration.md), puis appelle la [NextMethod fonction](nextmethod.md )jusqu'à ce que la méthode retourne `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="f9259-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="f9259-121">L’appelant éventuellement termine la séquence en appelant `EndMethodEnumeration`.</span><span class="sxs-lookup"><span data-stu-id="f9259-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="f9259-122">L’appelant peut arrêter l’énumération au début en appelant `EndMethodEnumeration` à tout moment.</span><span class="sxs-lookup"><span data-stu-id="f9259-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="f9259-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f9259-123">Requirements</span></span>  
 <span data-ttu-id="f9259-124">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9259-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9259-125">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f9259-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f9259-126">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f9259-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9259-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f9259-127">See also</span></span>

- [<span data-ttu-id="f9259-128">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="f9259-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
