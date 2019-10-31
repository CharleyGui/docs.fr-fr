---
title: Fonction CreateInstanceEnumWmi (référence des API non managées)
description: La fonction CreateInstanceEnumWmi retourne un énumérateur contenant des instances d’une classe spécifiée qui répondent aux critères de sélection.
ms.date: 11/06/2017
api_name:
- CreateInstanceEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstanceEnumWmi
helpviewer_keywords:
- CreateInstanceEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 9ffa718be0e8b67471fdf8cb277df201388d2840
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130402"
---
# <a name="createinstanceenumwmi-function"></a><span data-ttu-id="6de04-103">CreateInstanceEnumWmi fonction)</span><span class="sxs-lookup"><span data-stu-id="6de04-103">CreateInstanceEnumWmi function</span></span>

<span data-ttu-id="6de04-104">Retourne un énumérateur qui retourne les instances d’une classe spécifiée remplissant les critères de sélection spécifiés.</span><span class="sxs-lookup"><span data-stu-id="6de04-104">Returns an enumerator that returns the instances of a specified class that meet specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="6de04-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6de04-105">Syntax</span></span>

```cpp
HRESULT CreateInstanceEnumWmi (
   [in] BSTR                    strFilter,
   [in] long                    lFlags,
   [in] IWbemContext*           pCtx,
   [out] IEnumWbemClassObject** ppEnum,
   [in] DWORD                   authLevel,
   [in] DWORD                   impLevel,
   [in] IWbemServices*          pCurrentNamespace,
   [in] BSTR                    strUser,
   [in] BSTR                    strPassword,
   [in] BSTR                    strAuthority
);
```

## <a name="parameters"></a><span data-ttu-id="6de04-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6de04-106">Parameters</span></span>

`strFilter`\
<span data-ttu-id="6de04-107">dans Nom de la classe pour laquelle les instances sont souhaitées.</span><span class="sxs-lookup"><span data-stu-id="6de04-107">[in] The name of the class for which instances are desired.</span></span> <span data-ttu-id="6de04-108">Ce paramètre ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="6de04-108">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="6de04-109">dans Combinaison d’indicateurs qui affectent le comportement de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="6de04-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="6de04-110">Les valeurs suivantes sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="6de04-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6de04-111">Constante</span><span class="sxs-lookup"><span data-stu-id="6de04-111">Constant</span></span>  |<span data-ttu-id="6de04-112">valeur</span><span class="sxs-lookup"><span data-stu-id="6de04-112">Value</span></span>  |<span data-ttu-id="6de04-113">Description</span><span class="sxs-lookup"><span data-stu-id="6de04-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="6de04-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="6de04-114">0x20000</span></span> | <span data-ttu-id="6de04-115">Si cette valeur est définie, la fonction récupère les qualificateurs modifiés stockés dans l’espace de noms localisé des paramètres régionaux de la connexion actuelle.</span><span class="sxs-lookup"><span data-stu-id="6de04-115">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="6de04-116">Si la valeur n’est pas définie, la fonction récupère uniquement les qualificateurs stockés dans l’espace de noms immédiat.</span><span class="sxs-lookup"><span data-stu-id="6de04-116">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="6de04-117">0</span><span class="sxs-lookup"><span data-stu-id="6de04-117">0</span></span> | <span data-ttu-id="6de04-118">L’énumération comprend cette et toutes les sous-classes de la hiérarchie.</span><span class="sxs-lookup"><span data-stu-id="6de04-118">The enumeration includes this and all subclasses in the hierarchy.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="6de04-119">1</span><span class="sxs-lookup"><span data-stu-id="6de04-119">1</span></span> | <span data-ttu-id="6de04-120">L’énumération inclut uniquement des instances pures de cette classe et exclut toutes les instances des sous-classes qui fournissent des propriétés introuvables dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="6de04-120">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="6de04-121">0x10</span><span class="sxs-lookup"><span data-stu-id="6de04-121">0x10</span></span> | <span data-ttu-id="6de04-122">L’indicateur provoque un appel semi-synchrone.</span><span class="sxs-lookup"><span data-stu-id="6de04-122">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="6de04-123">0x20</span><span class="sxs-lookup"><span data-stu-id="6de04-123">0x20</span></span> | <span data-ttu-id="6de04-124">La fonction retourne un énumérateur avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="6de04-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="6de04-125">En général, les énumérateurs avant uniquement sont plus rapides et utilisent moins de mémoire que les énumérateurs conventionnels, mais ils n’autorisent pas les appels à [cloner](clone.md).</span><span class="sxs-lookup"><span data-stu-id="6de04-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="6de04-126">0</span><span class="sxs-lookup"><span data-stu-id="6de04-126">0</span></span> | <span data-ttu-id="6de04-127">WMI conserve les pointeurs vers les objets de l’énumération jusqu’à ce qu’ils soient libérés.</span><span class="sxs-lookup"><span data-stu-id="6de04-127">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="6de04-128">Les indicateurs recommandés sont `WBEM_FLAG_RETURN_IMMEDIATELY` et `WBEM_FLAG_FORWARD_ONLY` pour des performances optimales.</span><span class="sxs-lookup"><span data-stu-id="6de04-128">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="6de04-129">dans En général, cette valeur est `null`.</span><span class="sxs-lookup"><span data-stu-id="6de04-129">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="6de04-130">Dans le cas contraire, il s’agit d’un pointeur vers une instance [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) qui peut être utilisée par le fournisseur qui fournit les instances demandées.</span><span class="sxs-lookup"><span data-stu-id="6de04-130">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that may be used by the provider that is providing the requested instances.</span></span>

