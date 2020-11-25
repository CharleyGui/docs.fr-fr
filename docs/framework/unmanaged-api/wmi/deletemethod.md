---
title: Fonction DeleteMethod (référence des API non managées)
description: La fonction DeleteMethod supprime la méthode spécifiée d’une définition de classe CIM.
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
ms.openlocfilehash: 8ca58ed3510360b20577890055e4284869d1bf94
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708099"
---
# <a name="deletemethod-function"></a><span data-ttu-id="90e7d-103">DeleteMethod, fonction</span><span class="sxs-lookup"><span data-stu-id="90e7d-103">DeleteMethod function</span></span>

<span data-ttu-id="90e7d-104">Supprime la méthode spécifiée d’une définition de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="90e7d-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="90e7d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="90e7d-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszName
);
```  

## <a name="parameters"></a><span data-ttu-id="90e7d-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="90e7d-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="90e7d-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="90e7d-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="90e7d-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="90e7d-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="90e7d-109">dans Nom de la méthode à supprimer de la table de classes.</span><span class="sxs-lookup"><span data-stu-id="90e7d-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="90e7d-110">`wszName` doit être un pointeur vers un valide `LPCWSTR` .</span><span class="sxs-lookup"><span data-stu-id="90e7d-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="90e7d-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="90e7d-111">Return value</span></span>

<span data-ttu-id="90e7d-112">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="90e7d-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="90e7d-113">Constante</span><span class="sxs-lookup"><span data-stu-id="90e7d-113">Constant</span></span>  |<span data-ttu-id="90e7d-114">Value</span><span class="sxs-lookup"><span data-stu-id="90e7d-114">Value</span></span>  |<span data-ttu-id="90e7d-115">Description</span><span class="sxs-lookup"><span data-stu-id="90e7d-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="90e7d-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="90e7d-116">0x80041002</span></span> | <span data-ttu-id="90e7d-117">La méthode spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="90e7d-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="90e7d-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="90e7d-118">0x80041006</span></span> | <span data-ttu-id="90e7d-119">La mémoire disponible est insuffisante pour terminer cette opération.</span><span class="sxs-lookup"><span data-stu-id="90e7d-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="90e7d-120">0</span><span class="sxs-lookup"><span data-stu-id="90e7d-120">0</span></span> | <span data-ttu-id="90e7d-121">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="90e7d-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="90e7d-122">Remarques</span><span class="sxs-lookup"><span data-stu-id="90e7d-122">Remarks</span></span>

<span data-ttu-id="90e7d-123">Cette fonction encapsule un appel à la méthode [IWbemClassObject ::D eletemethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) .</span><span class="sxs-lookup"><span data-stu-id="90e7d-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="90e7d-124">La suppression de méthode n’est pas prise en charge pour les pointeurs [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui pointent vers des instances CIM.</span><span class="sxs-lookup"><span data-stu-id="90e7d-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="90e7d-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="90e7d-125">Requirements</span></span>  

 <span data-ttu-id="90e7d-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90e7d-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90e7d-127">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="90e7d-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="90e7d-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="90e7d-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e7d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90e7d-129">See also</span></span>

- [<span data-ttu-id="90e7d-130">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="90e7d-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
