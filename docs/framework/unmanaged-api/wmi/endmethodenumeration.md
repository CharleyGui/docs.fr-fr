---
title: Fonction EndMethodEnumeration (Référence API non managérée)
description: La fonction EndMethodEnumeration met fin à une séquence d’énumération de méthode.
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
ms.openlocfilehash: 63667d0668f905ded2aedd961be0d1831faf838c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175003"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="388f8-103">EndMethodEnumeration, fonction</span><span class="sxs-lookup"><span data-stu-id="388f8-103">EndMethodEnumeration function</span></span>
<span data-ttu-id="388f8-104">Termine une séquence de recensement commencée par un appel à la [fonction BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="388f8-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="388f8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="388f8-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="388f8-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="388f8-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="388f8-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="388f8-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="388f8-108">[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="388f8-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="388f8-109">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="388f8-109">Return value</span></span>

<span data-ttu-id="388f8-110">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="388f8-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="388f8-111">Constant</span><span class="sxs-lookup"><span data-stu-id="388f8-111">Constant</span></span>  |<span data-ttu-id="388f8-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="388f8-112">Value</span></span>  |<span data-ttu-id="388f8-113">Description</span><span class="sxs-lookup"><span data-stu-id="388f8-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="388f8-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="388f8-114">0x8004101d</span></span> | <span data-ttu-id="388f8-115">Une erreur interne s’est produite.</span><span class="sxs-lookup"><span data-stu-id="388f8-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="388f8-116">0</span><span class="sxs-lookup"><span data-stu-id="388f8-116">0</span></span> | <span data-ttu-id="388f8-117">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="388f8-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="388f8-118">Notes </span><span class="sxs-lookup"><span data-stu-id="388f8-118">Remarks</span></span>

<span data-ttu-id="388f8-119">Cette fonction enveloppe un appel à [l’IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) méthode.</span><span class="sxs-lookup"><span data-stu-id="388f8-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="388f8-120">L’appelant commence la séquence de recensement à l’aide de la [fonction BeginMethodEnumeration,](beginmethodenumeration.md)puis appelle la [fonction NextMethod](nextmethod.md )jusqu’à ce que la méthode revient `WBEM_S_NO_MORE_DATA`.</span><span class="sxs-lookup"><span data-stu-id="388f8-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="388f8-121">L’appelant termine optionnellement `EndMethodEnumeration`la séquence en appelant .</span><span class="sxs-lookup"><span data-stu-id="388f8-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="388f8-122">L’appelant peut mettre fin à `EndMethodEnumeration` l’énumération tôt en appelant à tout moment.</span><span class="sxs-lookup"><span data-stu-id="388f8-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="388f8-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="388f8-123">Requirements</span></span>  
 <span data-ttu-id="388f8-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="388f8-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="388f8-125">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="388f8-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="388f8-126">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="388f8-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="388f8-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="388f8-127">See also</span></span>

- [<span data-ttu-id="388f8-128">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="388f8-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
