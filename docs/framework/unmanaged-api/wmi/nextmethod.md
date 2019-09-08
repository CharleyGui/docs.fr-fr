---
title: Fonction NextMethod (référence des API non managées)
description: La fonction NextMethod récupère la méthode suivante dans une énumération.
ms.date: 11/06/2017
api_name:
- NextMethod
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- NextMethod
helpviewer_keywords:
- NextMethod function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee743a4499824bea723043d5a2c7d57d7cbd7106
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798420"
---
# <a name="nextmethod-function"></a><span data-ttu-id="a2642-103">NextMethod fonction)</span><span class="sxs-lookup"><span data-stu-id="a2642-103">NextMethod function</span></span>
<span data-ttu-id="a2642-104">Récupère la méthode suivante dans une énumération qui commence par un appel à [BeginMethodEnumeration](beginmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a2642-104">Retrieves the next method in an enumeration that begins with a call to [BeginMethodEnumeration](beginmethodenumeration.md).</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="a2642-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2642-105">Syntax</span></span>  
  
```cpp  
HRESULT NextMethod (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LONG                lFlags,
   [out] BSTR*              pName,
   [out] IWbemClassObject** ppInSignature,
   [out] IWbemClassObject** ppOutSignature   
); 
```  

## <a name="parameters"></a><span data-ttu-id="a2642-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a2642-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="a2642-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="a2642-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="a2642-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="a2642-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="a2642-109">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="a2642-109">[in] Reserved.</span></span> <span data-ttu-id="a2642-110">Ce paramètre doit avoir la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="a2642-110">This parameter must be 0.</span></span>

`pName`  
<span data-ttu-id="a2642-111">à Pointeur qui pointe vers `null` avant l’appel.</span><span class="sxs-lookup"><span data-stu-id="a2642-111">[out] A pointer that points to `null` prior to the call.</span></span> <span data-ttu-id="a2642-112">Lorsque la fonction retourne, adresse d’un nouveau `BSTR` qui contient le nom de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a2642-112">When the function returns, the address of a new `BSTR` that contains the method name.</span></span> 

`ppSignatureIn`  
<span data-ttu-id="a2642-113">à Pointeur qui reçoit un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui contient les `in` paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a2642-113">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `in` parameters for the method.</span></span> 

`ppSignatureOut`  
<span data-ttu-id="a2642-114">à Pointeur qui reçoit un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui contient les `out` paramètres de la méthode.</span><span class="sxs-lookup"><span data-stu-id="a2642-114">[out] A pointer that receives a pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) that contains the `out` parameters for the method.</span></span> 

## <a name="return-value"></a><span data-ttu-id="a2642-115">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a2642-115">Return value</span></span>

<span data-ttu-id="a2642-116">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="a2642-116">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="a2642-117">Constante</span><span class="sxs-lookup"><span data-stu-id="a2642-117">Constant</span></span>  |<span data-ttu-id="a2642-118">Valeur</span><span class="sxs-lookup"><span data-stu-id="a2642-118">Value</span></span>  |<span data-ttu-id="a2642-119">Description</span><span class="sxs-lookup"><span data-stu-id="a2642-119">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_UNEXPECTED` | <span data-ttu-id="a2642-120">0x8004101d</span><span class="sxs-lookup"><span data-stu-id="a2642-120">0x8004101d</span></span> | <span data-ttu-id="a2642-121">Aucun appel à la [`BeginEnumeration`](beginenumeration.md) fonction.</span><span class="sxs-lookup"><span data-stu-id="a2642-121">There was no call to the [`BeginEnumeration`](beginenumeration.md) function.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="a2642-122">0</span><span class="sxs-lookup"><span data-stu-id="a2642-122">0</span></span> | <span data-ttu-id="a2642-123">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="a2642-123">The function call was successful.</span></span>  |
| `WBEM_S_NO_MORE_DATA` | <span data-ttu-id="a2642-124">0x40005</span><span class="sxs-lookup"><span data-stu-id="a2642-124">0x40005</span></span> | <span data-ttu-id="a2642-125">Il n’y a plus de propriétés dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="a2642-125">There are no more properties in the enumeration.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="a2642-126">Notes</span><span class="sxs-lookup"><span data-stu-id="a2642-126">Remarks</span></span>

<span data-ttu-id="a2642-127">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) .</span><span class="sxs-lookup"><span data-stu-id="a2642-127">This function wraps a call to the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

<span data-ttu-id="a2642-128">L’appelant commence la séquence d’énumération en appelant la fonction [BeginMethodEnumeration](beginmethodenumeration.md) , puis appelle la fonction [NextMethod] jusqu’à ce `WBEM_S_NO_MORE_DATA`que la fonction retourne.</span><span class="sxs-lookup"><span data-stu-id="a2642-128">The caller begins the enumeration sequence by calling the [BeginMethodEnumeration](beginmethodenumeration.md) function, and then calls the [NextMethod] function until the function returns `WBEM_S_NO_MORE_DATA`.</span></span> <span data-ttu-id="a2642-129">Si vous le souhaitez, l’appelant termine la séquence en appelant [EndMethodEnumeration](endmethodenumeration.md).</span><span class="sxs-lookup"><span data-stu-id="a2642-129">Optionally, the caller finishes the sequence by calling [EndMethodEnumeration](endmethodenumeration.md).</span></span> <span data-ttu-id="a2642-130">L’appelant peut arrêter l’énumération tôt en appelant [EndMethodEnumeration](endmethodenumeration.md) à tout moment.</span><span class="sxs-lookup"><span data-stu-id="a2642-130">The caller may terminate the enumeration early by calling [EndMethodEnumeration](endmethodenumeration.md) at any time.</span></span>

## <a name="example"></a><span data-ttu-id="a2642-131">Exemples</span><span class="sxs-lookup"><span data-stu-id="a2642-131">Example</span></span>

<span data-ttu-id="a2642-132">Pour obtenir C++ un exemple, consultez la méthode [IWbemClassObject :: NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) .</span><span class="sxs-lookup"><span data-stu-id="a2642-132">For a C++ example, see the [IWbemClassObject::NextMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-nextmethod) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a2642-133">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a2642-133">Requirements</span></span>  
 <span data-ttu-id="a2642-134">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2642-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2642-135">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="a2642-135">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="a2642-136">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="a2642-136">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2642-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2642-137">See also</span></span>

- [<span data-ttu-id="a2642-138">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="a2642-138">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
