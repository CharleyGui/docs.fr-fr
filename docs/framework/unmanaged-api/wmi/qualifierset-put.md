---
title: Fonction QualifierSet_Put (référence des API non managées)
description: La fonction QualifierSet_Put écrit le qualificateur nommé et sa valeur.
ms.date: 11/06/2017
api_name:
- QualifierSet_Put
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- QualifierSet_Put
helpviewer_keywords:
- QualifierSet_Put function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 40688a0e4273233245d00fcd927f95945a43f712
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798270"
---
# <a name="qualifierset_put-function"></a><span data-ttu-id="02cd1-103">QualifierSet_Put fonction)</span><span class="sxs-lookup"><span data-stu-id="02cd1-103">QualifierSet_Put function</span></span>

<span data-ttu-id="02cd1-104">Écrit la valeur et le qualificateur nommés.</span><span class="sxs-lookup"><span data-stu-id="02cd1-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="02cd1-105">Le nouveau qualificateur remplace la valeur précédente du même nom.</span><span class="sxs-lookup"><span data-stu-id="02cd1-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="02cd1-106">Si le qualificateur n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="02cd1-106">If the qualifier does not exist, it is created.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="02cd1-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02cd1-107">Syntax</span></span>

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="02cd1-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="02cd1-108">Parameters</span></span>

`vFunc`\
<span data-ttu-id="02cd1-109">dans Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="02cd1-109">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="02cd1-110">dans Pointeur vers une instance [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) .</span><span class="sxs-lookup"><span data-stu-id="02cd1-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`\
<span data-ttu-id="02cd1-111">dans Nom du qualificateur à écrire.</span><span class="sxs-lookup"><span data-stu-id="02cd1-111">[in] The name of the qualifier to write.</span></span>

`pVal`\
<span data-ttu-id="02cd1-112">dans Pointeur vers un valide `VARIANT` qui contient le qualificateur à écrire.</span><span class="sxs-lookup"><span data-stu-id="02cd1-112">[in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="02cd1-113">Ce paramètre ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="02cd1-113">This parameter cannot be `null`.</span></span>

`lFlavor`\
<span data-ttu-id="02cd1-114">dans L’une des constantes suivantes qui définit les versions de qualificateur souhaitées pour ce qualificateur.</span><span class="sxs-lookup"><span data-stu-id="02cd1-114">[in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="02cd1-115">La valeur par défaut `WBEM_FLAVOR_OVERRIDABLE` est (0).</span><span class="sxs-lookup"><span data-stu-id="02cd1-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="02cd1-116">Constante</span><span class="sxs-lookup"><span data-stu-id="02cd1-116">Constant</span></span>  |<span data-ttu-id="02cd1-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="02cd1-117">Value</span></span>  |<span data-ttu-id="02cd1-118">Description</span><span class="sxs-lookup"><span data-stu-id="02cd1-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="02cd1-119">0</span><span class="sxs-lookup"><span data-stu-id="02cd1-119">0</span></span> | <span data-ttu-id="02cd1-120">Le qualificateur peut être substitué dans une classe ou une instance dérivée.</span><span class="sxs-lookup"><span data-stu-id="02cd1-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="02cd1-121">**Il s’agit de la valeur par défaut.**</span><span class="sxs-lookup"><span data-stu-id="02cd1-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="02cd1-122">1</span><span class="sxs-lookup"><span data-stu-id="02cd1-122">1</span></span> | <span data-ttu-id="02cd1-123">Le qualificateur est propagé aux instances.</span><span class="sxs-lookup"><span data-stu-id="02cd1-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="02cd1-124">2</span><span class="sxs-lookup"><span data-stu-id="02cd1-124">2</span></span> | <span data-ttu-id="02cd1-125">Le qualificateur est propagé aux classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="02cd1-125">The qualifier is propagated to derived classes.</span></span> |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | <span data-ttu-id="02cd1-126">0x10</span><span class="sxs-lookup"><span data-stu-id="02cd1-126">0x10</span></span> | <span data-ttu-id="02cd1-127">Le qualificateur ne peut pas être écrasé dans une classe ou une instance dérivée.</span><span class="sxs-lookup"><span data-stu-id="02cd1-127">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| `WBEM_FLAVOR_AMENDED` | <span data-ttu-id="02cd1-128">0x80</span><span class="sxs-lookup"><span data-stu-id="02cd1-128">0x80</span></span> | <span data-ttu-id="02cd1-129">Le qualificateur est localisé.</span><span class="sxs-lookup"><span data-stu-id="02cd1-129">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="02cd1-130">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="02cd1-130">Return value</span></span>

<span data-ttu-id="02cd1-131">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="02cd1-131">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="02cd1-132">Constante</span><span class="sxs-lookup"><span data-stu-id="02cd1-132">Constant</span></span>  |<span data-ttu-id="02cd1-133">Valeur</span><span class="sxs-lookup"><span data-stu-id="02cd1-133">Value</span></span>  |<span data-ttu-id="02cd1-134">Description</span><span class="sxs-lookup"><span data-stu-id="02cd1-134">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="02cd1-135">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="02cd1-135">0x8004101f</span></span> | <span data-ttu-id="02cd1-136">Tentative non autorisée de spécifier le qualificateur de **clé** sur une propriété qui ne peut pas être une clé.</span><span class="sxs-lookup"><span data-stu-id="02cd1-136">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="02cd1-137">Les clés sont spécifiées dans la définition de classe pour un objet et ne peuvent pas être modifiées pour chaque instance.</span><span class="sxs-lookup"><span data-stu-id="02cd1-137">The keys are specified in the class definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="02cd1-138">0x80041008</span><span class="sxs-lookup"><span data-stu-id="02cd1-138">0x80041008</span></span> | <span data-ttu-id="02cd1-139">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="02cd1-139">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="02cd1-140">0x80041029</span><span class="sxs-lookup"><span data-stu-id="02cd1-140">0x80041029</span></span> | <span data-ttu-id="02cd1-141">Le `pVal` paramètre n’est pas d’un type de qualificateur légal.</span><span class="sxs-lookup"><span data-stu-id="02cd1-141">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="02cd1-142">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="02cd1-142">0x8004101a</span></span> | <span data-ttu-id="02cd1-143">Il n’est pas possible d’appeler `QualifierSet_Put` la méthode sur le qualificateur, car l’objet propriétaire n’autorise pas les substitutions.</span><span class="sxs-lookup"><span data-stu-id="02cd1-143">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="02cd1-144">0</span><span class="sxs-lookup"><span data-stu-id="02cd1-144">0</span></span> | <span data-ttu-id="02cd1-145">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="02cd1-145">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="02cd1-146">Notes</span><span class="sxs-lookup"><span data-stu-id="02cd1-146">Remarks</span></span>

<span data-ttu-id="02cd1-147">Cette fonction encapsule un appel à la méthode [IWbemQualifierSet ::P ut](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) .</span><span class="sxs-lookup"><span data-stu-id="02cd1-147">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="02cd1-148">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="02cd1-148">Requirements</span></span>

<span data-ttu-id="02cd1-149">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02cd1-149">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="02cd1-150">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="02cd1-150">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="02cd1-151">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="02cd1-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="02cd1-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="02cd1-152">See also</span></span>

- [<span data-ttu-id="02cd1-153">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="02cd1-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
