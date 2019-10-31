---
title: Fonction ConnectServerWmi (référence des API non managées)
description: La fonction ConnectServerWmi utilise DCOM pour créer une connexion à un espace de noms WMI.
ms.date: 11/06/2017
api_name:
- ConnectServerWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- ConnectServerWmi
helpviewer_keywords:
- ConnectServerWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 25a73060ed242fd0e77042cd0ea9618b9b27250f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128692"
---
# <a name="connectserverwmi-function"></a><span data-ttu-id="ec837-103">ConnectServerWmi fonction)</span><span class="sxs-lookup"><span data-stu-id="ec837-103">ConnectServerWmi function</span></span>

<span data-ttu-id="ec837-104">Crée une connexion via DCOM à un espace de noms WMI sur un ordinateur spécifié.</span><span class="sxs-lookup"><span data-stu-id="ec837-104">Creates a connection through DCOM to a WMI namespace on a specified computer.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="ec837-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ec837-105">Syntax</span></span>

```cpp
HRESULT ConnectServerWmi (
   [in] BSTR               strNetworkResource,
   [in] BSTR               strUser,
   [in] BSTR               strPassword,
   [in] BSTR               strLocale,
   [in] long               lSecurityFlags,
   [in] BSTR               strAuthority,
   [in] IWbemContext*      pCtx,
   [out] IWbemServices**   ppNamespace,
   [in] DWORD              impLevel,
   [in] DWORD              authLevel
);
```

## <a name="parameters"></a><span data-ttu-id="ec837-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec837-106">Parameters</span></span>

`strNetworkResource`\
<span data-ttu-id="ec837-107">dans Pointeur vers un `BSTR` valide qui contient le chemin d’accès de l’objet de l’espace de noms WMI correct.</span><span class="sxs-lookup"><span data-stu-id="ec837-107">[in] Pointer to a valid `BSTR` that contains the object path of the correct WMI namespace.</span></span> <span data-ttu-id="ec837-108">Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ec837-108">See the [Remarks](#remarks) section for more information.</span></span>

`strUser`\
<span data-ttu-id="ec837-109">dans Pointeur vers un `BSTR` valide qui contient le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ec837-109">[in] A pointer to a valid `BSTR` that contains the user name.</span></span> <span data-ttu-id="ec837-110">Une valeur `null` indique le contexte de sécurité actuel.</span><span class="sxs-lookup"><span data-stu-id="ec837-110">A `null` value indicates the current security context.</span></span> <span data-ttu-id="ec837-111">Si l’utilisateur provient d’un domaine différent de celui en cours, `strUser` peut également contenir le domaine et le nom d’utilisateur séparés par une barre oblique inverse.</span><span class="sxs-lookup"><span data-stu-id="ec837-111">If the user is from a different domain than the current one, `strUser` can also contain the domain and user name separated by a backslash.</span></span> <span data-ttu-id="ec837-112">`strUser` peut également être au format UPN (user principal name), tel que `userName@domainName`.</span><span class="sxs-lookup"><span data-stu-id="ec837-112">`strUser` can also be in user principal name (UPN) format, such as `userName@domainName`.</span></span> <span data-ttu-id="ec837-113">Pour plus d’informations, consultez la section [Notes](#remarks) .</span><span class="sxs-lookup"><span data-stu-id="ec837-113">See the [Remarks](#remarks) section for more information.</span></span>

`strPassword`\
<span data-ttu-id="ec837-114">dans Pointeur vers un `BSTR` valide qui contient le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ec837-114">[in] A pointer to a valid `BSTR` that contains the password.</span></span> <span data-ttu-id="ec837-115">`null` indique le contexte de sécurité actuel.</span><span class="sxs-lookup"><span data-stu-id="ec837-115">A `null` indicates the current security context.</span></span> <span data-ttu-id="ec837-116">Une chaîne vide ("") indique un mot de passe de longueur nulle valide.</span><span class="sxs-lookup"><span data-stu-id="ec837-116">An empty string ("") indicates a valid zero-length password.</span></span>

