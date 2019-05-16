---
title: Execnotificationquerywmi, fonction (référence des API non managées)
description: Execnotificationquerywmi, de la fonction exécute une requête pour recevoir des événements.
ms.date: 11/06/2017
api_name:
- ExecNotificationQueryWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ExecNotificationQueryWmi
helpviewer_keywords:
- ExecNotificationQueryWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa2233bab82f3cd4d1bbcb59f5714c6e4dc91aa5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636560"
---
# <a name="execnotificationquerywmi-function"></a><span data-ttu-id="38826-103">ExecNotificationQueryWmi, fonction</span><span class="sxs-lookup"><span data-stu-id="38826-103">ExecNotificationQueryWmi function</span></span>

<span data-ttu-id="38826-104">Exécute une requête pour recevoir des événements.</span><span class="sxs-lookup"><span data-stu-id="38826-104">Executes a query to receive events.</span></span> <span data-ttu-id="38826-105">L’appel retourne immédiatement, et l’appelant peut interroger l’énumérateur retourné pour les événements dès leur arrivée.</span><span class="sxs-lookup"><span data-stu-id="38826-105">The call returns immediately, and the caller can poll the returned enumerator for events as they arrive.</span></span> <span data-ttu-id="38826-106">Libération de l’énumérateur retourné annule la requête.</span><span class="sxs-lookup"><span data-stu-id="38826-106">Releasing the returned enumerator cancels the query.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="38826-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38826-107">Syntax</span></span>

