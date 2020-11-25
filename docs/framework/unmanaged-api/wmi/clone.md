---
title: Fonction clone (référence des API non managées)
description: La fonction clone retourne un nouvel objet qui est un clone complet de l’objet actuel.
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
ms.openlocfilehash: aecbf750b42626629dcb5aef369978a2e2bd002a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708112"
---
# <a name="clone-function"></a><span data-ttu-id="625ad-103">Clone, fonction</span><span class="sxs-lookup"><span data-stu-id="625ad-103">Clone function</span></span>

<span data-ttu-id="625ad-104">Retourne un nouvel objet qui est un clone complet de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="625ad-104">Returns a new object that is a complete clone of the current object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="625ad-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="625ad-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [out] IWbemClassObject**  ppCopy
);
```  

## <a name="parameters"></a><span data-ttu-id="625ad-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="625ad-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="625ad-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="625ad-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="625ad-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="625ad-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`ppCopy`  
<span data-ttu-id="625ad-109">à Nouvel objet qui est un seul complet de `ptr` .</span><span class="sxs-lookup"><span data-stu-id="625ad-109">[out] A new object that is a complete lone of `ptr`.</span></span> <span data-ttu-id="625ad-110">Cet argument ne peut pas être `null` s’il reçoit la copie de l’objet en cours.</span><span class="sxs-lookup"><span data-stu-id="625ad-110">This argument cannot be `null` if it receives the copy of the current object.</span></span>

## <a name="return-value"></a><span data-ttu-id="625ad-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="625ad-111">Return value</span></span>

<span data-ttu-id="625ad-112">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="625ad-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="625ad-113">Constante</span><span class="sxs-lookup"><span data-stu-id="625ad-113">Constant</span></span>  |<span data-ttu-id="625ad-114">Value</span><span class="sxs-lookup"><span data-stu-id="625ad-114">Value</span></span>  |<span data-ttu-id="625ad-115">Description</span><span class="sxs-lookup"><span data-stu-id="625ad-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="625ad-116">0x80041001</span><span class="sxs-lookup"><span data-stu-id="625ad-116">0x80041001</span></span> | <span data-ttu-id="625ad-117">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="625ad-117">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="625ad-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="625ad-118">0x80041008</span></span> | <span data-ttu-id="625ad-119">`null` a été spécifié en tant que paramètre et n’est pas conforme dans cette utilisation.</span><span class="sxs-lookup"><span data-stu-id="625ad-119">`null` was specified as a parameter, and it is not legal in this usage.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="625ad-120">0x80041006</span><span class="sxs-lookup"><span data-stu-id="625ad-120">0x80041006</span></span> | <span data-ttu-id="625ad-121">Mémoire disponible insuffisante pour cloner l’objet.</span><span class="sxs-lookup"><span data-stu-id="625ad-121">Not enough memory is available to clone the object.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="625ad-122">0</span><span class="sxs-lookup"><span data-stu-id="625ad-122">0</span></span> | <span data-ttu-id="625ad-123">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="625ad-123">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="625ad-124">Remarques</span><span class="sxs-lookup"><span data-stu-id="625ad-124">Remarks</span></span>

<span data-ttu-id="625ad-125">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="625ad-125">This function wraps a call to the [IWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="625ad-126">L’objet cloné est un objet COM qui a un nombre de références de 1.</span><span class="sxs-lookup"><span data-stu-id="625ad-126">The cloned object is a COM object that has a reference count of 1.</span></span>

## <a name="requirements"></a><span data-ttu-id="625ad-127">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="625ad-127">Requirements</span></span>  

 <span data-ttu-id="625ad-128">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="625ad-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="625ad-129">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="625ad-129">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="625ad-130">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="625ad-130">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="625ad-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="625ad-131">See also</span></span>

- [<span data-ttu-id="625ad-132">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="625ad-132">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
