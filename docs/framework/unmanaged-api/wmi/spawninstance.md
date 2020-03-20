---
title: Fonction SpawnInstance (Référence API non gestion)
description: La fonction SpawnInstance crée une nouvelle instance d’une classe.
ms.date: 11/06/2017
api_name:
- SpawnInstance
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnInstance
helpviewer_keywords:
- SpawnInstance function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: a15eb8123c1ee807444bdb4c6fe71cdccc08f434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176719"
---
# <a name="spawninstance-function"></a><span data-ttu-id="b565c-103">SpawnInstance, fonction</span><span class="sxs-lookup"><span data-stu-id="b565c-103">SpawnInstance function</span></span>
<span data-ttu-id="b565c-104">Crée une instance d’une classe.</span><span class="sxs-lookup"><span data-stu-id="b565c-104">Creates a new instance of a class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="b565c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b565c-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc,
   [in] IWbemClassObject*    ptr,
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance);
```  

## <a name="parameters"></a><span data-ttu-id="b565c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b565c-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="b565c-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="b565c-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="b565c-108">[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="b565c-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="b565c-109">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="b565c-109">[in] Reserved.</span></span> <span data-ttu-id="b565c-110">Ce paramètre doit être de 0.</span><span class="sxs-lookup"><span data-stu-id="b565c-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="b565c-111">[out] Reçoit le pointeur de la nouvelle instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="b565c-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="b565c-112">Si une erreur se produit, un `ppNewInstance` nouvel objet n’est pas retourné et n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="b565c-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="b565c-113">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="b565c-113">Return value</span></span>

<span data-ttu-id="b565c-114">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="b565c-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="b565c-115">Constant</span><span class="sxs-lookup"><span data-stu-id="b565c-115">Constant</span></span>  |<span data-ttu-id="b565c-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="b565c-116">Value</span></span>  |<span data-ttu-id="b565c-117">Description</span><span class="sxs-lookup"><span data-stu-id="b565c-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="b565c-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="b565c-118">0x80041020</span></span> | <span data-ttu-id="b565c-119">`ptr`n’est pas une définition de classe valide et ne peut pas engendrer de nouveaux cas.</span><span class="sxs-lookup"><span data-stu-id="b565c-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="b565c-120">Soit il est incomplet ou il n’a pas été enregistré auprès de Windows Management en appelant [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="b565c-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="b565c-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="b565c-121">0x80041006</span></span> | <span data-ttu-id="b565c-122">La mémoire n'est pas suffisante pour terminer cette opération.</span><span class="sxs-lookup"><span data-stu-id="b565c-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="b565c-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="b565c-123">0x80041008</span></span> | <span data-ttu-id="b565c-124">`ppNewClass` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="b565c-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="b565c-125">0</span><span class="sxs-lookup"><span data-stu-id="b565c-125">0</span></span> | <span data-ttu-id="b565c-126">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="b565c-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="b565c-127">Notes </span><span class="sxs-lookup"><span data-stu-id="b565c-127">Remarks</span></span>

<span data-ttu-id="b565c-128">Cette fonction enveloppe un appel à [l’IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) méthode.</span><span class="sxs-lookup"><span data-stu-id="b565c-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="b565c-129">`ptr`doit être une définition de classe obtenue auprès de Windows Management.</span><span class="sxs-lookup"><span data-stu-id="b565c-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="b565c-130">(Notez que le fait de frayer une instance à partir d’une instance est pris en charge, mais l’instance retournée est vide.) Vous utilisez ensuite cette définition de classe pour créer de nouvelles instances.</span><span class="sxs-lookup"><span data-stu-id="b565c-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="b565c-131">Un appel à la fonction [PutInstanceWmi](putinstancewmi.md) est nécessaire si vous avez l’intention d’écrire l’instance à Windows Management.</span><span class="sxs-lookup"><span data-stu-id="b565c-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="b565c-132">Le nouvel objet `ppNewClass` retourné devient automatiquement une sous-classe de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="b565c-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="b565c-133">Ce comportement ne peut pas être remplacé.</span><span class="sxs-lookup"><span data-stu-id="b565c-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="b565c-134">Il n’existe pas d’autre méthode par laquelle des sous-classes (classes dérivées) peuvent être créées.</span><span class="sxs-lookup"><span data-stu-id="b565c-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="b565c-135">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b565c-135">Requirements</span></span>  
 <span data-ttu-id="b565c-136">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b565c-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b565c-137">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="b565c-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="b565c-138">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b565c-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b565c-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b565c-139">See also</span></span>

- [<span data-ttu-id="b565c-140">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="b565c-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
