---
title: Fonction PutInstanceWmi (référence des API non managées)
description: La fonction PutInstanceWmi crée ou met à jour une instance d’une classe existante.
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: b33f31d69c64ce520580c29f1014c058c78d0953
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127351"
---
# <a name="putinstancewmi-function"></a><span data-ttu-id="029ed-103">PutInstanceWmi fonction)</span><span class="sxs-lookup"><span data-stu-id="029ed-103">PutInstanceWmi function</span></span>

<span data-ttu-id="029ed-104">Crée ou met à jour une instance d’une classe existante.</span><span class="sxs-lookup"><span data-stu-id="029ed-104">Creates or updates an instance of an existing class.</span></span> <span data-ttu-id="029ed-105">L’instance est écrite dans le référentiel WMI.</span><span class="sxs-lookup"><span data-stu-id="029ed-105">The instance is written to the WMI repository.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="029ed-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="029ed-106">Syntax</span></span>

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="029ed-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="029ed-107">Parameters</span></span>

`pInst`\
<span data-ttu-id="029ed-108">dans Pointeur vers l’instance à écrire.</span><span class="sxs-lookup"><span data-stu-id="029ed-108">[in] A pointer to the instance to be written.</span></span>

`lFlags`\
<span data-ttu-id="029ed-109">dans Combinaison d’indicateurs qui affectent le comportement de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="029ed-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="029ed-110">Les valeurs suivantes sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="029ed-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="029ed-111">Constante</span><span class="sxs-lookup"><span data-stu-id="029ed-111">Constant</span></span>  |<span data-ttu-id="029ed-112">valeur</span><span class="sxs-lookup"><span data-stu-id="029ed-112">Value</span></span>  |<span data-ttu-id="029ed-113">Description</span><span class="sxs-lookup"><span data-stu-id="029ed-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="029ed-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="029ed-114">0x20000</span></span> | <span data-ttu-id="029ed-115">Si cette valeur est définie, WMI ne stocke pas de qualificateurs avec la version **modifiée** .</span><span class="sxs-lookup"><span data-stu-id="029ed-115">If set, WMI does not store any qualifiers with the **Amended** flavor.</span></span> <br> <span data-ttu-id="029ed-116">S’il n’est pas défini, il est supposé que cet objet n’est pas localisé, et tous les qualificateurs sont stockés avec cette instance.</span><span class="sxs-lookup"><span data-stu-id="029ed-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="029ed-117">0</span><span class="sxs-lookup"><span data-stu-id="029ed-117">0</span></span> | <span data-ttu-id="029ed-118">Créez l’instance si elle n’existe pas, ou remplacez-la si elle existe déjà.</span><span class="sxs-lookup"><span data-stu-id="029ed-118">Create the instance if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="029ed-119">1</span><span class="sxs-lookup"><span data-stu-id="029ed-119">1</span></span> | <span data-ttu-id="029ed-120">Mettez à jour l’instance.</span><span class="sxs-lookup"><span data-stu-id="029ed-120">Update the instance.</span></span> <span data-ttu-id="029ed-121">L’instance doit exister pour que l’appel réussisse.</span><span class="sxs-lookup"><span data-stu-id="029ed-121">The instance must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="029ed-122">2</span><span class="sxs-lookup"><span data-stu-id="029ed-122">2</span></span> | <span data-ttu-id="029ed-123">Créez l’instance.</span><span class="sxs-lookup"><span data-stu-id="029ed-123">Create the instance.</span></span> <span data-ttu-id="029ed-124">L’appel échoue si l’instance existe déjà.</span><span class="sxs-lookup"><span data-stu-id="029ed-124">The call fails if the instance already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="029ed-125">0x10</span><span class="sxs-lookup"><span data-stu-id="029ed-125">0x10</span></span> | <span data-ttu-id="029ed-126">L’indicateur provoque un appel semi-synchrone.</span><span class="sxs-lookup"><span data-stu-id="029ed-126">The flag causes a semisynchronous call.</span></span> |

