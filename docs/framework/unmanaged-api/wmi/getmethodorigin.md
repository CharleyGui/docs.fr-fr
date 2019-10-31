---
title: Fonction GetMethodOrigin (référence des API non managées)
description: La fonction GetMethodOrigin détermine la classe dans laquelle une méthode est déclarée.
ms.date: 11/06/2017
api_name:
- GetMethodOrigin
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetMethodOrigin
helpviewer_keywords:
- GetMethodOrigin function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 1f669d5721a7bd9434f0ce4b1e2290c0633e1b46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73102533"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="98a4e-103">GetMethodOrigin, fonction</span><span class="sxs-lookup"><span data-stu-id="98a4e-103">GetMethodOrigin function</span></span>
<span data-ttu-id="98a4e-104">Détermine la classe dans laquelle une méthode est déclarée.</span><span class="sxs-lookup"><span data-stu-id="98a4e-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="98a4e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98a4e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
); 
```  

## <a name="parameters"></a><span data-ttu-id="98a4e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="98a4e-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="98a4e-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="98a4e-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="98a4e-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="98a4e-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="98a4e-109">dans Nom de la méthode pour l’objet dont la classe propriétaire est demandée.</span><span class="sxs-lookup"><span data-stu-id="98a4e-109">[in] The name of the method for the object whose owning class is being requested.</span></span> 

`pstrClassName`  
<span data-ttu-id="98a4e-110">à Reçoit le nom de la classe qui possède la méthode.</span><span class="sxs-lookup"><span data-stu-id="98a4e-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="98a4e-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="98a4e-111">Return value</span></span>

<span data-ttu-id="98a4e-112">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="98a4e-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="98a4e-113">Constante</span><span class="sxs-lookup"><span data-stu-id="98a4e-113">Constant</span></span>  |<span data-ttu-id="98a4e-114">valeur</span><span class="sxs-lookup"><span data-stu-id="98a4e-114">Value</span></span>  |<span data-ttu-id="98a4e-115">Description</span><span class="sxs-lookup"><span data-stu-id="98a4e-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="98a4e-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="98a4e-116">0x80041002</span></span> | <span data-ttu-id="98a4e-117">La méthode spécifiée est introuvable.</span><span class="sxs-lookup"><span data-stu-id="98a4e-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="98a4e-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="98a4e-118">0x80041008</span></span> | <span data-ttu-id="98a4e-119">Un ou plusieurs paramètres ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="98a4e-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="98a4e-120">0</span><span class="sxs-lookup"><span data-stu-id="98a4e-120">0</span></span> | <span data-ttu-id="98a4e-121">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="98a4e-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="98a4e-122">Notes</span><span class="sxs-lookup"><span data-stu-id="98a4e-122">Remarks</span></span>

<span data-ttu-id="98a4e-123">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) .</span><span class="sxs-lookup"><span data-stu-id="98a4e-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="98a4e-124">Étant donné qu’une classe peut hériter de méthodes d’une ou plusieurs classes de base, les développeurs veulent souvent déterminer la classe dans laquelle une méthode donnée est définie.</span><span class="sxs-lookup"><span data-stu-id="98a4e-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="98a4e-125">Le paramètre `pstrClassName` ne doit pas pointer vers un `BSTR` valide avant que la fonction soit appelée, car il s’agit d’un paramètre `out` ; ce pointeur n’est pas libéré après le retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="98a4e-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="98a4e-126">spécifications</span><span class="sxs-lookup"><span data-stu-id="98a4e-126">Requirements</span></span>  
<span data-ttu-id="98a4e-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98a4e-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a4e-128">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="98a4e-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="98a4e-129">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="98a4e-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98a4e-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98a4e-130">See also</span></span>

- [<span data-ttu-id="98a4e-131">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="98a4e-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
