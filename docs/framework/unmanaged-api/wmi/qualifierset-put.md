---
title: QualifierSet_Put (fonction) (référence des API non managées)
description: La fonction QualifierSet_Put écrit qualificateur nommé et sa valeur.
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
ms.openlocfilehash: 42bef9ab728af251b043e29af4cee9e5cb3f405d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636543"
---
# <a name="qualifiersetput-function"></a><span data-ttu-id="9af5e-103">QualifierSet_Put (fonction)</span><span class="sxs-lookup"><span data-stu-id="9af5e-103">QualifierSet_Put function</span></span>

<span data-ttu-id="9af5e-104">Écrit la valeur et le qualificateur nommés.</span><span class="sxs-lookup"><span data-stu-id="9af5e-104">Writes the named qualifier and value.</span></span> <span data-ttu-id="9af5e-105">Le nouveau qualificateur remplace la valeur précédente du même nom.</span><span class="sxs-lookup"><span data-stu-id="9af5e-105">The new qualifier overwrites the previous value of the same name.</span></span> <span data-ttu-id="9af5e-106">Si le qualificateur n’existe pas, il est créé.</span><span class="sxs-lookup"><span data-stu-id="9af5e-106">If the qualifier does not exist, it is created.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="9af5e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9af5e-107">Syntax</span></span>

```cpp
HRESULT QualifierSet_Put (
   [in] int                  vFunc,
   [in] IWbemQualifierSet*   ptr,
   [in] LPCWSTR              wszName,
   [in] VARIANT*             pVal,
   [in] LONG                 lFlavor
);
```

## <a name="parameters"></a><span data-ttu-id="9af5e-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9af5e-108">Parameters</span></span>

`vFunc`\
<span data-ttu-id="9af5e-109">[in] Ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="9af5e-109">[in] This parameter is unused.</span></span>

