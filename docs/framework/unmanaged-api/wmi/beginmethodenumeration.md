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
ms.openlocfilehash: a27787052757098d4edb2d8516e22d8a03b7009a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138792"
---
# <a name="beginenumeration-function"></a><span data-ttu-id="c3475-103">BeginEnumeration, fonction</span><span class="sxs-lookup"><span data-stu-id="c3475-103">BeginEnumeration function</span></span>
<span data-ttu-id="c3475-104">Commence une énumération des méthodes disponibles pour l’objet.</span><span class="sxs-lookup"><span data-stu-id="c3475-104">Begins an enumeration of the methods available for the object.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="c3475-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3475-105">Syntax</span></span>  
  
```cpp 
HRESULT BeginMethodEnumeration (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LONG              lEnumFlags
); 
```  

## <a name="parameters"></a><span data-ttu-id="c3475-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3475-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c3475-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="c3475-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="c3475-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="c3475-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lEnumFlags`  
<span data-ttu-id="c3475-109">dans Zéro (0) pour toutes les méthodes, ou un indicateur qui spécifie la portée de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="c3475-109">[in] Zero (0) for all methods, or a flag that specifies the scope of the enumeration.</span></span> <span data-ttu-id="c3475-110">Les indicateurs suivants sont définis dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="c3475-110">The following flags are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

<span data-ttu-id="c3475-111">Constante</span><span class="sxs-lookup"><span data-stu-id="c3475-111">Constant</span></span>  |<span data-ttu-id="c3475-112">valeur</span><span class="sxs-lookup"><span data-stu-id="c3475-112">Value</span></span>  |<span data-ttu-id="c3475-113">Description</span><span class="sxs-lookup"><span data-stu-id="c3475-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | <span data-ttu-id="c3475-114">0x10</span><span class="sxs-lookup"><span data-stu-id="c3475-114">0x10</span></span> | <span data-ttu-id="c3475-115">Limitez l’énumération aux méthodes définies dans la classe elle-même.</span><span class="sxs-lookup"><span data-stu-id="c3475-115">Limit the enumeration to methods that are defined in the class itself.</span></span> |
| `WBEM_FLAG_PROPAGATED_ONLY` |  <span data-ttu-id="c3475-116">0x20</span><span class="sxs-lookup"><span data-stu-id="c3475-116">0x20</span></span> | <span data-ttu-id="c3475-117">Limitez l’énumération aux propriétés héritées des classes de base.</span><span class="sxs-lookup"><span data-stu-id="c3475-117">Limit the enumeration to properties that are inherited from base classes.</span></span> |

## <a name="return-value"></a><span data-ttu-id="c3475-118">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c3475-118">Return value</span></span>

<span data-ttu-id="c3475-119">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="c3475-119">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c3475-120">Constante</span><span class="sxs-lookup"><span data-stu-id="c3475-120">Constant</span></span>  |<span data-ttu-id="c3475-121">valeur</span><span class="sxs-lookup"><span data-stu-id="c3475-121">Value</span></span>  |<span data-ttu-id="c3475-122">Description</span><span class="sxs-lookup"><span data-stu-id="c3475-122">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="c3475-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="c3475-123">0x80041008</span></span> | <span data-ttu-id="c3475-124">`lEnnumFlags` est différent de zéro et n’est pas l’un des indicateurs spécifiés.</span><span class="sxs-lookup"><span data-stu-id="c3475-124">`lEnnumFlags` is non-zero and is not one of the specified flags.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="c3475-125">0</span><span class="sxs-lookup"><span data-stu-id="c3475-125">0</span></span> | <span data-ttu-id="c3475-126">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="c3475-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="c3475-127">Notes</span><span class="sxs-lookup"><span data-stu-id="c3475-127">Remarks</span></span>

<span data-ttu-id="c3475-128">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) .</span><span class="sxs-lookup"><span data-stu-id="c3475-128">This function wraps a call to the [IWbemClassObject::BeginMethodEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-beginmethodenumeration) method.</span></span>

<span data-ttu-id="c3475-129">Cet appel de méthode est pris en charge uniquement si l’objet actuel est une définition de classe.</span><span class="sxs-lookup"><span data-stu-id="c3475-129">This method call is only supported if the current object is a class definition.</span></span> <span data-ttu-id="c3475-130">La manipulation de méthode n’est pas disponible à partir de pointeurs [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui pointent vers des instances.</span><span class="sxs-lookup"><span data-stu-id="c3475-130">Method manipulation is not available from [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to instances.</span></span> <span data-ttu-id="c3475-131">L’ordre dans lequel les méthodes sont énumérées est toujours indifférent pour une instance donnée de [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="c3475-131">The order in which methods are enumerated is guaranteed to be invariant for a given instance of [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject).</span></span>

## <a name="requirements"></a><span data-ttu-id="c3475-132">spécifications</span><span class="sxs-lookup"><span data-stu-id="c3475-132">Requirements</span></span>  
 <span data-ttu-id="c3475-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3475-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3475-134">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="c3475-134">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c3475-135">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c3475-135">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3475-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3475-136">See also</span></span>

- [<span data-ttu-id="c3475-137">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="c3475-137">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
