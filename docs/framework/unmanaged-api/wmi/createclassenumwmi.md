---
title: Fonction CreateClassEnumWmi (référence des API non managées)
description: La fonction CreateClassEnumWmi retourne un énumérateur pour toutes les classes qui répondent aux critères spécifiés.
ms.date: 11/06/2017
api_name:
- CreateClassEnumWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CreateClassEnumWmi
helpviewer_keywords:
- CreateClassEnumWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a696a6f02f6d3a5afbcb45e5566e4b667739e2c5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798742"
---
# <a name="createclassenumwmi-function"></a><span data-ttu-id="d256e-103">CreateClassEnumWmi fonction)</span><span class="sxs-lookup"><span data-stu-id="d256e-103">CreateClassEnumWmi function</span></span>
<span data-ttu-id="d256e-104">Retourne un énumérateur pour toutes les classes qui remplissent les critères de sélection spécifiés.</span><span class="sxs-lookup"><span data-stu-id="d256e-104">Returns an enumerator for all classes that satisfy the specified selection criteria.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="d256e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d256e-105">Syntax</span></span>

```cpp
HRESULT CreateClassEnumWmi (
   [in] BSTR                    strSuperclass,
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

## <a name="parameters"></a><span data-ttu-id="d256e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d256e-106">Parameters</span></span>

`strSuperclass`\
<span data-ttu-id="d256e-107">dans Si la `null` valeur n’est pas ou vide, spécifie le nom d’une classe parente ; l’énumérateur retourne uniquement les sous-classes de cette classe.</span><span class="sxs-lookup"><span data-stu-id="d256e-107">[in] If not `null` or blank, specifies the name of a parent class; the enumerator returns only subclasses of this class.</span></span> <span data-ttu-id="d256e-108">Si elle est `null` ou vide et `lFlags` est WBEM_FLAG_SHALLOW, retourne uniquement les classes de niveau supérieur (classes sans classe parente).</span><span class="sxs-lookup"><span data-stu-id="d256e-108">If it is `null` or blank and `lFlags` is WBEM_FLAG_SHALLOW, returns only top-level classes (classes with no parent class).</span></span> <span data-ttu-id="d256e-109">Si la valeur `null` est ou est `lFlags` vide `WBEM_FLAG_DEEP`et si a la valeur, retourne toutes les classes de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d256e-109">If it is `null` or blank and `lFlags` is `WBEM_FLAG_DEEP`, returns all classes in the namespace.</span></span>

`lFlags`\
<span data-ttu-id="d256e-110">dans Combinaison d’indicateurs qui affectent le comportement de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="d256e-110">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="d256e-111">Les valeurs suivantes sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="d256e-111">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d256e-112">Constante</span><span class="sxs-lookup"><span data-stu-id="d256e-112">Constant</span></span>  |<span data-ttu-id="d256e-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="d256e-113">Value</span></span>  |<span data-ttu-id="d256e-114">Description</span><span class="sxs-lookup"><span data-stu-id="d256e-114">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="d256e-115">0x20000</span><span class="sxs-lookup"><span data-stu-id="d256e-115">0x20000</span></span> | <span data-ttu-id="d256e-116">Si cette valeur est définie, la fonction récupère les qualificateurs modifiés stockés dans l’espace de noms localisé des paramètres régionaux de la connexion actuelle.</span><span class="sxs-lookup"><span data-stu-id="d256e-116">If set, the function retrieves the amended qualifiers stored in the localized namespace of the current connection's locale.</span></span> <br/> <span data-ttu-id="d256e-117">Si la valeur n’est pas définie, la fonction récupère uniquement les qualificateurs stockés dans l’espace de noms immédiat.</span><span class="sxs-lookup"><span data-stu-id="d256e-117">If not set, the function retrieves only the qualifiers stored in the immediate namespace.</span></span> |
| `WBEM_FLAG_DEEP` | <span data-ttu-id="d256e-118">0</span><span class="sxs-lookup"><span data-stu-id="d256e-118">0</span></span> | <span data-ttu-id="d256e-119">L’énumération comprend toutes les sous-classes de la hiérarchie, mais pas cette classe.</span><span class="sxs-lookup"><span data-stu-id="d256e-119">The enumeration includes all subclasses in the hierarchy, but not this class.</span></span> |
| `WBEM_FLAG_SHALLOW` | <span data-ttu-id="d256e-120">1</span><span class="sxs-lookup"><span data-stu-id="d256e-120">1</span></span> | <span data-ttu-id="d256e-121">L’énumération inclut uniquement des instances pures de cette classe et exclut toutes les instances des sous-classes qui fournissent des propriétés introuvables dans cette classe.</span><span class="sxs-lookup"><span data-stu-id="d256e-121">The enumeration includes only pure instances of this class and excludes all instances of subclasses that supply properties not found in this class.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="d256e-122">0x10</span><span class="sxs-lookup"><span data-stu-id="d256e-122">0x10</span></span> | <span data-ttu-id="d256e-123">L’indicateur provoque un appel semi-synchrone.</span><span class="sxs-lookup"><span data-stu-id="d256e-123">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="d256e-124">0x20</span><span class="sxs-lookup"><span data-stu-id="d256e-124">0x20</span></span> | <span data-ttu-id="d256e-125">La fonction retourne un énumérateur avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="d256e-125">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="d256e-126">En général, les énumérateurs avant uniquement sont plus rapides et utilisent moins de mémoire que les énumérateurs conventionnels, mais ils n’autorisent pas les appels à [cloner](clone.md).</span><span class="sxs-lookup"><span data-stu-id="d256e-126">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |
| `WBEM_FLAG_BIDIRECTIONAL` | <span data-ttu-id="d256e-127">0</span><span class="sxs-lookup"><span data-stu-id="d256e-127">0</span></span> | <span data-ttu-id="d256e-128">WMI conserve les pointeurs vers les objets de l’énumération jusqu’à ce qu’ils soient libérés.</span><span class="sxs-lookup"><span data-stu-id="d256e-128">WMI retains pointers to objects in the enumeration until they are released.</span></span> |

<span data-ttu-id="d256e-129">Les indicateurs recommandés sont `WBEM_FLAG_RETURN_IMMEDIATELY` et `WBEM_FLAG_FORWARD_ONLY` pour des performances optimales.</span><span class="sxs-lookup"><span data-stu-id="d256e-129">The recommended flags are `WBEM_FLAG_RETURN_IMMEDIATELY` and `WBEM_FLAG_FORWARD_ONLY` for best performance.</span></span>

`pCtx`\
<span data-ttu-id="d256e-130">dans En général, cette valeur `null`est.</span><span class="sxs-lookup"><span data-stu-id="d256e-130">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="d256e-131">Dans le cas contraire, il s’agit d’un pointeur vers une instance [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) qui peut être utilisée par le fournisseur qui fournit les classes demandées.</span><span class="sxs-lookup"><span data-stu-id="d256e-131">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppEnum`\
<span data-ttu-id="d256e-132">à Reçoit le pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="d256e-132">[out] Receives the pointer to the enumerator.</span></span>

