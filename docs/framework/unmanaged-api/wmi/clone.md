---
title: Fonction clone (référence API non gestion)
description: La fonction Clone renvoie un nouvel objet qui est un clone complet de l’actuel.
ms.date: 11/06/2017
api_name:
- Clone
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- Clone
helpviewer_keywords:
- Clone function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: cb4951a1f289417482bfa1287028cc66349a5938
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176849"
---
# <a name="clone-function"></a><span data-ttu-id="f12f6-103">Clone, fonction</span><span class="sxs-lookup"><span data-stu-id="f12f6-103">Clone function</span></span>
<span data-ttu-id="f12f6-104">Retourne un nouvel objet qui est un clone complet de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="f12f6-104">Returns a new object that is a complete clone of the current object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f12f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f12f6-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [out] IWbemClassObject**  ppCopy
);
```  

## <a name="parameters"></a><span data-ttu-id="f12f6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f12f6-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="f12f6-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="f12f6-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="f12f6-108">[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="f12f6-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="f12f6-109">[out] Un nouvel objet qui est `ptr`un solitaire complet de .</span><span class="sxs-lookup"><span data-stu-id="f12f6-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="f12f6-110">Cet argument `null` ne peut pas être si elle reçoit la copie de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="f12f6-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="f12f6-111">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="f12f6-111">Return value</span></span>

<span data-ttu-id="f12f6-112">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="f12f6-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f12f6-113">Constant</span><span class="sxs-lookup"><span data-stu-id="f12f6-113">Constant</span></span>  |<span data-ttu-id="f12f6-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="f12f6-114">Value</span></span>  |<span data-ttu-id="f12f6-115">Description</span><span class="sxs-lookup"><span data-stu-id="f12f6-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="f12f6-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f12f6-116">0x80041001</span></span> | <span data-ttu-id="f12f6-117">Il y a eu un échec général.</span><span class="sxs-lookup"><span data-stu-id="f12f6-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f12f6-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f12f6-118">0x80041008</span></span> | <span data-ttu-id="f12f6-119">`null`a été spécifié comme un paramètre, et il n’est pas légal dans cette utilisation.</span><span class="sxs-lookup"><span data-stu-id="f12f6-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f12f6-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f12f6-120">0x80041006</span></span> | <span data-ttu-id="f12f6-121">Pas assez de mémoire est disponible pour cloner l’objet.</span><span class="sxs-lookup"><span data-stu-id="f12f6-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f12f6-122">0</span><span class="sxs-lookup"><span data-stu-id="f12f6-122">0</span></span> | <span data-ttu-id="f12f6-123">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="f12f6-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="f12f6-124">Notes </span><span class="sxs-lookup"><span data-stu-id="f12f6-124">Remarks</span></span>

<span data-ttu-id="f12f6-125">Cette fonction enveloppe un appel à [l’IWbemClassObject::Méthode Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone)</span><span class="sxs-lookup"><span data-stu-id="f12f6-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="f12f6-126">L’objet cloné est un objet COM qui a un nombre de références de 1.</span><span class="sxs-lookup"><span data-stu-id="f12f6-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="f12f6-127">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f12f6-127">Requirements</span></span>  
 <span data-ttu-id="f12f6-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f12f6-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f12f6-129">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f12f6-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f12f6-130">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f12f6-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12f6-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f12f6-131">See also</span></span>

- [<span data-ttu-id="f12f6-132">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="f12f6-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
