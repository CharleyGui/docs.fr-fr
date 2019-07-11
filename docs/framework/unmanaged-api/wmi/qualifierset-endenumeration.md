---
title: QualifierSet_EndEnumeration (fonction) (référence des API non managées)
description: La fonction QualifierSet_EndEnumeration met fin à une énumération.
ms.date: 11/06/2017
api_name:
- QualifierSet_EndEnumeration
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_EndEnumeration
helpviewer_keywords:
- QualifierSet_EndEnumeration function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 206d6448835b60c55b378636ff5daa5fa4f8b5d0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782594"
---
# <a name="qualifiersetendenumeration-function"></a><span data-ttu-id="450f0-103">QualifierSet_EndEnumeration (fonction)</span><span class="sxs-lookup"><span data-stu-id="450f0-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="450f0-104">Met fin à l’énumération commencée avec un appel à la [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="450f0-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="450f0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="450f0-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="450f0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="450f0-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="450f0-107">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="450f0-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="450f0-108">[in] Un pointeur vers un [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="450f0-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="450f0-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="450f0-109">Return value</span></span>

<span data-ttu-id="450f0-110">La valeur suivante est retournée par cette fonction est définie dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez la définir en tant que constante dans votre code :</span><span class="sxs-lookup"><span data-stu-id="450f0-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="450f0-111">Constante</span><span class="sxs-lookup"><span data-stu-id="450f0-111">Constant</span></span>  |<span data-ttu-id="450f0-112">`Value`</span><span class="sxs-lookup"><span data-stu-id="450f0-112">Value</span></span>  |<span data-ttu-id="450f0-113">Description</span><span class="sxs-lookup"><span data-stu-id="450f0-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="450f0-114">0</span><span class="sxs-lookup"><span data-stu-id="450f0-114">0</span></span> | <span data-ttu-id="450f0-115">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="450f0-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="450f0-116">Notes</span><span class="sxs-lookup"><span data-stu-id="450f0-116">Remarks</span></span>

<span data-ttu-id="450f0-117">Cette fonction encapsule un appel à la [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) (méthode).</span><span class="sxs-lookup"><span data-stu-id="450f0-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="450f0-118">Cet appel est recommandé, mais pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="450f0-118">This call is recommended, but not required.</span></span> <span data-ttu-id="450f0-119">Il libère immédiatement les ressources associées à l’énumération.</span><span class="sxs-lookup"><span data-stu-id="450f0-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="450f0-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="450f0-120">Requirements</span></span>  

<span data-ttu-id="450f0-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="450f0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="450f0-122">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="450f0-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="450f0-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="450f0-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="450f0-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="450f0-124">See also</span></span>

- [<span data-ttu-id="450f0-125">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="450f0-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