`strLocale`\
<span data-ttu-id="ec837-117">dans Pointeur vers un `BSTR` valide qui indique les paramètres régionaux corrects pour la récupération d’informations.</span><span class="sxs-lookup"><span data-stu-id="ec837-117">[in] A pointer to a valid `BSTR` that indicates the correct locale for information retrieval.</span></span> <span data-ttu-id="ec837-118">Pour les identificateurs de paramètres régionaux Microsoft, le format de la chaîne est « MS\_*xxx*», où *xxx* est une chaîne au format hexadécimal qui indique l’identificateur de paramètres régionaux (LCID).</span><span class="sxs-lookup"><span data-stu-id="ec837-118">For Microsoft locale identifiers, the format of the string is "MS\_*xxx*", where *xxx* is a string in hexadecimal form that indicates the locale identifier (LCID).</span></span> <span data-ttu-id="ec837-119">Si des paramètres régionaux non valides sont spécifiés, la méthode retourne `WBEM_E_INVALID_PARAMETER` sauf sur Windows 7, où les paramètres régionaux par défaut du serveur sont utilisés à la place.</span><span class="sxs-lookup"><span data-stu-id="ec837-119">If an invalid locale is specified, the method returns `WBEM_E_INVALID_PARAMETER` except on Windows 7, where the default locale of the server is used instead.</span></span> <span data-ttu-id="ec837-120">Si « NULL1 », les paramètres régionaux actuels sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="ec837-120">If \`null1, the current locale is used.</span></span>

`lSecurityFlags`\
<span data-ttu-id="ec837-121">dans Indicateurs à passer à la méthode `ConnectServerWmi`.</span><span class="sxs-lookup"><span data-stu-id="ec837-121">[in] Flags to pass to the `ConnectServerWmi` method.</span></span> <span data-ttu-id="ec837-122">La valeur zéro (0) pour ce paramètre entraîne l’appel à `ConnectServerWmi` retourner uniquement après l’établissement d’une connexion au serveur.</span><span class="sxs-lookup"><span data-stu-id="ec837-122">A value of zero (0) for this parameter results in the call to `ConnectServerWmi` returning only after a connection to the server is established.</span></span> <span data-ttu-id="ec837-123">Cela peut empêcher une application de répondre indéfiniment en cas de rupture du serveur.</span><span class="sxs-lookup"><span data-stu-id="ec837-123">This could result in an application not responding indefinitely if the server is broken.</span></span> <span data-ttu-id="ec837-124">Les autres valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="ec837-124">The other valid values are:</span></span>

| <span data-ttu-id="ec837-125">Constante</span><span class="sxs-lookup"><span data-stu-id="ec837-125">Constant</span></span>  | <span data-ttu-id="ec837-126">valeur</span><span class="sxs-lookup"><span data-stu-id="ec837-126">Value</span></span>  | <span data-ttu-id="ec837-127">Description</span><span class="sxs-lookup"><span data-stu-id="ec837-127">Description</span></span>  |
|---------|---------|---------|
| `CONNECT_REPOSITORY_ONLY` | <span data-ttu-id="ec837-128">0x40</span><span class="sxs-lookup"><span data-stu-id="ec837-128">0x40</span></span> | <span data-ttu-id="ec837-129">Réservé à un usage interne.</span><span class="sxs-lookup"><span data-stu-id="ec837-129">Reserved for internal use.</span></span> <span data-ttu-id="ec837-130">Ne pas utiliser.</span><span class="sxs-lookup"><span data-stu-id="ec837-130">Do not use.</span></span> |
| `WBEM_FLAG_CONNECT_USE_MAX_WAIT` | <span data-ttu-id="ec837-131">0x80</span><span class="sxs-lookup"><span data-stu-id="ec837-131">0x80</span></span> | <span data-ttu-id="ec837-132">`ConnectServerWmi` retourne en deux minutes ou moins.</span><span class="sxs-lookup"><span data-stu-id="ec837-132">`ConnectServerWmi` returns in two minutes or less.</span></span> |

`strAuthority`\
<span data-ttu-id="ec837-133">dans Nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="ec837-133">[in] The domain name of the user.</span></span> <span data-ttu-id="ec837-134">Il peut afficher les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ec837-134">It can have the following values:</span></span>

| <span data-ttu-id="ec837-135">valeur</span><span class="sxs-lookup"><span data-stu-id="ec837-135">Value</span></span> | <span data-ttu-id="ec837-136">Description</span><span class="sxs-lookup"><span data-stu-id="ec837-136">Description</span></span> |
|---------|---------|
| <span data-ttu-id="ec837-137">vide</span><span class="sxs-lookup"><span data-stu-id="ec837-137">blank</span></span> | <span data-ttu-id="ec837-138">L’authentification NTLM est utilisée et le domaine NTLM de l’utilisateur actuel est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ec837-138">NTLM authentication is used, and the NTLM domain of the current user is used.</span></span> <span data-ttu-id="ec837-139">Si `strUser` spécifie le domaine (emplacement recommandé), il ne doit pas être spécifié ici.</span><span class="sxs-lookup"><span data-stu-id="ec837-139">If `strUser` specifies the domain (the recommended location), it must not be specified here.</span></span> <span data-ttu-id="ec837-140">La fonction retourne `WBEM_E_INVALID_PARAMETER` si vous spécifiez le domaine dans les deux paramètres.</span><span class="sxs-lookup"><span data-stu-id="ec837-140">The function returns `WBEM_E_INVALID_PARAMETER` if you specify the domain in both parameters.</span></span> |
| <span data-ttu-id="ec837-141">Kerberos :*nom principal*</span><span class="sxs-lookup"><span data-stu-id="ec837-141">Kerberos:*principal name*</span></span> | <span data-ttu-id="ec837-142">L’authentification Kerberos est utilisée, et ce paramètre contient un nom de principal Kerberos.</span><span class="sxs-lookup"><span data-stu-id="ec837-142">Kerberos authentication is used, and this parameter contains a Kerberos principal name.</span></span> |
| <span data-ttu-id="ec837-143">NTLMDOMAIN :*nom de domaine*</span><span class="sxs-lookup"><span data-stu-id="ec837-143">NTLMDOMAIN:*domain name*</span></span> | <span data-ttu-id="ec837-144">L’authentification NT LAN Manager est utilisée, et ce paramètre contient un nom de domaine NTLM.</span><span class="sxs-lookup"><span data-stu-id="ec837-144">NT LAN Manager authentication is used, and this parameter contains an NTLM domain name.</span></span> |

`pCtx`\
<span data-ttu-id="ec837-145">dans En général, ce paramètre est `null`.</span><span class="sxs-lookup"><span data-stu-id="ec837-145">[in] Typically, this parameter is `null`.</span></span> <span data-ttu-id="ec837-146">Dans le cas contraire, il s’agit d’un pointeur vers un objet [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) requis par un ou plusieurs fournisseurs de classes dynamiques.</span><span class="sxs-lookup"><span data-stu-id="ec837-146">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) object required by one or more dynamic class providers.</span></span>

`ppNamespace`\
<span data-ttu-id="ec837-147">à Quand la fonction retourne une valeur, reçoit un pointeur vers un objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) lié à l’espace de noms spécifié.</span><span class="sxs-lookup"><span data-stu-id="ec837-147">[out] When the function returns, receives a pointer to an [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object bound to the specified namespace.</span></span> <span data-ttu-id="ec837-148">Elle est définie pour pointer vers `null` lorsqu’il y a une erreur.</span><span class="sxs-lookup"><span data-stu-id="ec837-148">It is set to point to `null` when there is an error.</span></span>

`impLevel`\
<span data-ttu-id="ec837-149">dans Niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="ec837-149">[in] The impersonation level.</span></span>

`authLevel`\
<span data-ttu-id="ec837-150">dans Niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="ec837-150">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="ec837-151">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ec837-151">Return value</span></span>

<span data-ttu-id="ec837-152">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="ec837-152">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="ec837-153">Constante</span><span class="sxs-lookup"><span data-stu-id="ec837-153">Constant</span></span>  |<span data-ttu-id="ec837-154">valeur</span><span class="sxs-lookup"><span data-stu-id="ec837-154">Value</span></span>  |<span data-ttu-id="ec837-155">Description</span><span class="sxs-lookup"><span data-stu-id="ec837-155">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="ec837-156">0x80041001</span><span class="sxs-lookup"><span data-stu-id="ec837-156">0x80041001</span></span> | <span data-ttu-id="ec837-157">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ec837-157">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="ec837-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="ec837-158">0x80041008</span></span> | <span data-ttu-id="ec837-159">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="ec837-159">A parameter is not valid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="ec837-160">0x80041006</span><span class="sxs-lookup"><span data-stu-id="ec837-160">0x80041006</span></span> | <span data-ttu-id="ec837-161">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="ec837-161">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="ec837-162">0</span><span class="sxs-lookup"><span data-stu-id="ec837-162">0</span></span> | <span data-ttu-id="ec837-163">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="ec837-163">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="ec837-164">Notes</span><span class="sxs-lookup"><span data-stu-id="ec837-164">Remarks</span></span>

<span data-ttu-id="ec837-165">Cette fonction encapsule un appel à la méthode [IWbemLocator :: ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) .</span><span class="sxs-lookup"><span data-stu-id="ec837-165">This function wraps a call to the [IWbemLocator::ConnectServer](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemlocator-connectserver) method.</span></span>

<span data-ttu-id="ec837-166">Pour un accès local à l’espace de noms par défaut, `strNetworkResource` peut être un chemin d’objet simple : « root\default » ou «\\.\root\default ».</span><span class="sxs-lookup"><span data-stu-id="ec837-166">For local access to the default namespace, `strNetworkResource` can be a simple object path: "root\default" or "\\.\root\default".</span></span> <span data-ttu-id="ec837-167">Pour accéder à l’espace de noms par défaut sur un ordinateur distant à l’aide de COM ou de la mise en réseau compatible avec Microsoft, incluez le nom de l’ordinateur : «\\myserver\root\default ».</span><span class="sxs-lookup"><span data-stu-id="ec837-167">For access to the default namespace on a remote computer using COM or Microsoft-compatible networking, include the computer name: "\\myserver\root\default".</span></span> <span data-ttu-id="ec837-168">Le nom de l’ordinateur peut également être un nom DNS ou une adresse IP.</span><span class="sxs-lookup"><span data-stu-id="ec837-168">The computer name also can be a DNS name or IP address.</span></span> <span data-ttu-id="ec837-169">La fonction `ConnectServerWmi` peut également se connecter à des ordinateurs exécutant IPv6 à l’aide d’une adresse IPv6.</span><span class="sxs-lookup"><span data-stu-id="ec837-169">The `ConnectServerWmi` function can also connect with computers running IPv6 using an IPv6 address.</span></span>

<span data-ttu-id="ec837-170">`strUser` ne peut pas être une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="ec837-170">`strUser` cannot be an empty string.</span></span> <span data-ttu-id="ec837-171">Si le domaine est spécifié dans `strAuthority`, il ne doit pas être également inclus dans `strUser`ou la fonction retourne `WBEM_E_INVALID_PARAMETER`.</span><span class="sxs-lookup"><span data-stu-id="ec837-171">If the domain is specified in `strAuthority`, it must not also be included in `strUser`, or the function returns `WBEM_E_INVALID_PARAMETER`.</span></span>

## <a name="requirements"></a><span data-ttu-id="ec837-172">spécifications</span><span class="sxs-lookup"><span data-stu-id="ec837-172">Requirements</span></span>

 <span data-ttu-id="ec837-173">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec837-173">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="ec837-174">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="ec837-174">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="ec837-175">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ec837-175">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="ec837-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec837-176">See also</span></span>

- [<span data-ttu-id="ec837-177">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="ec837-177">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
