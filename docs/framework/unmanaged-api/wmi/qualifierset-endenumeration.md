---
title: Fonction QualifierSet_EndEnumeration (référence des API non managées)
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
ms.openlocfilehash: 82627fa416f71e123ed2c03bae4584e4433310eb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127292"
---
# <a name="qualifierset_endenumeration-function"></a><span data-ttu-id="160cc-103">QualifierSet_EndEnumeration fonction)</span><span class="sxs-lookup"><span data-stu-id="160cc-103">QualifierSet_EndEnumeration function</span></span>
<span data-ttu-id="160cc-104">Termine l’énumération commencée par un appel à la fonction [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="160cc-104">Terminates the enumeration begun with a call to the [QualifierSet_BeginEnumeration](qualifierset-beginenumeration.md) function.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="160cc-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="160cc-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_EndEnumeration (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr
); 
```  

## <a name="parameters"></a><span data-ttu-id="160cc-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="160cc-106">Parameters</span></span>

`vFunc`  
<span data-ttu-id="160cc-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="160cc-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="160cc-108">dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="160cc-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

## <a name="return-value"></a><span data-ttu-id="160cc-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="160cc-109">Return value</span></span>

<span data-ttu-id="160cc-110">La valeur suivante retournée par cette fonction est définie dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez la définir en tant que constante dans votre code :</span><span class="sxs-lookup"><span data-stu-id="160cc-110">The following value returned by this function is defined in the *WbemCli.h* header file, or you can define it as a constant in your code:</span></span>

|<span data-ttu-id="160cc-111">Constante</span><span class="sxs-lookup"><span data-stu-id="160cc-111">Constant</span></span>  |<span data-ttu-id="160cc-112">valeur</span><span class="sxs-lookup"><span data-stu-id="160cc-112">Value</span></span>  |<span data-ttu-id="160cc-113">Description</span><span class="sxs-lookup"><span data-stu-id="160cc-113">Description</span></span>  |
|---------|---------|---------|
|`WBEM_S_NO_ERROR` | <span data-ttu-id="160cc-114">0</span><span class="sxs-lookup"><span data-stu-id="160cc-114">0</span></span> | <span data-ttu-id="160cc-115">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="160cc-115">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="160cc-116">Notes</span><span class="sxs-lookup"><span data-stu-id="160cc-116">Remarks</span></span>

<span data-ttu-id="160cc-117">Cette fonction encapsule un appel à la méthode [IWbemQualifierSet :: EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) .</span><span class="sxs-lookup"><span data-stu-id="160cc-117">This function wraps a call to the [IWbemQualifierSet::EndEnumeration](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-endenumeration) method.</span></span>

<span data-ttu-id="160cc-118">Cet appel est recommandé, mais pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="160cc-118">This call is recommended, but not required.</span></span> <span data-ttu-id="160cc-119">Il libère immédiatement les ressources associées à l’énumération.</span><span class="sxs-lookup"><span data-stu-id="160cc-119">It immediately releases resources associated with the enumeration.</span></span>

## <a name="requirements"></a><span data-ttu-id="160cc-120">spécifications</span><span class="sxs-lookup"><span data-stu-id="160cc-120">Requirements</span></span>  

<span data-ttu-id="160cc-121">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="160cc-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
<span data-ttu-id="160cc-122">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="160cc-122">**Header:** WMINet_Utils.idl</span></span>  
  
<span data-ttu-id="160cc-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="160cc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="160cc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="160cc-124">See also</span></span>

- [<span data-ttu-id="160cc-125">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="160cc-125">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
