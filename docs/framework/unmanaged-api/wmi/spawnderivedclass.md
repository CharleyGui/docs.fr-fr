---
title: Fonction SpawnDerivedClass (Référence API non gestion)
description: La fonction SpawnDerivedClass crée un nouvel objet qui dérive d’un objet.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: e9784f8a024c788823dc702794b2b86eea1827bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174847"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="68b7c-103">SpawnDerivedClass, fonction</span><span class="sxs-lookup"><span data-stu-id="68b7c-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="68b7c-104">Crée un objet de classe dérivé à partir d’un objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="68b7c-104">Creates a newly derived class object from a specified object.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="68b7c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68b7c-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass);
```  

## <a name="parameters"></a><span data-ttu-id="68b7c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68b7c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="68b7c-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="68b7c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="68b7c-108">[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="68b7c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="68b7c-109">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="68b7c-109">[in] Reserved.</span></span> <span data-ttu-id="68b7c-110">Ce paramètre doit être de 0.</span><span class="sxs-lookup"><span data-stu-id="68b7c-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="68b7c-111">[out] Reçoit le pointeur de la nouvelle définition de classe objet.</span><span class="sxs-lookup"><span data-stu-id="68b7c-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="68b7c-112">Si une erreur se produit, un `ppNewClass` nouvel objet n’est pas retourné et n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="68b7c-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="68b7c-113">Sa valeur `null`ne peut pas être .</span><span class="sxs-lookup"><span data-stu-id="68b7c-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="68b7c-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="68b7c-114">Return value</span></span>

<span data-ttu-id="68b7c-115">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="68b7c-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="68b7c-116">Constant</span><span class="sxs-lookup"><span data-stu-id="68b7c-116">Constant</span></span>  |<span data-ttu-id="68b7c-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="68b7c-117">Value</span></span>  |<span data-ttu-id="68b7c-118">Description</span><span class="sxs-lookup"><span data-stu-id="68b7c-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="68b7c-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="68b7c-119">0x80041001</span></span> | <span data-ttu-id="68b7c-120">Il y a eu un échec général.</span><span class="sxs-lookup"><span data-stu-id="68b7c-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="68b7c-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="68b7c-121">0x80041016</span></span> | <span data-ttu-id="68b7c-122">Une opération invalide, comme le fait de frayer une classe à partir d’une instance, a été demandée.</span><span class="sxs-lookup"><span data-stu-id="68b7c-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="68b7c-123">La classe source n’a pas été entièrement définie ou enregistrée auprès de Windows Management, de sorte qu’une nouvelle classe dérivée n’est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="68b7c-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="68b7c-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="68b7c-124">0x80041006</span></span> | <span data-ttu-id="68b7c-125">La mémoire n'est pas suffisante pour terminer cette opération.</span><span class="sxs-lookup"><span data-stu-id="68b7c-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="68b7c-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="68b7c-126">0x80041008</span></span> | <span data-ttu-id="68b7c-127">`ppNewClass` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="68b7c-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="68b7c-128">0</span><span class="sxs-lookup"><span data-stu-id="68b7c-128">0</span></span> | <span data-ttu-id="68b7c-129">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="68b7c-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="68b7c-130">Notes </span><span class="sxs-lookup"><span data-stu-id="68b7c-130">Remarks</span></span>

<span data-ttu-id="68b7c-131">Cette fonction enveloppe un appel à [l’IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) méthode.</span><span class="sxs-lookup"><span data-stu-id="68b7c-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="68b7c-132">`ptr`doit être une définition de classe qui devient la classe parente de l’objet engendré.</span><span class="sxs-lookup"><span data-stu-id="68b7c-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="68b7c-133">L’objet retourné devient une sous-classe de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="68b7c-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="68b7c-134">Le nouvel objet `ppNewClass` retourné devient automatiquement une sous-classe de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="68b7c-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="68b7c-135">Ce comportement ne peut pas être remplacé.</span><span class="sxs-lookup"><span data-stu-id="68b7c-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="68b7c-136">Il n’existe pas d’autre méthode par laquelle des sous-classes (classes dérivées) peuvent être créées.</span><span class="sxs-lookup"><span data-stu-id="68b7c-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="68b7c-137">Spécifications</span><span class="sxs-lookup"><span data-stu-id="68b7c-137">Requirements</span></span>  
 <span data-ttu-id="68b7c-138">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68b7c-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68b7c-139">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="68b7c-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="68b7c-140">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="68b7c-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68b7c-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68b7c-141">See also</span></span>

- [<span data-ttu-id="68b7c-142">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="68b7c-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
