---
title: SpawnInstance (fonction) (référence des API non managées)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97a3ab62cda82526a7ad8b8e5d985d9fce7d6f07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783068"
---
# <a name="spawninstance-function"></a><span data-ttu-id="d52de-103">SpawnInstance (fonction)</span><span class="sxs-lookup"><span data-stu-id="d52de-103">SpawnInstance function</span></span>
<span data-ttu-id="d52de-104">Crée une instance d’une classe.</span><span class="sxs-lookup"><span data-stu-id="d52de-104">Creates a new instance of a class.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="d52de-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d52de-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnInstance (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewInstance); 
```  

## <a name="parameters"></a><span data-ttu-id="d52de-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d52de-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="d52de-107">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="d52de-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="d52de-108">[in] Un pointeur vers un [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span><span class="sxs-lookup"><span data-stu-id="d52de-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="d52de-109">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="d52de-109">[in] Reserved.</span></span> <span data-ttu-id="d52de-110">Ce paramètre doit être 0.</span><span class="sxs-lookup"><span data-stu-id="d52de-110">This parameter must be 0.</span></span>

`ppNewInstance`  
<span data-ttu-id="d52de-111">[out] Reçoit le pointeur vers la nouvelle instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="d52de-111">[out] Receives the pointer to the new instance of the class.</span></span> <span data-ttu-id="d52de-112">Si une erreur se produit, un nouvel objet n’est pas retournée, et `ppNewInstance` est gauche tels quels.</span><span class="sxs-lookup"><span data-stu-id="d52de-112">If an error occurs, a new object is not returned, and `ppNewInstance` is left unmodified.</span></span>

## <a name="return-value"></a><span data-ttu-id="d52de-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d52de-113">Return value</span></span>

<span data-ttu-id="d52de-114">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="d52de-114">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d52de-115">Constante</span><span class="sxs-lookup"><span data-stu-id="d52de-115">Constant</span></span>  |<span data-ttu-id="d52de-116">Valeur</span><span class="sxs-lookup"><span data-stu-id="d52de-116">Value</span></span>  |<span data-ttu-id="d52de-117">Description</span><span class="sxs-lookup"><span data-stu-id="d52de-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="d52de-118">0x80041020</span><span class="sxs-lookup"><span data-stu-id="d52de-118">0x80041020</span></span> | <span data-ttu-id="d52de-119">`ptr` n’est pas une définition de classe valide et ne peut pas générer de nouvelles instances.</span><span class="sxs-lookup"><span data-stu-id="d52de-119">`ptr` is not a valid class definition and cannot spawn new instances.</span></span> <span data-ttu-id="d52de-120">Soit il est incomplet, soit il n’a pas été inscrit avec la gestion de Windows en appelant [PutClassWmi](putclasswmi.md).</span><span class="sxs-lookup"><span data-stu-id="d52de-120">Either it is incomplete or it has not been registered with Windows Management by calling [PutClassWmi](putclasswmi.md).</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d52de-121">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d52de-121">0x80041006</span></span> | <span data-ttu-id="d52de-122">Mémoire est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="d52de-122">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d52de-123">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d52de-123">0x80041008</span></span> | <span data-ttu-id="d52de-124">`ppNewClass` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="d52de-124">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="d52de-125">0</span><span class="sxs-lookup"><span data-stu-id="d52de-125">0</span></span> | <span data-ttu-id="d52de-126">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="d52de-126">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="d52de-127">Notes</span><span class="sxs-lookup"><span data-stu-id="d52de-127">Remarks</span></span>

<span data-ttu-id="d52de-128">Cette fonction encapsule un appel à la [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) (méthode).</span><span class="sxs-lookup"><span data-stu-id="d52de-128">This function wraps a call to the [IWbemClassObject::SpawnInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-spawninstance) method.</span></span>

<span data-ttu-id="d52de-129">`ptr` doit être une définition de classe obtenue à partir de la gestion de Windows.</span><span class="sxs-lookup"><span data-stu-id="d52de-129">`ptr` must be a class definition obtained from Windows Management.</span></span> <span data-ttu-id="d52de-130">(Notez que lors de la génération une instance d’une instance est prise en charge, mais l’instance retournée est vide.) Vous utilisez ensuite cette définition de classe pour créer des instances.</span><span class="sxs-lookup"><span data-stu-id="d52de-130">(Note that spawning an instance from an instance is supported but the returned instance is empty.) You then use this class definition to create new instances.</span></span> <span data-ttu-id="d52de-131">Un appel à la [PutInstanceWmi](putinstancewmi.md) fonction est nécessaire si vous avez l’intention d’écrire l’instance à la gestion de Windows.</span><span class="sxs-lookup"><span data-stu-id="d52de-131">A call to the [PutInstanceWmi](putinstancewmi.md) function is required if you intend to write the instance to Windows Management.</span></span>

<span data-ttu-id="d52de-132">Le nouvel objet retourné dans `ppNewClass` devient automatiquement une sous-classe de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="d52de-132">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="d52de-133">Ce comportement ne peut pas être remplacé.</span><span class="sxs-lookup"><span data-stu-id="d52de-133">This behavior cannot be overridden.</span></span> <span data-ttu-id="d52de-134">Il n’existe aucune autre méthode par laquelle les sous-classes (classes dérivées) peuvent être créés.</span><span class="sxs-lookup"><span data-stu-id="d52de-134">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="d52de-135">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d52de-135">Requirements</span></span>  
 <span data-ttu-id="d52de-136">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d52de-136">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d52de-137">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d52de-137">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="d52de-138">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d52de-138">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d52de-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d52de-139">See also</span></span>

- [<span data-ttu-id="d52de-140">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="d52de-140">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