```cpp
HRESULT ExecNotificationQueryWmi (
   [in] BSTR                    strQueryLanguage,
   [in] BSTR                    strQuery,
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

## <a name="parameters"></a><span data-ttu-id="38826-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="38826-108">Parameters</span></span>

`strQueryLanguage`\
<span data-ttu-id="38826-109">[in] Chaîne avec le langage de requête valide pris en charge par la gestion de Windows.</span><span class="sxs-lookup"><span data-stu-id="38826-109">[in] A string with the valid query language supported by Windows Management.</span></span> <span data-ttu-id="38826-110">Il doit être « WQL », l’acronyme de langage de requête WMI.</span><span class="sxs-lookup"><span data-stu-id="38826-110">It must be "WQL", the acronym for WMI Query Language.</span></span>

`strQuery`\
<span data-ttu-id="38826-111">[in] Le texte de la requête.</span><span class="sxs-lookup"><span data-stu-id="38826-111">[in] The text of the query.</span></span> <span data-ttu-id="38826-112">Ce paramètre ne peut pas être `null`.</span><span class="sxs-lookup"><span data-stu-id="38826-112">This parameter cannot be `null`.</span></span>

`lFlags`\
<span data-ttu-id="38826-113">[in] Une combinaison des deux indicateurs suivants qui affectent le comportement de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="38826-113">[in] A combination of the following two flags that affect the behavior of this function.</span></span> <span data-ttu-id="38826-114">Ces valeurs sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code.</span><span class="sxs-lookup"><span data-stu-id="38826-114">These values are defined in the *WbemCli.h* header file, or you can define them as constants in your code.</span></span>

| <span data-ttu-id="38826-115">Constante</span><span class="sxs-lookup"><span data-stu-id="38826-115">Constant</span></span> | <span data-ttu-id="38826-116">Value</span><span class="sxs-lookup"><span data-stu-id="38826-116">Value</span></span>  | <span data-ttu-id="38826-117">Description</span><span class="sxs-lookup"><span data-stu-id="38826-117">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="38826-118">0x10</span><span class="sxs-lookup"><span data-stu-id="38826-118">0x10</span></span> | <span data-ttu-id="38826-119">L’indicateur provoque un appel semi-synchrone.</span><span class="sxs-lookup"><span data-stu-id="38826-119">The flag causes a semisynchronous call.</span></span> <span data-ttu-id="38826-120">Si cet indicateur n’est pas défini, l’appel échoue.</span><span class="sxs-lookup"><span data-stu-id="38826-120">If this flag is not set, the call fails.</span></span> <span data-ttu-id="38826-121">Il s’agit, car les événements sont reçus en continu, ce qui signifie que l’utilisateur doit interroger l’énumérateur retourné.</span><span class="sxs-lookup"><span data-stu-id="38826-121">This is because events are received continuously, which means the user must poll the returned enumerator.</span></span> <span data-ttu-id="38826-122">Cet appel de blocage indéfiniment rend qui est impossible.</span><span class="sxs-lookup"><span data-stu-id="38826-122">Blocking this call indefinitely makes that impossible.</span></span> |
| `WBEM_FLAG_FORWARD_ONLY` | <span data-ttu-id="38826-123">0x20</span><span class="sxs-lookup"><span data-stu-id="38826-123">0x20</span></span> | <span data-ttu-id="38826-124">La fonction retourne un énumérateur avant uniquement.</span><span class="sxs-lookup"><span data-stu-id="38826-124">The function returns a forward-only enumerator.</span></span> <span data-ttu-id="38826-125">En règle générale, les énumérateurs avant uniquement sont plus rapides et utilisent moins de mémoire que les énumérateurs classiques, mais ils ne permettent pas d’appels à [Clone](clone.md).</span><span class="sxs-lookup"><span data-stu-id="38826-125">Typically, forward-only enumerators are faster and use less memory than conventional enumerators, but they do not allow calls to [Clone](clone.md).</span></span> |

`pCtx`\
<span data-ttu-id="38826-126">[in] En règle générale, cette valeur est `null`.</span><span class="sxs-lookup"><span data-stu-id="38826-126">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="38826-127">Sinon, il est un pointeur vers un [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance qui peut être utilisé par le fournisseur qui fournit les événements demandés.</span><span class="sxs-lookup"><span data-stu-id="38826-127">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested events.</span></span>

`ppEnum`\
<span data-ttu-id="38826-128">[out] Si aucune erreur ne se produit, reçoit le pointeur vers l’énumérateur qui permet à l’appelant récupérer les instances dans le jeu de résultats de la requête.</span><span class="sxs-lookup"><span data-stu-id="38826-128">[out] If no error occurs, receives the pointer to the enumerator that allows the caller to retrieve the instances in the query's result set.</span></span> <span data-ttu-id="38826-129">Consultez le [notes](#remarks) section pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="38826-129">See the [Remarks](#remarks) section for more information.</span></span>

`authLevel`\
<span data-ttu-id="38826-130">[in] Le niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="38826-130">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="38826-131">[in] Le niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="38826-131">[in] The impersonation level.</span></span>

`pCurrentNamespace`\
<span data-ttu-id="38826-132">[in] Un pointeur vers un [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) objet qui représente l’espace de noms actuel.</span><span class="sxs-lookup"><span data-stu-id="38826-132">[in] A pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object that represents the current namespace.</span></span>

`strUser`\
<span data-ttu-id="38826-133">[in] Le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38826-133">[in] The user name.</span></span> <span data-ttu-id="38826-134">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="38826-134">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="38826-135">[in] Le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="38826-135">[in] The password.</span></span> <span data-ttu-id="38826-136">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="38826-136">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="38826-137">[in] Le nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="38826-137">[in] The domain name of the user.</span></span> <span data-ttu-id="38826-138">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="38826-138">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="38826-139">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="38826-139">Return value</span></span>

<span data-ttu-id="38826-140">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="38826-140">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="38826-141">Constante</span><span class="sxs-lookup"><span data-stu-id="38826-141">Constant</span></span>  |<span data-ttu-id="38826-142">Value</span><span class="sxs-lookup"><span data-stu-id="38826-142">Value</span></span>  |<span data-ttu-id="38826-143">Description</span><span class="sxs-lookup"><span data-stu-id="38826-143">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="38826-144">0x80041003</span><span class="sxs-lookup"><span data-stu-id="38826-144">0x80041003</span></span> | <span data-ttu-id="38826-145">L’utilisateur n’a pas l’autorisation d’afficher un ou plusieurs des classes qui la fonction peut retourner.</span><span class="sxs-lookup"><span data-stu-id="38826-145">The user does not have permission to view one or more of the classes that the function can return.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="38826-146">0x80041001</span><span class="sxs-lookup"><span data-stu-id="38826-146">0x80041001</span></span> | <span data-ttu-id="38826-147">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="38826-147">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="38826-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="38826-148">0x80041008</span></span> | <span data-ttu-id="38826-149">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="38826-149">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="38826-150">0x80041010</span><span class="sxs-lookup"><span data-stu-id="38826-150">0x80041010</span></span> | <span data-ttu-id="38826-151">La requête spécifie une classe qui n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="38826-151">The query specifies a class that does not exist.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_PRECISE` | <span data-ttu-id="38826-152">0x80042002</span><span class="sxs-lookup"><span data-stu-id="38826-152">0x80042002</span></span> | <span data-ttu-id="38826-153">Trop de précision dans la livraison d’événements a été demandée.</span><span class="sxs-lookup"><span data-stu-id="38826-153">Too much precision in delivery of events has been requested.</span></span> <span data-ttu-id="38826-154">Une plus grande tolérance d’interrogation doit être spécifiée.</span><span class="sxs-lookup"><span data-stu-id="38826-154">A larger polling tolerance must be specified.</span></span> |
| `WBEMESS_E_REGISTRATION_TOO_BROAD` | <span data-ttu-id="38826-155">0x80042001</span><span class="sxs-lookup"><span data-stu-id="38826-155">0x80042001</span></span> | <span data-ttu-id="38826-156">La requête demande plus d’informations que celles d’administration de Windows.</span><span class="sxs-lookup"><span data-stu-id="38826-156">The query requests more information than Windows Management can provide.</span></span> <span data-ttu-id="38826-157">Cela `HRESULT` est retournée lorsqu’une requête d’événement entraîne une demande d’interrogation de tous les objets dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="38826-157">This `HRESULT` is returned when an event query results in a request to poll all objects in a namespace.</span></span> |
| `WBEM_E_INVALID_QUERY` | <span data-ttu-id="38826-158">0x80041017</span><span class="sxs-lookup"><span data-stu-id="38826-158">0x80041017</span></span> | <span data-ttu-id="38826-159">La requête a dû à une erreur de syntaxe.</span><span class="sxs-lookup"><span data-stu-id="38826-159">The query had a syntax error.</span></span> |
| `WBEM_E_INVALID_QUERY_TYPE` | <span data-ttu-id="38826-160">0x80041018</span><span class="sxs-lookup"><span data-stu-id="38826-160">0x80041018</span></span> | <span data-ttu-id="38826-161">Le langage de requête demandé n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="38826-161">The requested query language is not supported.</span></span> |
| `WBEM_E_QUOTA_VIOLATION` | <span data-ttu-id="38826-162">0x8004106c</span><span class="sxs-lookup"><span data-stu-id="38826-162">0x8004106c</span></span> | <span data-ttu-id="38826-163">La requête est trop complexe.</span><span class="sxs-lookup"><span data-stu-id="38826-163">The query is too complex.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="38826-164">0x80041006</span><span class="sxs-lookup"><span data-stu-id="38826-164">0x80041006</span></span> | <span data-ttu-id="38826-165">Mémoire est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="38826-165">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="38826-166">0x80041033</span><span class="sxs-lookup"><span data-stu-id="38826-166">0x80041033</span></span> | <span data-ttu-id="38826-167">WMI s’est probablement arrêté et redémarrage.</span><span class="sxs-lookup"><span data-stu-id="38826-167">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="38826-168">Appelez [ConnectServerWmi](connectserverwmi.md) à nouveau.</span><span class="sxs-lookup"><span data-stu-id="38826-168">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="38826-169">0x80041015</span><span class="sxs-lookup"><span data-stu-id="38826-169">0x80041015</span></span> | <span data-ttu-id="38826-170">Le lien remote procedure call (RPC) entre les processus en cours et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="38826-170">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_E_UNPARSABLE_QUERY` | <span data-ttu-id="38826-171">0x80041058</span><span class="sxs-lookup"><span data-stu-id="38826-171">0x80041058</span></span> | <span data-ttu-id="38826-172">La requête ne peut pas être analysée.</span><span class="sxs-lookup"><span data-stu-id="38826-172">The query cannot be parsed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="38826-173">0</span><span class="sxs-lookup"><span data-stu-id="38826-173">0</span></span> | <span data-ttu-id="38826-174">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="38826-174">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="38826-175">Notes</span><span class="sxs-lookup"><span data-stu-id="38826-175">Remarks</span></span>

<span data-ttu-id="38826-176">Cette fonction encapsule un appel à la [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) (méthode).</span><span class="sxs-lookup"><span data-stu-id="38826-176">This function wraps a call to the [IWbemServices::ExecNotificationQuery](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-execnotificationquery) method.</span></span>

<span data-ttu-id="38826-177">Après le retour de la fonction, l’appelant transmet régulièrement retourné `ppEnum` de l’objet à la [suivant](next.md) (fonction) pour vérifier si tous les événements sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="38826-177">After the function returns, the caller periodically passes the returned `ppEnum` object to the [Next](next.md) function to see if any events are available.</span></span>

<span data-ttu-id="38826-178">Il existe des limites au nombre de `AND` et `OR` mots clés qui peuvent être utilisées dans les requêtes WQL.</span><span class="sxs-lookup"><span data-stu-id="38826-178">There are limits to the number of `AND` and `OR` keywords that can be used in WQL queries.</span></span> <span data-ttu-id="38826-179">Grand nombre de mots clés WQL utilisés dans une requête complexe peut provoquer de WMI retourner le `WBEM_E_QUOTA_VIOLATION` (ou 0x8004106c) code d’erreur comme un `HRESULT` valeur.</span><span class="sxs-lookup"><span data-stu-id="38826-179">Large numbers of WQL keywords used in a complex query can cause WMI to return the `WBEM_E_QUOTA_VIOLATION` (or 0x8004106c) error code as an `HRESULT` value.</span></span> <span data-ttu-id="38826-180">La limite des mots clés WQL dépend de la complexité de la requête est.</span><span class="sxs-lookup"><span data-stu-id="38826-180">The limit of WQL keywords depends on how complex the query is.</span></span>

<span data-ttu-id="38826-181">Si l’appel de fonction échoue, vous pouvez obtenir des informations d’erreur supplémentaires en appelant le [GetErrorInfo](geterrorinfo.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="38826-181">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="38826-182">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="38826-182">Requirements</span></span>

<span data-ttu-id="38826-183">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38826-183">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="38826-184">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="38826-184">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="38826-185">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="38826-185">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="38826-186">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38826-186">See also</span></span>

- [<span data-ttu-id="38826-187">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="38826-187">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
