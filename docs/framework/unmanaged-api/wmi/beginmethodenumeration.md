---
title: Fonction BeginMethodEnumeration (référence des API non managées)
description: La fonction BeginMethodEnumeration commence une énumération des méthodes de l’objet
ms.date: 11/06/2017
api_name:
- BeginMethodEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BeginMethodEnumeration
helpviewer_keywords:
- BeginMethodEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a72d61a572a0582ed8c03e56a8a9933c5f2775f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719760"
---
# <a name="beginmethodenumeration-function"></a><span data-ttu-id="9ab4d-103">BeginMethodEnumeration, fonction</span><span class="sxs-lookup"><span data-stu-id="9ab4d-103">BeginMethodEnumeration function</span></span>

<span data-ttu-id="9ab4d-104">Commence une énumération des méthodes disponibles pour l’objet.</span><span class="sxs-lookup"><span data-stu-id="9ab4d-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="9ab4d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ab4d-105">Syntax</span></span>  
  
```cpp
HRESULT BeginMethodEnumeration (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LONG              lEnumFlags
);
```  

## <a name="parameters"></a><span data-ttu-id="9ab4d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9ab4d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="9ab4d-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="9ab4d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="9ab4d-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="9ab4d-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="9ab4d-109">dans Zéro (0) pour toutes les méthodes, ou un indicateur qui spécifie la portée de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="9ab4d-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="9ab4d-110">Les indicateurs suivants sont définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="9ab4d-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="9ab4d-111">Constante</span><span class="sxs-lookup"><span data-stu-id="9ab4d-111">Constant</span></span>  |<span data-ttu-id="9ab4d-112">Value</span><span class="sxs-lookup"><span data-stu-id="9ab4d-112">Value</span></span>  |<span data-ttu-id="9ab4d-113">Description</span><span class="sxs-lookup"><span data-stu-id="9ab4d-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="9ab4d-114">0x10</span><span class="sxs-lookup"><span data-stu-id="9ab4d-114">0x10</span></span> | <span data-ttu-id="9ab4d-115">Limitez l’énumération aux méthodes définies dans la classe elle-même.</span><span class="sxs-lookup"><span data-stu-id="9ab4d-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="9ab4d-116">0x20</span><span class="sxs-lookup"><span data-stu-id="9ab4d-116">0x20</span></span> | <span data-ttu-id="9ab4d-117">Limitez l’énumération aux propriétés héritées des classes de base.</span><span class="sxs-lookup"><span data-stu-id="9ab4d-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="9ab4d-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9ab4d-118">Return value</span></span>

<span data-ttu-id="9ab4d-119">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="9ab4d-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9ab4d-120">Constante</span><span class="sxs-lookup"><span data-stu-id="9ab4d-120">Constant</span></span>  |<span data-ttu-id="9ab4d-121">Value</span><span class="sxs-lookup"><span data-stu-id="9ab4d-121">Value</span></span>  |<span data-ttu-id="9ab4d-122">Description</span><span class="sxs-lookup"><span data-stu-id="9ab4d-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9ab4d-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9ab4d-123">0x80041008</span></span> | <span data-ttu-id="9ab4d-124">`lEnnumFlags` est différent de zéro et n’est pas l’un des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="9ab4d-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="9ab4d-125">0</span><span class="sxs-lookup"><span data-stu-id="9ab4d-125">0</span></span> | <span data-ttu-id="9ab4d-126">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="9ab4d-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="9ab4d-127">Remarques</span><span class="sxs-lookup"><span data-stu-id="9ab4d-127">Remarks</span></span>

<span data-ttu-id="9ab4d-128">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) .</span><span class="sxs-lookup"><span data-stu-id="9ab4d-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="9ab4d-129">Cet appel de méthode est pris en charge uniquement si l’objet actuel est une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="9ab4d-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="9ab4d-130">La manipulation de méthode n’est pas disponible à partir de pointeurs [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui pointent vers des instances.</span><span class="sxs-lookup"><span data-stu-id="9ab4d-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="9ab4d-131">L’ordre dans lequel les méthodes sont énumérées est toujours indifférent pour une instance donnée de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="9ab4d-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="9ab4d-132">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9ab4d-132">Requirements</span></span>  

 <span data-ttu-id="9ab4d-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ab4d-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ab4d-134">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="9ab4d-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9ab4d-135">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9ab4d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab4d-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9ab4d-136">See also</span></span>

- [<span data-ttu-id="9ab4d-137">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="9ab4d-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