`pCtx`\
<span data-ttu-id="029ed-127">dans En général, cette valeur est `null`.</span><span class="sxs-lookup"><span data-stu-id="029ed-127">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="029ed-128">Dans le cas contraire, il s’agit d’un pointeur vers une instance [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) qui peut être utilisée par le fournisseur qui fournit les classes demandées.</span><span class="sxs-lookup"><span data-stu-id="029ed-128">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="029ed-129">à Si `null`, ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="029ed-129">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="029ed-130">Si `lFlags` contient des `WBEM_FLAG_RETURN_IMMEDIATELY`, la fonction retourne immédiatement avec `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="029ed-130">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="029ed-131">Le paramètre `ppCallResult` reçoit un pointeur vers un nouvel objet [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .</span><span class="sxs-lookup"><span data-stu-id="029ed-131">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="029ed-132">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="029ed-132">Return value</span></span>

<span data-ttu-id="029ed-133">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="029ed-133">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="029ed-134">Constante</span><span class="sxs-lookup"><span data-stu-id="029ed-134">Constant</span></span>  |<span data-ttu-id="029ed-135">valeur</span><span class="sxs-lookup"><span data-stu-id="029ed-135">Value</span></span>  |<span data-ttu-id="029ed-136">Description</span><span class="sxs-lookup"><span data-stu-id="029ed-136">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="029ed-137">0x80041003</span><span class="sxs-lookup"><span data-stu-id="029ed-137">0x80041003</span></span> | <span data-ttu-id="029ed-138">L’utilisateur n’a pas l’autorisation de mettre à jour une instance de la classe spécifiée.</span><span class="sxs-lookup"><span data-stu-id="029ed-138">The user does not have permission to update an instance of the specified class.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="029ed-139">0x80041001</span><span class="sxs-lookup"><span data-stu-id="029ed-139">0x80041001</span></span> | <span data-ttu-id="029ed-140">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="029ed-140">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="029ed-141">0x80041010</span><span class="sxs-lookup"><span data-stu-id="029ed-141">0x80041010</span></span> | <span data-ttu-id="029ed-142">La classe prenant en charge cette instance n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="029ed-142">The class supporting this instance is not valid.</span></span> |
| `WBEM_E_ILLEGAL_NULL` | <span data-ttu-id="029ed-143">0x80041028</span><span class="sxs-lookup"><span data-stu-id="029ed-143">0x80041028</span></span> | <span data-ttu-id="029ed-144">une `null` a été spécifiée pour une propriété qui ne peut pas être `null`, telle que celle qui est marquée par un qualificateur **indexé** ou **not_null** .</span><span class="sxs-lookup"><span data-stu-id="029ed-144">a `null` was specified for a property that cannot be `null`, such as one that is marked by an **Indexed** or **Not_Null** qualifier.</span></span> |
| `WBEM_E_INVALID_OBJECT` | <span data-ttu-id="029ed-145">0x8004100f</span><span class="sxs-lookup"><span data-stu-id="029ed-145">0x8004100f</span></span> | <span data-ttu-id="029ed-146">L’instance spécifiée n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="029ed-146">The specified instance is not valid.</span></span> <span data-ttu-id="029ed-147">(Par exemple, l’appel de `PutInstanceWmi` avec une classe retourne cette valeur.)</span><span class="sxs-lookup"><span data-stu-id="029ed-147">(For example, calling `PutInstanceWmi` with a class returns this value.)</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="029ed-148">0x80041008</span><span class="sxs-lookup"><span data-stu-id="029ed-148">0x80041008</span></span> | <span data-ttu-id="029ed-149">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="029ed-149">A parameter is not valid.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="029ed-150">0x80041019</span><span class="sxs-lookup"><span data-stu-id="029ed-150">0x80041019</span></span> | <span data-ttu-id="029ed-151">L’indicateur de `WBEM_FLAG_CREATE_ONLY` a été spécifié, mais l’instance existe déjà.</span><span class="sxs-lookup"><span data-stu-id="029ed-151">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the instance already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="029ed-152">0x80041002</span><span class="sxs-lookup"><span data-stu-id="029ed-152">0x80041002</span></span> | <span data-ttu-id="029ed-153">`WBEM_FLAG_UPDATE_ONLY` a été spécifié dans `lFlags`, mais l’instance n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="029ed-153">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, but the instance does not exist.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="029ed-154">0x80041006</span><span class="sxs-lookup"><span data-stu-id="029ed-154">0x80041006</span></span> | <span data-ttu-id="029ed-155">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="029ed-155">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="029ed-156">0x80041033</span><span class="sxs-lookup"><span data-stu-id="029ed-156">0x80041033</span></span> | <span data-ttu-id="029ed-157">WMI a probablement été arrêté et redémarré.</span><span class="sxs-lookup"><span data-stu-id="029ed-157">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="029ed-158">Appelez à nouveau [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="029ed-158">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="029ed-159">0x80041015</span><span class="sxs-lookup"><span data-stu-id="029ed-159">0x80041015</span></span> | <span data-ttu-id="029ed-160">Le lien de l’appel de procédure distante (RPC) entre le processus en cours et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="029ed-160">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="029ed-161">0</span><span class="sxs-lookup"><span data-stu-id="029ed-161">0</span></span> | <span data-ttu-id="029ed-162">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="029ed-162">The function call was successful.</span></span> |

## <a name="remarks"></a><span data-ttu-id="029ed-163">Notes</span><span class="sxs-lookup"><span data-stu-id="029ed-163">Remarks</span></span>

<span data-ttu-id="029ed-164">Cette fonction encapsule un appel à la méthode [IWbemServices ::P utinstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) .</span><span class="sxs-lookup"><span data-stu-id="029ed-164">This function wraps a call to the [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance) method.</span></span>

<span data-ttu-id="029ed-165">La fonction `PutInstanceWmi` prend en charge la création d’instances et la mise à jour des instances de classes existantes uniquement.</span><span class="sxs-lookup"><span data-stu-id="029ed-165">The `PutInstanceWmi` function supports creating instances and updating instances of existing classes only.</span></span>  <span data-ttu-id="029ed-166">Selon la façon dont le paramètre `pCtx` est défini, une partie ou la totalité des propriétés de l’instance est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="029ed-166">Depending on how the `pCtx` parameter is set, either some or all of the properties of the instance are updated.</span></span>

<span data-ttu-id="029ed-167">Lorsque l’instance vers laquelle pointe `pInst` appartient à une sous-classe, la gestion Windows appelle tous les fournisseurs responsables des classes dont dérive la sous-classe.</span><span class="sxs-lookup"><span data-stu-id="029ed-167">When the instance pointed to by `pInst` belongs to a subclass, Windows Management calls all the providers responsible for the classes from which the subclass derives.</span></span> <span data-ttu-id="029ed-168">Tous ces fournisseurs doivent être correctement exécutés pour que la demande d' `PutInstanceWmi` d’origine aboutisse.</span><span class="sxs-lookup"><span data-stu-id="029ed-168">All of these providers must succeed for the original `PutInstanceWmi` request to succeed.</span></span> <span data-ttu-id="029ed-169">Le fournisseur qui prend en charge la classe de niveau supérieur dans la hiérarchie est appelé en premier.</span><span class="sxs-lookup"><span data-stu-id="029ed-169">The provider supporting the topmost class in the hierarchy is called first.</span></span> <span data-ttu-id="029ed-170">L’ordre appelant se poursuit avec la sous-classe de la classe la plus haute et s’exécute de haut en bas jusqu’à ce que la gestion de Windows atteigne le fournisseur de la classe propriétaire de l’instance désignée par `pInst`.</span><span class="sxs-lookup"><span data-stu-id="029ed-170">The calling order continues with the subclass of the topmost class and proceeds from top to bottom until Windows Management reaches the provider for the class owning the instance pointed to by `pInst`.</span></span>
<span data-ttu-id="029ed-171">La gestion Windows n’appelle pas les fournisseurs pour les classes enfants d’une instance.</span><span class="sxs-lookup"><span data-stu-id="029ed-171">Windows Management does not call the providers for any of the child classes of an instance.</span></span>

<span data-ttu-id="029ed-172">Quand une application doit mettre à jour une instance qui appartient à une hiérarchie de classes, le paramètre `pInst` doit pointer vers l’instance contenant les propriétés à modifier.</span><span class="sxs-lookup"><span data-stu-id="029ed-172">When an application must update an instance that belongs to a class hierarchy, the `pInst` parameter must point to the instance containing the properties to be modified.</span></span> <span data-ttu-id="029ed-173">Autrement dit, considérez une instance cible qui appartient à **ClassB**.</span><span class="sxs-lookup"><span data-stu-id="029ed-173">That is, consider a target instance that belongs to **ClassB**.</span></span> <span data-ttu-id="029ed-174">L’instance de **ClassB** dérive de **classa**, et **classa** définit la propriété **PROPA**.</span><span class="sxs-lookup"><span data-stu-id="029ed-174">The **ClassB** instance derives from **ClassA**, and **ClassA** defines the property **PropA**.</span></span> <span data-ttu-id="029ed-175">Si une application souhaite apporter une modification à la valeur de **PROPA** dans l’instance de **ClassB** , elle doit définir `pInst` à cette instance plutôt qu’à une instance de **classa**.</span><span class="sxs-lookup"><span data-stu-id="029ed-175">If an application wants to make a change to the value of **PropA** in the **ClassB** instance, it must set `pInst` to that instance rather than an instance of **ClassA**.</span></span>

<span data-ttu-id="029ed-176">L’appel de `PutInstanceWmi` sur une instance d’une classe abstraite n’est pas autorisé.</span><span class="sxs-lookup"><span data-stu-id="029ed-176">Calling `PutInstanceWmi` on an instance of an abstract class is not allowed.</span></span>

<span data-ttu-id="029ed-177">Si l’appel de fonction échoue, vous pouvez obtenir des informations supplémentaires sur l’erreur en appelant la fonction [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="029ed-177">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="029ed-178">spécifications</span><span class="sxs-lookup"><span data-stu-id="029ed-178">Requirements</span></span>

<span data-ttu-id="029ed-179">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="029ed-179">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="029ed-180">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="029ed-180">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="029ed-181">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="029ed-181">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="029ed-182">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="029ed-182">See also</span></span>

- [<span data-ttu-id="029ed-183">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="029ed-183">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
