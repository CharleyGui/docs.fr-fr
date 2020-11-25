---
title: Fonction EndMethodEnumeration (référence des API non managées)
description: La fonction EndMethodEnumeration termine une séquence d’énumération de méthode.
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
ms.openlocfilehash: 82f50530967699427d8a00b1c9f518b639273626
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708060"
---
# <a name="endmethodenumeration-function"></a><span data-ttu-id="53e74-103">EndMethodEnumeration, fonction</span><span class="sxs-lookup"><span data-stu-id="53e74-103">EndMethodEnumeration function</span></span>

<span data-ttu-id="53e74-104">Termine une séquence d’énumération démarrée avec un appel à la [fonction BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="53e74-104">Terminates an enumeration sequence started with a call to the [BeginMethodEnumeration function](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="53e74-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53e74-105">Syntax</span></span>  
  
```cpp  
HRESULT EndMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr
);
```  

## <a name="parameters"></a><span data-ttu-id="53e74-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="53e74-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="53e74-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="53e74-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="53e74-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="53e74-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="53e74-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="53e74-109">Return value</span></span>

<span data-ttu-id="53e74-110">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="53e74-110">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="53e74-111">Constante</span><span class="sxs-lookup"><span data-stu-id="53e74-111">Constant</span></span>  |<span data-ttu-id="53e74-112">Value</span><span class="sxs-lookup"><span data-stu-id="53e74-112">Value</span></span>  |<span data-ttu-id="53e74-113">Description</span><span class="sxs-lookup"><span data-stu-id="53e74-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_UNEXPECTED` | <span data-ttu-id="53e74-114">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="53e74-114">0x8004101d</span></span> | <span data-ttu-id="53e74-115">Une erreur interne s’est produite.</span><span class="sxs-lookup"><span data-stu-id="53e74-115">An internal error occurred.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="53e74-116">0</span><span class="sxs-lookup"><span data-stu-id="53e74-116">0</span></span> | <span data-ttu-id="53e74-117">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="53e74-117">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="53e74-118">Remarques</span><span class="sxs-lookup"><span data-stu-id="53e74-118">Remarks</span></span>

<span data-ttu-id="53e74-119">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) .</span><span class="sxs-lookup"><span data-stu-id="53e74-119">This function wraps a call to the [IWbemClassObject::EndMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-endmethodenumeration) method.</span></span>

<span data-ttu-id="53e74-120">L’appelant commence la séquence d’énumération à l’aide de la [fonction BeginMethodEnumeration](beginmethodenumeration.md), puis appelle la [fonction NextMethod](nextmethod.md )jusqu’à ce que la méthode retourne `WBEM_S_NO_MORE_DATA` .</span><span class="sxs-lookup"><span data-stu-id="53e74-120">The caller begins the enumeration sequence using [BeginMethodEnumeration function](beginmethodenumeration.md), and then calls the [NextMethod function](nextmethod.md )until the method  returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="53e74-121">L’appelant termine éventuellement la séquence en appelant `EndMethodEnumeration` .</span><span class="sxs-lookup"><span data-stu-id="53e74-121">The caller optionally finishes the sequence by calling `EndMethodEnumeration`.</span></span> <span data-ttu-id="53e74-122">L’appelant peut arrêter l’énumération tôt en appelant `EndMethodEnumeration` à tout moment.</span><span class="sxs-lookup"><span data-stu-id="53e74-122">The caller may terminate the enumeration early by calling `EndMethodEnumeration` at any time.</span></span>

## <a name="requirements"></a><span data-ttu-id="53e74-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="53e74-123">Requirements</span></span>  

 <span data-ttu-id="53e74-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53e74-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53e74-125">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="53e74-125">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="53e74-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="53e74-126">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53e74-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53e74-127">See also</span></span>

- [<span data-ttu-id="53e74-128">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="53e74-128">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
