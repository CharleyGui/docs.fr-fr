---
title: Fonction GetMethodOrigin (référence API non managérisée)
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
ms.openlocfilehash: 5b4609b6649be875aea7dfcf52ba36b1e98ab7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176797"
---
# <a name="getmethodorigin-function"></a><span data-ttu-id="48c59-103">GetMethodOrigin, fonction</span><span class="sxs-lookup"><span data-stu-id="48c59-103">GetMethodOrigin function</span></span>
<span data-ttu-id="48c59-104">Détermine la classe dans laquelle une méthode est déclarée.</span><span class="sxs-lookup"><span data-stu-id="48c59-104">Determines the class in which a method is declared.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="48c59-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48c59-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodOrigin (
   [in] int                 vFunc,
   [in] IWbemClassObject*   ptr,
   [in] LPCWSTR             wszMethodName,
   [out] BSTR*              pstrClassName
);
```  

## <a name="parameters"></a><span data-ttu-id="48c59-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="48c59-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="48c59-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="48c59-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="48c59-108">[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="48c59-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszMethodName`  
<span data-ttu-id="48c59-109">[dans] Le nom de la méthode de l’objet dont la classe de possession est demandée.</span><span class="sxs-lookup"><span data-stu-id="48c59-109">[in] The name of the method for the object whose owning class is being requested.</span></span>

`pstrClassName`  
<span data-ttu-id="48c59-110">[out] Reçoit le nom de la classe qui possède la méthode.</span><span class="sxs-lookup"><span data-stu-id="48c59-110">[out] Receives the name of the class that owns the method.</span></span>

## <a name="return-value"></a><span data-ttu-id="48c59-111">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="48c59-111">Return value</span></span>

<span data-ttu-id="48c59-112">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="48c59-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="48c59-113">Constant</span><span class="sxs-lookup"><span data-stu-id="48c59-113">Constant</span></span>  |<span data-ttu-id="48c59-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="48c59-114">Value</span></span>  |<span data-ttu-id="48c59-115">Description</span><span class="sxs-lookup"><span data-stu-id="48c59-115">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="48c59-116">0x80041002</span><span class="sxs-lookup"><span data-stu-id="48c59-116">0x80041002</span></span> | <span data-ttu-id="48c59-117">La méthode spécifiée n’a pas été trouvée.</span><span class="sxs-lookup"><span data-stu-id="48c59-117">The specified method was not found.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="48c59-118">0x80041008</span><span class="sxs-lookup"><span data-stu-id="48c59-118">0x80041008</span></span> | <span data-ttu-id="48c59-119">Un ou plusieurs paramètres ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="48c59-119">One or more parameters are not valid.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="48c59-120">0</span><span class="sxs-lookup"><span data-stu-id="48c59-120">0</span></span> | <span data-ttu-id="48c59-121">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="48c59-121">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="48c59-122">Notes </span><span class="sxs-lookup"><span data-stu-id="48c59-122">Remarks</span></span>

<span data-ttu-id="48c59-123">Cette fonction enveloppe un appel à [l’IWbemClassObject:GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) méthode.</span><span class="sxs-lookup"><span data-stu-id="48c59-123">This function wraps a call to the [IWbemClassObject::GetMethodOrigin](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getmethod) method.</span></span>

<span data-ttu-id="48c59-124">Parce qu’une classe peut hériter de méthodes d’une ou plusieurs classes de base, les développeurs veulent souvent déterminer la classe dans laquelle une méthode donnée est définie.</span><span class="sxs-lookup"><span data-stu-id="48c59-124">Because a class can inherit methods from one or more base classes, developers often want to determine the class in which a given method is defined.</span></span>

<span data-ttu-id="48c59-125">Le `pstrClassName` paramètre ne doit `BSTR` pas indiquer un valide `out` avant que la fonction soit appelée parce qu’il s’agit d’un paramètre; ce pointeur n’est pas deallocated après le retour de la fonction.</span><span class="sxs-lookup"><span data-stu-id="48c59-125">The `pstrClassName` parameter must not point to a valid `BSTR` before the function is called because this is an `out` parameter; this pointer is not deallocated after the function returns.</span></span>

## <a name="requirements"></a><span data-ttu-id="48c59-126">Spécifications</span><span class="sxs-lookup"><span data-stu-id="48c59-126">Requirements</span></span>  
<span data-ttu-id="48c59-127">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48c59-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48c59-128">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="48c59-128">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="48c59-129">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="48c59-129">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48c59-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48c59-130">See also</span></span>

- [<span data-ttu-id="48c59-131">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="48c59-131">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
