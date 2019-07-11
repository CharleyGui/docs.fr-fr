---
title: DeleteMethod, fonction (référence des API non managées)
description: La fonction DeleteMethod supprime la méthode spécifiée à partir d’une définition de classe CIM.
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 291d5d0461da8d130d41f9a0eca67ea3be42b4bc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746814"
---
# <a name="deletemethod-function"></a><span data-ttu-id="c090a-103">DeleteMethod, fonction</span><span class="sxs-lookup"><span data-stu-id="c090a-103">DeleteMethod function</span></span>
<span data-ttu-id="c090a-104">Supprime la méthode spécifiée à partir d’une définition de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="c090a-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="c090a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c090a-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="c090a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c090a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="c090a-107">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="c090a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="c090a-108">[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="c090a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="c090a-109">[in] Le nom de la méthode à supprimer de la table de la classe.</span><span class="sxs-lookup"><span data-stu-id="c090a-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="c090a-110">`wszName` doit être un pointeur désignant une valide `LPCWSTR`.</span><span class="sxs-lookup"><span data-stu-id="c090a-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="c090a-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c090a-111">Return value</span></span>

<span data-ttu-id="c090a-112">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="c090a-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="c090a-113">Constante</span><span class="sxs-lookup"><span data-stu-id="c090a-113">Constant</span></span>  |<span data-ttu-id="c090a-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="c090a-114">Value</span></span>  |<span data-ttu-id="c090a-115">Description</span><span class="sxs-lookup"><span data-stu-id="c090a-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="c090a-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="c090a-116">0x80041002</span></span> | <span data-ttu-id="c090a-117">La méthode spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="c090a-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="c090a-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="c090a-118">0x80041006</span></span> | <span data-ttu-id="c090a-119">Il n’est pas suffisamment de mémoire pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="c090a-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="c090a-120">0</span><span class="sxs-lookup"><span data-stu-id="c090a-120">0</span></span> | <span data-ttu-id="c090a-121">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="c090a-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="c090a-122">Notes</span><span class="sxs-lookup"><span data-stu-id="c090a-122">Remarks</span></span>

<span data-ttu-id="c090a-123">Cette fonction encapsule un appel à la [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) (méthode).</span><span class="sxs-lookup"><span data-stu-id="c090a-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="c090a-124">Suppression de la méthode n’est pas prise en charge pour [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointeurs qui pointent vers des instances CIM.</span><span class="sxs-lookup"><span data-stu-id="c090a-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="c090a-125">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c090a-125">Requirements</span></span>  
 <span data-ttu-id="c090a-126">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c090a-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c090a-127">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="c090a-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="c090a-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c090a-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c090a-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c090a-129">See also</span></span>

- [<span data-ttu-id="c090a-130">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="c090a-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