`ptr`\
<span data-ttu-id="9af5e-110">[in] Un pointeur vers un [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span><span class="sxs-lookup"><span data-stu-id="9af5e-110">[in] A pointer to an [IWbemQualifierSet](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemqualifierset) instance.</span></span>

`wszName`\
<span data-ttu-id="9af5e-111">[in] Le nom du qualificateur à écrire.</span><span class="sxs-lookup"><span data-stu-id="9af5e-111">[in] The name of the qualifier to write.</span></span>

`pVal`\
<span data-ttu-id="9af5e-112">[in] Un pointeur vers une valide `VARIANT` qui contient le qualificateur à écrire.</span><span class="sxs-lookup"><span data-stu-id="9af5e-112">[in] A pointer to a valid `VARIANT` that contains the qualifier to write.</span></span> <span data-ttu-id="9af5e-113">Ce paramètre ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="9af5e-113">This parameter cannot be `null`.</span></span>

`lFlavor`\
<span data-ttu-id="9af5e-114">[in] Une des constantes suivantes qui définit les types de qualificateurs souhaitée pour ce qualificateur.</span><span class="sxs-lookup"><span data-stu-id="9af5e-114">[in] One of the following constants that defines the desired qualifier flavors for this qualifier.</span></span> <span data-ttu-id="9af5e-115">La valeur par défaut est `WBEM_FLAVOR_OVERRIDABLE` (0).</span><span class="sxs-lookup"><span data-stu-id="9af5e-115">The default value is `WBEM_FLAVOR_OVERRIDABLE` (0).</span></span>

|<span data-ttu-id="9af5e-116">Constante</span><span class="sxs-lookup"><span data-stu-id="9af5e-116">Constant</span></span>  |<span data-ttu-id="9af5e-117">Value</span><span class="sxs-lookup"><span data-stu-id="9af5e-117">Value</span></span>  |<span data-ttu-id="9af5e-118">Description</span><span class="sxs-lookup"><span data-stu-id="9af5e-118">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAVOR_OVERRIDABLE` | <span data-ttu-id="9af5e-119">0</span><span class="sxs-lookup"><span data-stu-id="9af5e-119">0</span></span> | <span data-ttu-id="9af5e-120">Le qualificateur peut être substitué dans une classe dérivée ou une instance.</span><span class="sxs-lookup"><span data-stu-id="9af5e-120">The qualifier can be overridden in a derived class or instance.</span></span> <span data-ttu-id="9af5e-121">**Il s’agit de la valeur par défaut.**</span><span class="sxs-lookup"><span data-stu-id="9af5e-121">**This is the default value.**</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_INSTANCE` | <span data-ttu-id="9af5e-122">1</span><span class="sxs-lookup"><span data-stu-id="9af5e-122">1</span></span> | <span data-ttu-id="9af5e-123">Le qualificateur est propagé aux instances.</span><span class="sxs-lookup"><span data-stu-id="9af5e-123">The qualifier is propagated to instances.</span></span> |
| `WBEM_FLAVOR_FLAG_PROPAGATE_TO_DERIVED_CLASS` | <span data-ttu-id="9af5e-124">2</span><span class="sxs-lookup"><span data-stu-id="9af5e-124">2</span></span> | <span data-ttu-id="9af5e-125">Le qualificateur est propagé aux classes dérivées.</span><span class="sxs-lookup"><span data-stu-id="9af5e-125">The qualifier is propagated to derived classes.</span></span> |
| `WBEM_FLAVOR_NOT_OVERRIDABLE` | <span data-ttu-id="9af5e-126">0x10</span><span class="sxs-lookup"><span data-stu-id="9af5e-126">0x10</span></span> | <span data-ttu-id="9af5e-127">Le qualificateur ne peut pas être écrasé dans une classe ou une instance dérivée.</span><span class="sxs-lookup"><span data-stu-id="9af5e-127">The qualifier cannot be overridden in a derived class or instance.</span></span> |
| `WBEM_FLAVOR_AMENDED` | <span data-ttu-id="9af5e-128">0x80</span><span class="sxs-lookup"><span data-stu-id="9af5e-128">0x80</span></span> | <span data-ttu-id="9af5e-129">Le qualificateur est localisé.</span><span class="sxs-lookup"><span data-stu-id="9af5e-129">The qualifier is localized.</span></span> |

## <a name="return-value"></a><span data-ttu-id="9af5e-130">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9af5e-130">Return value</span></span>

<span data-ttu-id="9af5e-131">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="9af5e-131">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9af5e-132">Constante</span><span class="sxs-lookup"><span data-stu-id="9af5e-132">Constant</span></span>  |<span data-ttu-id="9af5e-133">Value</span><span class="sxs-lookup"><span data-stu-id="9af5e-133">Value</span></span>  |<span data-ttu-id="9af5e-134">Description</span><span class="sxs-lookup"><span data-stu-id="9af5e-134">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_CANNOT_BE_KEY` | <span data-ttu-id="9af5e-135">0x8004101f</span><span class="sxs-lookup"><span data-stu-id="9af5e-135">0x8004101f</span></span> | <span data-ttu-id="9af5e-136">Il y a une tentative non conforme pour spécifier le **clé** qualificateur sur une propriété qui ne peut pas être une clé.</span><span class="sxs-lookup"><span data-stu-id="9af5e-136">There was an illegal attempt to specify the **Key** qualifier on a property that cannot be a key.</span></span> <span data-ttu-id="9af5e-137">Les clés sont spécifiés om c ; définition ass pour un objet et ne peut pas être modifiée sur une base par instance.</span><span class="sxs-lookup"><span data-stu-id="9af5e-137">The keys are specified om tje c;ass definition for an object and cannot be altered on a per-instance basis.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="9af5e-138">0x80041008</span><span class="sxs-lookup"><span data-stu-id="9af5e-138">0x80041008</span></span> | <span data-ttu-id="9af5e-139">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="9af5e-139">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_QUALIFIER_TYPE` | <span data-ttu-id="9af5e-140">0x80041029</span><span class="sxs-lookup"><span data-stu-id="9af5e-140">0x80041029</span></span> | <span data-ttu-id="9af5e-141">Le `pVal` paramètre n’est pas un type de qualificateur conforme.</span><span class="sxs-lookup"><span data-stu-id="9af5e-141">The `pVal` parameter is not of a legal qualifier type.</span></span> |
| `WBEM_E_OVERRIDE_NOT_ALLOWED` | <span data-ttu-id="9af5e-142">0x8004101a</span><span class="sxs-lookup"><span data-stu-id="9af5e-142">0x8004101a</span></span> | <span data-ttu-id="9af5e-143">Il n’est pas possible d’appeler le `QualifierSet_Put` substitutions des méthodes sur le qualificateur parce que l’objet propriétaire n’autorise pas.</span><span class="sxs-lookup"><span data-stu-id="9af5e-143">It is not possible to call the `QualifierSet_Put` method on the qualifier because the owning object does not permit overrides.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="9af5e-144">0</span><span class="sxs-lookup"><span data-stu-id="9af5e-144">0</span></span> | <span data-ttu-id="9af5e-145">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="9af5e-145">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="9af5e-146">Notes</span><span class="sxs-lookup"><span data-stu-id="9af5e-146">Remarks</span></span>

<span data-ttu-id="9af5e-147">Cette fonction encapsule un appel à la [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) (méthode).</span><span class="sxs-lookup"><span data-stu-id="9af5e-147">This function wraps a call to the [IWbemQualifierSet::Put](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemqualifierset-put) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9af5e-148">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9af5e-148">Requirements</span></span>

<span data-ttu-id="9af5e-149">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9af5e-149">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="9af5e-150">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="9af5e-150">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="9af5e-151">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9af5e-151">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="9af5e-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9af5e-152">See also</span></span>

- [<span data-ttu-id="9af5e-153">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="9af5e-153">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
