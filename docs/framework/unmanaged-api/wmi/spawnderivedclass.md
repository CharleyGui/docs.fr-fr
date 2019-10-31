---
title: Fonction SpawnDerivedClass (référence des API non managées)
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
ms.openlocfilehash: f72e6b1c356077a94b141e40d6efe485e77e7a9e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120177"
---
# <a name="spawnderivedclass-function"></a><span data-ttu-id="ea6e2-103">SpawnDerivedClass fonction)</span><span class="sxs-lookup"><span data-stu-id="ea6e2-103">SpawnDerivedClass function</span></span>
<span data-ttu-id="ea6e2-104">Crée un objet de classe dérivé à partir d’un objet spécifié.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-104">Creates a newly derived class object from a specified object.</span></span>    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="ea6e2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea6e2-105">Syntax</span></span>  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a><span data-ttu-id="ea6e2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ea6e2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ea6e2-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ea6e2-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="ea6e2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`lFlags`  
<span data-ttu-id="ea6e2-109">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-109">[in] Reserved.</span></span> <span data-ttu-id="ea6e2-110">Ce paramètre doit avoir la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-110">This parameter must be 0.</span></span>

`ppNewClass`  
<span data-ttu-id="ea6e2-111">à Reçoit le pointeur vers le nouvel objet de définition de classe.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-111">[out] Receives the pointer to the new class definition object.</span></span> <span data-ttu-id="ea6e2-112">Si une erreur se produit, aucun nouvel objet n’est retourné et `ppNewClass` reste inchangé.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-112">If an error occurs, a new object is not returned, and `ppNewClass` is left unmodified.</span></span> <span data-ttu-id="ea6e2-113">Sa valeur ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-113">Its value cannot be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="ea6e2-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ea6e2-114">Return value</span></span>

<span data-ttu-id="ea6e2-115">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="ea6e2-115">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ea6e2-116">Constante</span><span class="sxs-lookup"><span data-stu-id="ea6e2-116">Constant</span></span>  |<span data-ttu-id="ea6e2-117">valeur</span><span class="sxs-lookup"><span data-stu-id="ea6e2-117">Value</span></span>  |<span data-ttu-id="ea6e2-118">Description</span><span class="sxs-lookup"><span data-stu-id="ea6e2-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="ea6e2-119">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ea6e2-119">0x80041001</span></span> | <span data-ttu-id="ea6e2-120">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-120">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_OPERATION` | <span data-ttu-id="ea6e2-121">0x80041016</span><span class="sxs-lookup"><span data-stu-id="ea6e2-121">0x80041016</span></span> | <span data-ttu-id="ea6e2-122">Une opération non valide, telle que la génération d’une classe à partir d’une instance, a été demandée.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-122">An invalid operation, such as spawning a class from an instance, was requested.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="ea6e2-123">La classe source n’a pas été complètement définie ou inscrite avec la gestion de Windows, de sorte qu’une nouvelle classe dérivée n’est pas autorisée.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-123">The source class was not completely defined or registered with Windows Management, so a new derived class is not permitted.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ea6e2-124">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ea6e2-124">0x80041006</span></span> | <span data-ttu-id="ea6e2-125">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-125">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ea6e2-126">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ea6e2-126">0x80041008</span></span> | <span data-ttu-id="ea6e2-127">`ppNewClass` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-127">`ppNewClass` is `null`.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="ea6e2-128">0</span><span class="sxs-lookup"><span data-stu-id="ea6e2-128">0</span></span> | <span data-ttu-id="ea6e2-129">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-129">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="ea6e2-130">Notes</span><span class="sxs-lookup"><span data-stu-id="ea6e2-130">Remarks</span></span>

<span data-ttu-id="ea6e2-131">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="ea6e2-131">This function wraps a call to the [IWbemClassObject::SpawnDerivedClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) method.</span></span>

<span data-ttu-id="ea6e2-132">`ptr` doit être une définition de classe qui devient la classe parente de l’objet généré.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-132">`ptr` must be a class definition that becomes the parent class of the spawned object.</span></span> <span data-ttu-id="ea6e2-133">L’objet retourné devient une sous-classe de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-133">The returned object becomes a subclass of the current object.</span></span>

<span data-ttu-id="ea6e2-134">Le nouvel objet retourné dans `ppNewClass` devient automatiquement une sous-classe de l’objet actuel.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-134">The new object returned in `ppNewClass` automatically becomes a subclass of the current object.</span></span> <span data-ttu-id="ea6e2-135">Ce comportement ne peut pas être substitué.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-135">This behavior cannot be overridden.</span></span> <span data-ttu-id="ea6e2-136">Il n’existe aucune autre méthode par laquelle les sous-classes (classes dérivées) peuvent être créées.</span><span class="sxs-lookup"><span data-stu-id="ea6e2-136">There is no other method by which subclasses (derived classes) can be created.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea6e2-137">spécifications</span><span class="sxs-lookup"><span data-stu-id="ea6e2-137">Requirements</span></span>  
 <span data-ttu-id="ea6e2-138">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea6e2-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea6e2-139">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="ea6e2-139">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ea6e2-140">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ea6e2-140">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea6e2-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea6e2-141">See also</span></span>

- [<span data-ttu-id="ea6e2-142">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="ea6e2-142">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
