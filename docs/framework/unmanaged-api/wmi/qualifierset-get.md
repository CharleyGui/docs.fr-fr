---
title: fonction QualifierSet_Get (référence API non gestion)
description: La fonction QualifierSet_Get obtient un qualificatif nommé.
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
ms.openlocfilehash: 2f4e2d4518e01f3415b8f17ce5778dd98b2a45c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174886"
---
# <a name="qualifierset_get-function"></a><span data-ttu-id="7403f-103">QualifierSet_Get, fonction</span><span class="sxs-lookup"><span data-stu-id="7403f-103">QualifierSet_Get function</span></span>
<span data-ttu-id="7403f-104">Obtient le qualificateur nommé spécifié.</span><span class="sxs-lookup"><span data-stu-id="7403f-104">Gets the specified named qualifier.</span></span>  

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="7403f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7403f-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="7403f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7403f-106">Parameters</span></span>

<span data-ttu-id="7403f-107">`vFunc`[dans] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="7403f-107">`vFunc` [in] This parameter is unused.</span></span>

<span data-ttu-id="7403f-108">`ptr`[dans] Un pointeur à une instance [IWbemQualifierSet.](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset)</span><span class="sxs-lookup"><span data-stu-id="7403f-108">`ptr` [in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

<span data-ttu-id="7403f-109">`wszName`[dans] Le nom du qualificatif dont la valeur est demandée.</span><span class="sxs-lookup"><span data-stu-id="7403f-109">`wszName` [in] The name of the qualifier whose value is requested.</span></span>

<span data-ttu-id="7403f-110">`lFlags`[dans] Réservés au.</span><span class="sxs-lookup"><span data-stu-id="7403f-110">`lFlags` [in] Reserved.</span></span> <span data-ttu-id="7403f-111">Ce paramètre doit être de 0.</span><span class="sxs-lookup"><span data-stu-id="7403f-111">This parameter must be 0.</span></span>

<span data-ttu-id="7403f-112">`pVal`[out] En cas de succès, le bon type et la valeur pour le qualificatif.</span><span class="sxs-lookup"><span data-stu-id="7403f-112">`pVal` [out] When successful, the correct type and value for the qualifier.</span></span> <span data-ttu-id="7403f-113">Si la fonction `VARIANT` échoue, `pVal` le pointé vers par n’est pas modifié.</span><span class="sxs-lookup"><span data-stu-id="7403f-113">If the function fails, the `VARIANT` pointed to by `pVal` is not modified.</span></span> <span data-ttu-id="7403f-114">Si ce `null`paramètre est , le paramètre est ignoré.</span><span class="sxs-lookup"><span data-stu-id="7403f-114">If this parameter is `null`, the parameter is ignored.</span></span>

<span data-ttu-id="7403f-115">`plFlavor`[out] Un pointeur à un LONG qui reçoit les bits de saveur qualificatif pour le qualificatif demandé.</span><span class="sxs-lookup"><span data-stu-id="7403f-115">`plFlavor` [out] A pointer to a LONG that receives the qualifier flavor bits for the requested qualifier.</span></span> <span data-ttu-id="7403f-116">Si l’information de saveur n’est pas désirée, ce paramètre peut être `null`.</span><span class="sxs-lookup"><span data-stu-id="7403f-116">If flavor information is not desired, this parameter can be `null`.</span></span>

## <a name="return-value"></a><span data-ttu-id="7403f-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="7403f-117">Return value</span></span>

<span data-ttu-id="7403f-118">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="7403f-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="7403f-119">Constant</span><span class="sxs-lookup"><span data-stu-id="7403f-119">Constant</span></span>  |<span data-ttu-id="7403f-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="7403f-120">Value</span></span>  |<span data-ttu-id="7403f-121">Description</span><span class="sxs-lookup"><span data-stu-id="7403f-121">Description</span></span>  |
|---------|---------|---------|
|`WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="7403f-122">0x80041008</span><span class="sxs-lookup"><span data-stu-id="7403f-122">0x80041008</span></span> | <span data-ttu-id="7403f-123">Un paramètre n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="7403f-123">A parameter is not valid.</span></span> |
|`WBEM_E_NOT_FOUND` | <span data-ttu-id="7403f-124">0x80041002</span><span class="sxs-lookup"><span data-stu-id="7403f-124">0x80041002</span></span> | <span data-ttu-id="7403f-125">Le qualificatif spécifié n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="7403f-125">The specified qualifier does not exist.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="7403f-126">0</span><span class="sxs-lookup"><span data-stu-id="7403f-126">0</span></span> | <span data-ttu-id="7403f-127">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="7403f-127">The function call was successful.</span></span>  |
  
## <a name="remarks"></a><span data-ttu-id="7403f-128">Notes </span><span class="sxs-lookup"><span data-stu-id="7403f-128">Remarks</span></span>

<span data-ttu-id="7403f-129">Cette fonction enveloppe un appel à [l’IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) méthode.</span><span class="sxs-lookup"><span data-stu-id="7403f-129">This function wraps a call to the [IWbemQualifierSet::Get](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-get) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7403f-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7403f-130">Requirements</span></span>  
 <span data-ttu-id="7403f-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7403f-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7403f-132">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="7403f-132">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="7403f-133">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="7403f-133">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7403f-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7403f-134">See also</span></span>

- [<span data-ttu-id="7403f-135">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="7403f-135">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
