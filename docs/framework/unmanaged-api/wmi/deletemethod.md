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
ms.openlocfilehash: db360584dacf250be2f35e5e6666f8332b39a8dd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120648"
---
# <a name="deletemethod-function"></a><span data-ttu-id="82c02-103">DeleteMethod, fonction</span><span class="sxs-lookup"><span data-stu-id="82c02-103">DeleteMethod function</span></span>
<span data-ttu-id="82c02-104">Supprime la méthode spécifiée d’une définition de classe CIM.</span><span class="sxs-lookup"><span data-stu-id="82c02-104">Deletes the specified method from a CIM class definition.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="82c02-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82c02-105">Syntax</span></span>  
  
```cpp  
HRESULT Delete (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszName 
); 
```  

## <a name="parameters"></a><span data-ttu-id="82c02-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82c02-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="82c02-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="82c02-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="82c02-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="82c02-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszName`  
<span data-ttu-id="82c02-109">dans Nom de la méthode à supprimer de la table de classes.</span><span class="sxs-lookup"><span data-stu-id="82c02-109">[in] The name of the method to remove from the class table.</span></span> <span data-ttu-id="82c02-110">`wszName` doit être un pointeur désignant un `LPCWSTR`valide.</span><span class="sxs-lookup"><span data-stu-id="82c02-110">`wszName` must be a pointer to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="82c02-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="82c02-111">Return value</span></span>

<span data-ttu-id="82c02-112">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="82c02-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="82c02-113">Constante</span><span class="sxs-lookup"><span data-stu-id="82c02-113">Constant</span></span>  |<span data-ttu-id="82c02-114">valeur</span><span class="sxs-lookup"><span data-stu-id="82c02-114">Value</span></span>  |<span data-ttu-id="82c02-115">Description</span><span class="sxs-lookup"><span data-stu-id="82c02-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="82c02-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="82c02-116">0x80041002</span></span> | <span data-ttu-id="82c02-117">La méthode spécifiée n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="82c02-117">The specified method does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="82c02-118">0x80041006</span><span class="sxs-lookup"><span data-stu-id="82c02-118">0x80041006</span></span> | <span data-ttu-id="82c02-119">La mémoire est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="82c02-119">There is not enough memory to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="82c02-120">0</span><span class="sxs-lookup"><span data-stu-id="82c02-120">0</span></span> | <span data-ttu-id="82c02-121">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="82c02-121">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="82c02-122">Notes</span><span class="sxs-lookup"><span data-stu-id="82c02-122">Remarks</span></span>

<span data-ttu-id="82c02-123">Cette fonction encapsule un appel à la méthode [IWbemClassObject ::D eletemethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) .</span><span class="sxs-lookup"><span data-stu-id="82c02-123">This function wraps a call to the [IWbemClassObject::DeleteMethod](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-deletemethod) method.</span></span>

<span data-ttu-id="82c02-124">La suppression de méthode n’est pas prise en charge pour les pointeurs [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) qui pointent vers des instances CIM.</span><span class="sxs-lookup"><span data-stu-id="82c02-124">Method deletion is not supported for [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) pointers that point to CIM instances.</span></span>

## <a name="requirements"></a><span data-ttu-id="82c02-125">spécifications</span><span class="sxs-lookup"><span data-stu-id="82c02-125">Requirements</span></span>  
 <span data-ttu-id="82c02-126">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82c02-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82c02-127">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="82c02-127">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="82c02-128">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="82c02-128">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82c02-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82c02-129">See also</span></span>

- [<span data-ttu-id="82c02-130">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="82c02-130">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
