---
title: Fonction QualifierSet_Get (référence des API non managées)
description: La fonction QualifierSet_Get obtient un qualificateur nommé.
ms.date: 11/06/2017
api_name:
- QualifierSet_Get
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Get
helpviewer_keywords:
- QualifierSet_Get function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: dc09cd30c43647fa00cccc1dc00da4f8de367e84
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127274"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="1fef7-103">QualifierSet_Get fonction)</span><span class="sxs-lookup"><span data-stu-id="1fef7-103">QualifierSet_Get function</span></span>
<span data-ttu-id="1fef7-104">Obtient le qualificateur nommé spécifié.</span><span class="sxs-lookup"><span data-stu-id="1fef7-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="1fef7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fef7-105">Syntax</span></span>  
  
```cpp  
HRESULT QualifierSet_Get (
   [in] int                  vFunc, 
   [in] IWbemQualifierSet*   ptr, 
   [in] LPCWSTR              wszName,
   [in] LONG                 lFlags,
   [out] VARIANT*            pVal,
   [out] LONG*               plFlavor                 
); 
```  

## <a name="parameters"></a><span data-ttu-id="1fef7-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1fef7-106">Parameters</span></span>

`vFunc`   
<span data-ttu-id="1fef7-107">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="1fef7-107">[in] This parameter is unused.</span></span>

`ptr`   
<span data-ttu-id="1fef7-108">dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="1fef7-108">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`   
<span data-ttu-id="1fef7-109">dans Nom du qualificateur dont la valeur est demandée.</span><span class="sxs-lookup"><span data-stu-id="1fef7-109">[in] The name of the qualifier whose value is requested.</span></span>

`lFlags`   
<span data-ttu-id="1fef7-110">[in] Réservée.</span><span class="sxs-lookup"><span data-stu-id="1fef7-110">[in] Reserved.</span></span> <span data-ttu-id="1fef7-111">Ce paramètre doit avoir la valeur 0.</span><span class="sxs-lookup"><span data-stu-id="1fef7-111">This parameter must be 0.</span></span>

`pVal`   
<span data-ttu-id="1fef7-112">à En cas de réussite, le type et la valeur corrects pour le qualificateur.</span><span class="sxs-lookup"><span data-stu-id="1fef7-112">[out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="1fef7-113">Si la fonction échoue, le `VARIANT` désigné par `pVal` n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="1fef7-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="1fef7-114">Si ce paramètre est `null`, le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="1fef7-114">If this parameter is `null`, the parameter is ignored.</span></span>

`plFlavor`   
<span data-ttu-id="1fef7-115">à Pointeur vers une valeur de type LONG qui reçoit les bits de version de qualificateur pour le qualificateur demandé.</span><span class="sxs-lookup"><span data-stu-id="1fef7-115">[out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="1fef7-116">Si les informations de version ne sont pas souhaitées, ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="1fef7-116">If flavor information is not desired, this parameter can be `null`.</span></span> 

## <a name="return-value"></a><span data-ttu-id="1fef7-117">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1fef7-117">Return value</span></span>

<span data-ttu-id="1fef7-118">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="1fef7-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="1fef7-119">Constante</span><span class="sxs-lookup"><span data-stu-id="1fef7-119">Constant</span></span>  |<span data-ttu-id="1fef7-120">valeur</span><span class="sxs-lookup"><span data-stu-id="1fef7-120">Value</span></span>  |<span data-ttu-id="1fef7-121">Description</span><span class="sxs-lookup"><span data-stu-id="1fef7-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="1fef7-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="1fef7-122">0x80041008</span></span> | <span data-ttu-id="1fef7-123">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="1fef7-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="1fef7-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="1fef7-124">0x80041002</span></span> | <span data-ttu-id="1fef7-125">Le qualificateur spécifié n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="1fef7-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="1fef7-126">0</span><span class="sxs-lookup"><span data-stu-id="1fef7-126">0</span></span> | <span data-ttu-id="1fef7-127">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="1fef7-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="1fef7-128">Notes</span><span class="sxs-lookup"><span data-stu-id="1fef7-128">Remarks</span></span>

<span data-ttu-id="1fef7-129">Cette fonction encapsule un appel à la méthode [IWbemQualifierSet :: obtenir](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) .</span><span class="sxs-lookup"><span data-stu-id="1fef7-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1fef7-130">spécifications</span><span class="sxs-lookup"><span data-stu-id="1fef7-130">Requirements</span></span>  
 <span data-ttu-id="1fef7-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1fef7-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1fef7-132">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="1fef7-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="1fef7-133">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1fef7-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fef7-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1fef7-134">See also</span></span>

- [<span data-ttu-id="1fef7-135">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="1fef7-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
