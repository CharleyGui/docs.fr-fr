---
title: Fonction InheritsFrom (référence des API non managées)
description: La fonction InheritsFrom détermine si une classe ou une instance dérive d’une classe parente particulière.
ms.date: 11/06/2017
api_name:
- InheritsFrom
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- InheritsFrom
helpviewer_keywords:
- InheritsFrom function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 6bda63377251e3a208dfb1620896535ccdf8ccd8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127431"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="ba13a-103">InheritsFrom fonction)</span><span class="sxs-lookup"><span data-stu-id="ba13a-103">InheritsFrom function</span></span>
<span data-ttu-id="ba13a-104">Détermine si l’instance ou la classe active dérive d’une classe parente spécifié.</span><span class="sxs-lookup"><span data-stu-id="ba13a-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a><span data-ttu-id="ba13a-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba13a-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc, 
   [in] IWbemClassObject* ptr, 
   [in] LPCWSTR           wszAncestor 
); 
```  

## <a name="parameters"></a><span data-ttu-id="ba13a-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ba13a-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="ba13a-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="ba13a-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="ba13a-108">dans Pointeur vers une instance [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) .</span><span class="sxs-lookup"><span data-stu-id="ba13a-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="ba13a-109">dans Nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="ba13a-109">[in] The name of the class.</span></span> <span data-ttu-id="ba13a-110">`wszAncestor` doit pointer vers un `LPCWSTR`valide.</span><span class="sxs-lookup"><span data-stu-id="ba13a-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="ba13a-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ba13a-111">Return value</span></span>

<span data-ttu-id="ba13a-112">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="ba13a-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ba13a-113">Constante</span><span class="sxs-lookup"><span data-stu-id="ba13a-113">Constant</span></span>  |<span data-ttu-id="ba13a-114">valeur</span><span class="sxs-lookup"><span data-stu-id="ba13a-114">Value</span></span>  |<span data-ttu-id="ba13a-115">Description</span><span class="sxs-lookup"><span data-stu-id="ba13a-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="ba13a-116">0</span><span class="sxs-lookup"><span data-stu-id="ba13a-116">0</span></span> | <span data-ttu-id="ba13a-117">L’objet actuel hérite de `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="ba13a-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="ba13a-118">1</span><span class="sxs-lookup"><span data-stu-id="ba13a-118">1</span></span> | <span data-ttu-id="ba13a-119">L’objet actuel n’hérite pas de `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="ba13a-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ba13a-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ba13a-120">0x80041008</span></span> | <span data-ttu-id="ba13a-121">`wszAncestor` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="ba13a-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="ba13a-122">Notes</span><span class="sxs-lookup"><span data-stu-id="ba13a-122">Remarks</span></span>

<span data-ttu-id="ba13a-123">Cette fonction encapsule un appel à la méthode [IWbemClassObject :: InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) .</span><span class="sxs-lookup"><span data-stu-id="ba13a-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ba13a-124">spécifications</span><span class="sxs-lookup"><span data-stu-id="ba13a-124">Requirements</span></span>  
 <span data-ttu-id="ba13a-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba13a-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba13a-126">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="ba13a-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="ba13a-127">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ba13a-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba13a-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ba13a-128">See also</span></span>

- [<span data-ttu-id="ba13a-129">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="ba13a-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
