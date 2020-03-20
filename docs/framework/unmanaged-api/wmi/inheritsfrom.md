---
title: Héritede fonction (référence API non mentée)
description: La fonction InheritsDe détermine si une classe ou une instance provient d’une classe parente particulière.
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
ms.openlocfilehash: c735c01c45beda8a1ba988a5c580e6b04ae46312
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174938"
---
# <a name="inheritsfrom-function"></a><span data-ttu-id="17fd2-103">InheritsFrom, fonction</span><span class="sxs-lookup"><span data-stu-id="17fd2-103">InheritsFrom function</span></span>
<span data-ttu-id="17fd2-104">Détermine si l’instance ou la classe active dérive d’une classe parente spécifié.</span><span class="sxs-lookup"><span data-stu-id="17fd2-104">Determines whether the current class or instance derives from a specified parent class.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="17fd2-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17fd2-105">Syntax</span></span>  
  
```cpp
HRESULT InheritsFrom (
   [in] int               vFunc,
   [in] IWbemClassObject* ptr,
   [in] LPCWSTR           wszAncestor
);
```  

## <a name="parameters"></a><span data-ttu-id="17fd2-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="17fd2-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="17fd2-107">[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="17fd2-107">[in] This parameter is unused.</span></span>

`ptr`  
<span data-ttu-id="17fd2-108">[dans] Un pointeur à une instance [IWbemClassObject.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)</span><span class="sxs-lookup"><span data-stu-id="17fd2-108">[in] A pointer to an [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) instance.</span></span>

`wszAncestor`  
<span data-ttu-id="17fd2-109">[dans] Le nom de la classe.</span><span class="sxs-lookup"><span data-stu-id="17fd2-109">[in] The name of the class.</span></span> <span data-ttu-id="17fd2-110">`wszAncestor`doit indiquer une `LPCWSTR`validité .</span><span class="sxs-lookup"><span data-stu-id="17fd2-110">`wszAncestor` must point to a valid `LPCWSTR`.</span></span>

## <a name="return-value"></a><span data-ttu-id="17fd2-111">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="17fd2-111">Return value</span></span>

<span data-ttu-id="17fd2-112">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="17fd2-112">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="17fd2-113">Constant</span><span class="sxs-lookup"><span data-stu-id="17fd2-113">Constant</span></span>  |<span data-ttu-id="17fd2-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="17fd2-114">Value</span></span>  |<span data-ttu-id="17fd2-115">Description</span><span class="sxs-lookup"><span data-stu-id="17fd2-115">Description</span></span>  |
|---------|---------|---------|
| `WBEM_S_NO_ERROR` | <span data-ttu-id="17fd2-116">0</span><span class="sxs-lookup"><span data-stu-id="17fd2-116">0</span></span> | <span data-ttu-id="17fd2-117">L’objet actuel `wszAncestor`hérite de .</span><span class="sxs-lookup"><span data-stu-id="17fd2-117">The current object inherits from `wszAncestor`.</span></span>  |
| `WBEM_S_FALSE` | <span data-ttu-id="17fd2-118">1</span><span class="sxs-lookup"><span data-stu-id="17fd2-118">1</span></span> | <span data-ttu-id="17fd2-119">L’objet actuel n’hérite pas de `wszAncestor`.</span><span class="sxs-lookup"><span data-stu-id="17fd2-119">The current object does not inherit from `wszAncestor`.</span></span> |
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="17fd2-120">0x80041008</span><span class="sxs-lookup"><span data-stu-id="17fd2-120">0x80041008</span></span> | <span data-ttu-id="17fd2-121">`wszAncestor` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="17fd2-121">`wszAncestor` is `null`.</span></span> |
  
## <a name="remarks"></a><span data-ttu-id="17fd2-122">Notes </span><span class="sxs-lookup"><span data-stu-id="17fd2-122">Remarks</span></span>

<span data-ttu-id="17fd2-123">Cette fonction enveloppe un appel à [l’IWbemClassObject::InheritsDe](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) méthode.</span><span class="sxs-lookup"><span data-stu-id="17fd2-123">This function wraps a call to the [IWbemClassObject::InheritsFrom](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-inheritsfrom) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="17fd2-124">Spécifications</span><span class="sxs-lookup"><span data-stu-id="17fd2-124">Requirements</span></span>  
 <span data-ttu-id="17fd2-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17fd2-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17fd2-126">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="17fd2-126">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="17fd2-127">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="17fd2-127">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17fd2-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17fd2-128">See also</span></span>

- [<span data-ttu-id="17fd2-129">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="17fd2-129">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