`ppEnum`\
<span data-ttu-id="6de04-131">à Reçoit le pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="6de04-131">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="6de04-132">dans Niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="6de04-132">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="6de04-133">dans Niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="6de04-133">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="6de04-134">dans Pointeur vers un objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) qui représente l’espace de noms actuel.</span><span class="sxs-lookup"><span data-stu-id="6de04-134">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="6de04-135">dans Nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6de04-135">[in] The user name.</span></span> <span data-ttu-id="6de04-136">Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6de04-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="6de04-137">dans Mot de passe.</span><span class="sxs-lookup"><span data-stu-id="6de04-137">[in] The password.</span></span> <span data-ttu-id="6de04-138">Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6de04-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="6de04-139">dans Nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6de04-139">[in] The domain name of the user.</span></span> <span data-ttu-id="6de04-140">Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6de04-140">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="6de04-141">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6de04-141">Return value</span></span>

<span data-ttu-id="6de04-142">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="6de04-142">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="6de04-143">Constante</span><span class="sxs-lookup"><span data-stu-id="6de04-143">Constant</span></span>  |<span data-ttu-id="6de04-144">valeur</span><span class="sxs-lookup"><span data-stu-id="6de04-144">Value</span></span>  |<span data-ttu-id="6de04-145">Description</span><span class="sxs-lookup"><span data-stu-id="6de04-145">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="6de04-146">0x80041003</span><span class="sxs-lookup"><span data-stu-id="6de04-146">0x80041003</span></span> | <span data-ttu-id="6de04-147">L’utilisateur n’a pas l’autorisation d’afficher les instances de la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6de04-147">The user does not have permission to view instances of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="6de04-148">0x80041001</span><span class="sxs-lookup"><span data-stu-id="6de04-148">0x80041001</span></span> | <span data-ttu-id="6de04-149">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="6de04-149">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="6de04-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="6de04-150">0x80041010</span></span> | <span data-ttu-id="6de04-151">`strFilter` n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="6de04-151">`strFilter` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="6de04-152">0x80041008</span><span class="sxs-lookup"><span data-stu-id="6de04-152">0x80041008</span></span> | <span data-ttu-id="6de04-153">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="6de04-153">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="6de04-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="6de04-154">0x80041006</span></span> | <span data-ttu-id="6de04-155">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="6de04-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="6de04-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="6de04-156">0x80041033</span></span> | <span data-ttu-id="6de04-157">WMI a probablement été arrêté et redémarré.</span><span class="sxs-lookup"><span data-stu-id="6de04-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="6de04-158">Appelez à nouveau [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="6de04-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="6de04-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="6de04-159">0x80041015</span></span> | <span data-ttu-id="6de04-160">Le lien de l’appel de procédure distante (RPC) entre le processus en cours et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="6de04-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="6de04-161">0</span><span class="sxs-lookup"><span data-stu-id="6de04-161">0</span></span> | <span data-ttu-id="6de04-162">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="6de04-162">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="6de04-163">Notes</span><span class="sxs-lookup"><span data-stu-id="6de04-163">Remarks</span></span>

<span data-ttu-id="6de04-164">Cette fonction encapsule un appel à la méthode [IWbemServices :: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) .</span><span class="sxs-lookup"><span data-stu-id="6de04-164">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) method.</span></span>

<span data-ttu-id="6de04-165">Notez que l’énumérateur retourné peut avoir zéro élément.</span><span class="sxs-lookup"><span data-stu-id="6de04-165">Note that the returned enumerator can have zero elements.</span></span>

<span data-ttu-id="6de04-166">Si l’appel de fonction échoue, vous pouvez obtenir des informations supplémentaires sur l’erreur en appelant la fonction [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="6de04-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="6de04-167">spécifications</span><span class="sxs-lookup"><span data-stu-id="6de04-167">Requirements</span></span>

<span data-ttu-id="6de04-168">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6de04-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="6de04-169">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="6de04-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="6de04-170">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6de04-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6de04-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6de04-171">See also</span></span>

- [<span data-ttu-id="6de04-172">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="6de04-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