`authLevel`\
<span data-ttu-id="d256e-133">dans Niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="d256e-133">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="d256e-134">dans Niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="d256e-134">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="d256e-135">dans Pointeur vers un objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) qui représente l’espace de noms actuel.</span><span class="sxs-lookup"><span data-stu-id="d256e-135">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="d256e-136">dans Nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d256e-136">[in] The user name.</span></span> <span data-ttu-id="d256e-137">Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="d256e-137">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="d256e-138">dans Mot de passe.</span><span class="sxs-lookup"><span data-stu-id="d256e-138">[in] The password.</span></span> <span data-ttu-id="d256e-139">Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="d256e-139">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="d256e-140">dans Nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d256e-140">[in] The domain name of the user.</span></span> <span data-ttu-id="d256e-141">Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="d256e-141">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="d256e-142">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d256e-142">Return value</span></span>

<span data-ttu-id="d256e-143">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="d256e-143">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="d256e-144">Constante</span><span class="sxs-lookup"><span data-stu-id="d256e-144">Constant</span></span>  |<span data-ttu-id="d256e-145">Valeur</span><span class="sxs-lookup"><span data-stu-id="d256e-145">Value</span></span>  |<span data-ttu-id="d256e-146">Description</span><span class="sxs-lookup"><span data-stu-id="d256e-146">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="d256e-147">0x80041003</span><span class="sxs-lookup"><span data-stu-id="d256e-147">0x80041003</span></span> | <span data-ttu-id="d256e-148">L’utilisateur n’a pas l’autorisation d’afficher une ou plusieurs des classes que la fonction peut retourner.</span><span class="sxs-lookup"><span data-stu-id="d256e-148">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="d256e-149">0x80041001</span><span class="sxs-lookup"><span data-stu-id="d256e-149">0x80041001</span></span> | <span data-ttu-id="d256e-150">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="d256e-150">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="d256e-151">0x80041010</span><span class="sxs-lookup"><span data-stu-id="d256e-151">0x80041010</span></span> | <span data-ttu-id="d256e-152">`strSuperClass` n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="d256e-152">`strSuperClass` does not exist.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="d256e-153">0x80041008</span><span class="sxs-lookup"><span data-stu-id="d256e-153">0x80041008</span></span> | <span data-ttu-id="d256e-154">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="d256e-154">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="d256e-155">0x80041006</span><span class="sxs-lookup"><span data-stu-id="d256e-155">0x80041006</span></span> | <span data-ttu-id="d256e-156">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="d256e-156">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="d256e-157">0x80041033</span><span class="sxs-lookup"><span data-stu-id="d256e-157">0x80041033</span></span> | <span data-ttu-id="d256e-158">WMI a probablement été arrêté et redémarré.</span><span class="sxs-lookup"><span data-stu-id="d256e-158">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="d256e-159">Appelez à nouveau [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="d256e-159">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="d256e-160">0x80041015</span><span class="sxs-lookup"><span data-stu-id="d256e-160">0x80041015</span></span> | <span data-ttu-id="d256e-161">Le lien de l’appel de procédure distante (RPC) entre le processus en cours et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="d256e-161">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
|`WBEM_S_NO_ERROR` | <span data-ttu-id="d256e-162">0</span><span class="sxs-lookup"><span data-stu-id="d256e-162">0</span></span> | <span data-ttu-id="d256e-163">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="d256e-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="d256e-164">Notes</span><span class="sxs-lookup"><span data-stu-id="d256e-164">Remarks</span></span>

<span data-ttu-id="d256e-165">Cette fonction encapsule un appel à la méthode [IWbemServices :: CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) .</span><span class="sxs-lookup"><span data-stu-id="d256e-165">This function wraps a call to the [IWbemServices::CreateClassEnum](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-createclassenum) method.</span></span>

<span data-ttu-id="d256e-166">Si l’appel de fonction échoue, vous pouvez obtenir des informations supplémentaires sur l’erreur en appelant la fonction [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="d256e-166">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="d256e-167">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d256e-167">Requirements</span></span>

<span data-ttu-id="d256e-168">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d256e-168">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d256e-169">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="d256e-169">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="d256e-170">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="d256e-170">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d256e-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d256e-171">See also</span></span>

- [<span data-ttu-id="d256e-172">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="d256e-172">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
