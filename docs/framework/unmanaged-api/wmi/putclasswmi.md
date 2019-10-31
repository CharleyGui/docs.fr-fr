---
title: Fonction PutClassWmi (référence des API non managées)
description: La fonction PutClassWmi crée une nouvelle classe ou met à jour une classe existante.
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 95a5e1f6339bde9dfe5c5ad9f989fc06e10fa7f8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101791"
---
# <a name="putclasswmi-function"></a><span data-ttu-id="878fd-103">PutClassWmi fonction)</span><span class="sxs-lookup"><span data-stu-id="878fd-103">PutClassWmi function</span></span>

<span data-ttu-id="878fd-104">Crée une classe ou met à jour une classe existante.</span><span class="sxs-lookup"><span data-stu-id="878fd-104">Creates a new class or updates an existing one.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="878fd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="878fd-105">Syntax</span></span>

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a><span data-ttu-id="878fd-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="878fd-106">Parameters</span></span>

`pObject`\
<span data-ttu-id="878fd-107">dans Pointeur vers une définition de classe valide.</span><span class="sxs-lookup"><span data-stu-id="878fd-107">[in] A pointer to a valid class definition.</span></span> <span data-ttu-id="878fd-108">Elle doit être correctement initialisée avec toutes les valeurs de propriété requises.</span><span class="sxs-lookup"><span data-stu-id="878fd-108">It must be correctly initialized with all the required property values.</span></span>

`lFlags`\
<span data-ttu-id="878fd-109">dans Combinaison d’indicateurs qui affectent le comportement de cette fonction.</span><span class="sxs-lookup"><span data-stu-id="878fd-109">[in] A combination of flags that affect the behavior of this function.</span></span> <span data-ttu-id="878fd-110">Les valeurs suivantes sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="878fd-110">The following values are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="878fd-111">Constante</span><span class="sxs-lookup"><span data-stu-id="878fd-111">Constant</span></span>  |<span data-ttu-id="878fd-112">valeur</span><span class="sxs-lookup"><span data-stu-id="878fd-112">Value</span></span>  |<span data-ttu-id="878fd-113">Description</span><span class="sxs-lookup"><span data-stu-id="878fd-113">Description</span></span>  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | <span data-ttu-id="878fd-114">0x20000</span><span class="sxs-lookup"><span data-stu-id="878fd-114">0x20000</span></span> | <span data-ttu-id="878fd-115">Si cette valeur est définie, WMI ne stocke pas de qualificateurs avec la version modifiée.</span><span class="sxs-lookup"><span data-stu-id="878fd-115">If set, WMI does not store any qualifiers with the amended flavor.</span></span> <br> <span data-ttu-id="878fd-116">S’il n’est pas défini, il est supposé que cet objet n’est pas localisé, et tous les qualificateurs sont stockés avec cette instance.</span><span class="sxs-lookup"><span data-stu-id="878fd-116">If not set, it is assumed that this object is not localized, and all qualifiers are stored with this instance.</span></span> |
| `WBEM_FLAG_CREATE_OR_UPDATE` | <span data-ttu-id="878fd-117">0</span><span class="sxs-lookup"><span data-stu-id="878fd-117">0</span></span> | <span data-ttu-id="878fd-118">Créez la classe si elle n’existe pas, ou remplacez-la si elle existe déjà.</span><span class="sxs-lookup"><span data-stu-id="878fd-118">Create the class if it does not exist, or overwrite it if it exists already.</span></span> |
| `WBEM_FLAG_UPDATE_ONLY` | <span data-ttu-id="878fd-119">1</span><span class="sxs-lookup"><span data-stu-id="878fd-119">1</span></span> | <span data-ttu-id="878fd-120">Mettez à jour la classe.</span><span class="sxs-lookup"><span data-stu-id="878fd-120">Update the class.</span></span> <span data-ttu-id="878fd-121">La classe doit exister pour que l’appel réussisse.</span><span class="sxs-lookup"><span data-stu-id="878fd-121">The class must exist for the call to be successful.</span></span> |
| `WBEM_FLAG_CREATE_ONLY` | <span data-ttu-id="878fd-122">2</span><span class="sxs-lookup"><span data-stu-id="878fd-122">2</span></span> | <span data-ttu-id="878fd-123">Créez la classe.</span><span class="sxs-lookup"><span data-stu-id="878fd-123">Create the class.</span></span> <span data-ttu-id="878fd-124">L’appel échoue si la classe existe déjà.</span><span class="sxs-lookup"><span data-stu-id="878fd-124">The call fails if the class already exists.</span></span> |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | <span data-ttu-id="878fd-125">0x10</span><span class="sxs-lookup"><span data-stu-id="878fd-125">0x10</span></span> | <span data-ttu-id="878fd-126">L’indicateur provoque un appel semi-synchrone.</span><span class="sxs-lookup"><span data-stu-id="878fd-126">The flag causes a semisynchronous call.</span></span> |
| `WBEM_FLAG_OWNER_UPDATE` | <span data-ttu-id="878fd-127">0x10000</span><span class="sxs-lookup"><span data-stu-id="878fd-127">0x10000</span></span> | <span data-ttu-id="878fd-128">Les fournisseurs de notifications push doivent spécifier cet indicateur lors de l’appel de `PutClassWmi` pour indiquer que cette classe a été modifiée.</span><span class="sxs-lookup"><span data-stu-id="878fd-128">Push providers must specify this flag when calling `PutClassWmi` to indicate that this class has changed.</span></span> |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | <span data-ttu-id="878fd-129">0</span><span class="sxs-lookup"><span data-stu-id="878fd-129">0</span></span> | <span data-ttu-id="878fd-130">Permet à une classe d’être mise à jour s’il n’y a pas de classes dérivées et aucune instance de cette classe.</span><span class="sxs-lookup"><span data-stu-id="878fd-130">Allows a class to be updated if there are no derived classes and no instances of that class.</span></span> <span data-ttu-id="878fd-131">Il autorise également les mises à jour dans tous les cas si la modification concerne uniquement des qualificateurs peu importants, tels que le qualificateur de description.</span><span class="sxs-lookup"><span data-stu-id="878fd-131">It also allows updates in all cases if the change is just to unimportant qualifiers, such as the Description qualifier.</span></span> <span data-ttu-id="878fd-132">Si la classe a des instances ou des modifications pour des qualificateurs importants, la mise à jour échoue.</span><span class="sxs-lookup"><span data-stu-id="878fd-132">If the class has instances or changes are to important qualifiers, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | <span data-ttu-id="878fd-133">0x20</span><span class="sxs-lookup"><span data-stu-id="878fd-133">0x20</span></span> | <span data-ttu-id="878fd-134">Autorise les mises à jour des classes, même s’il existe des classes enfants tant que la modification n’entraîne pas de conflits avec les classes enfants.</span><span class="sxs-lookup"><span data-stu-id="878fd-134">Allows updates of classes even if there are child classes as long as the change does not cause any conflicts with child classes.</span></span> <span data-ttu-id="878fd-135">Par exemple, cet indicateur permet d’ajouter une nouvelle propriété à la classe de base qui n’a pas été précédemment mentionnée dans une des classes enfants.</span><span class="sxs-lookup"><span data-stu-id="878fd-135">For example, this flag allows a new property to be added to the base class that was not previously mentioned in any of the child classes.</span></span> <span data-ttu-id="878fd-136">Si la classe a des instances, la mise à jour échoue.</span><span class="sxs-lookup"><span data-stu-id="878fd-136">If the class has instances, the update fails.</span></span> |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | <span data-ttu-id="878fd-137">0x40</span><span class="sxs-lookup"><span data-stu-id="878fd-137">0x40</span></span> | <span data-ttu-id="878fd-138">force les mises à jour des classes lorsque des classes enfants sont en conflit.</span><span class="sxs-lookup"><span data-stu-id="878fd-138">forces updates of classes when conflicting child classes exist.</span></span> <span data-ttu-id="878fd-139">Par exemple, cet indicateur force une mise à jour si un qualificateur de classe est défini dans une classe enfant, et si la classe de base tente d’ajouter le même qualificateur qui est en conflit avec l’option existante.</span><span class="sxs-lookup"><span data-stu-id="878fd-139">For example, this flag forces an update if a class qualifier is defined in a child class, and the base class tries to add the same qualifier which conflicts with the existing one.</span></span> <span data-ttu-id="878fd-140">En mode forcé, le conflit tis est résolu en supprimant le qualificateur en conflit dans la classe enfant.</span><span class="sxs-lookup"><span data-stu-id="878fd-140">In force mode, tis conflict is resolved by deleting the conflicting qualifier in the child class.</span></span> |

`pCtx`\
<span data-ttu-id="878fd-141">dans En général, cette valeur est `null`.</span><span class="sxs-lookup"><span data-stu-id="878fd-141">[in] Typically, this value is `null`.</span></span> <span data-ttu-id="878fd-142">Dans le cas contraire, il s’agit d’un pointeur vers une instance [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) qui peut être utilisée par le fournisseur qui fournit les classes demandées.</span><span class="sxs-lookup"><span data-stu-id="878fd-142">Otherwise, it is a pointer to an [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext) instance that can be used by the provider that is providing the requested classes.</span></span>

`ppCallResult`\
<span data-ttu-id="878fd-143">à Si `null`, ce paramètre n’est pas utilisé.</span><span class="sxs-lookup"><span data-stu-id="878fd-143">[out] If `null`, this parameter is unused.</span></span> <span data-ttu-id="878fd-144">Si `lFlags` contient des `WBEM_FLAG_RETURN_IMMEDIATELY`, la fonction retourne immédiatement avec `WBEM_S_NO_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="878fd-144">If `lFlags` contains `WBEM_FLAG_RETURN_IMMEDIATELY`, the function returns immediately with `WBEM_S_NO_ERROR`.</span></span> <span data-ttu-id="878fd-145">Le paramètre `ppCallResult` reçoit un pointeur vers un nouvel objet [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) .</span><span class="sxs-lookup"><span data-stu-id="878fd-145">The `ppCallResult` parameter receives a pointer to a new [IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult) object.</span></span>

## <a name="return-value"></a><span data-ttu-id="878fd-146">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="878fd-146">Return value</span></span>

<span data-ttu-id="878fd-147">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="878fd-147">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="878fd-148">Constante</span><span class="sxs-lookup"><span data-stu-id="878fd-148">Constant</span></span>  |<span data-ttu-id="878fd-149">valeur</span><span class="sxs-lookup"><span data-stu-id="878fd-149">Value</span></span>  |<span data-ttu-id="878fd-150">Description</span><span class="sxs-lookup"><span data-stu-id="878fd-150">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | <span data-ttu-id="878fd-151">0x80041003</span><span class="sxs-lookup"><span data-stu-id="878fd-151">0x80041003</span></span> | <span data-ttu-id="878fd-152">L’utilisateur n’a pas l’autorisation de créer ou de modifier des classes.</span><span class="sxs-lookup"><span data-stu-id="878fd-152">The user does not have permission to create or modify classes.</span></span> |
| `WBEM_E_FAILED` | <span data-ttu-id="878fd-153">0x80041001</span><span class="sxs-lookup"><span data-stu-id="878fd-153">0x80041001</span></span> | <span data-ttu-id="878fd-154">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="878fd-154">An unspecified error has occurred.</span></span> |
| `WBEM_E_INVALID_CLASS` | <span data-ttu-id="878fd-155">0x80041010</span><span class="sxs-lookup"><span data-stu-id="878fd-155">0x80041010</span></span> | <span data-ttu-id="878fd-156">La classe spécifiée n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="878fd-156">The specified class is not valid.</span></span> <span data-ttu-id="878fd-157">En règle générale, cela indique que `pObject` spécifie un objet d’instance.</span><span class="sxs-lookup"><span data-stu-id="878fd-157">Typically, this indicates that `pObject` specifies an instance object.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="878fd-158">0x80041008</span><span class="sxs-lookup"><span data-stu-id="878fd-158">0x80041008</span></span> | <span data-ttu-id="878fd-159">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="878fd-159">A parameter is not valid.</span></span> |
| `WBEM_E_INVALID OPERATION` | <span data-ttu-id="878fd-160">0x80041016</span><span class="sxs-lookup"><span data-stu-id="878fd-160">0x80041016</span></span> | <span data-ttu-id="878fd-161">Le nom de classe spécifié n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="878fd-161">The specified class name is not valid.</span></span> |
| `WBEM_E_CLASS_HAS_CHILDREN` | <span data-ttu-id="878fd-162">0x80041025</span><span class="sxs-lookup"><span data-stu-id="878fd-162">0x80041025</span></span> | <span data-ttu-id="878fd-163">Une tentative a été effectuée pour apporter une modification qui invaliderait une sous-classe.</span><span class="sxs-lookup"><span data-stu-id="878fd-163">An attempt was made to make a change that would invalidate a subclass.</span></span> |
| `WBEM_E_ALREADY_EXISTS` | <span data-ttu-id="878fd-164">0x80041019</span><span class="sxs-lookup"><span data-stu-id="878fd-164">0x80041019</span></span> | <span data-ttu-id="878fd-165">L’indicateur de `WBEM_FLAG_CREATE_ONLY` a été spécifié, mais la classe existe déjà.</span><span class="sxs-lookup"><span data-stu-id="878fd-165">The `WBEM_FLAG_CREATE_ONLY` flag was specified, but the class already exists.</span></span> |
| `WBEM_E_NOT_FOUND` | <span data-ttu-id="878fd-166">0x80041002</span><span class="sxs-lookup"><span data-stu-id="878fd-166">0x80041002</span></span> | <span data-ttu-id="878fd-167">`WBEM_FLAG_UPDATE_ONLY` a été spécifié dans `lFlags`, et la classe est introuvable.</span><span class="sxs-lookup"><span data-stu-id="878fd-167">`WBEM_FLAG_UPDATE_ONLY` was specified in `lFlags`, and the class was not found.</span></span> |
| `WBEM_E_INCOMPLETE_CLASS` | <span data-ttu-id="878fd-168">0x80041020</span><span class="sxs-lookup"><span data-stu-id="878fd-168">0x80041020</span></span> | <span data-ttu-id="878fd-169">Les propriétés requises pour les classes n’ont pas toutes été définies.</span><span class="sxs-lookup"><span data-stu-id="878fd-169">The required properties for classes have not all been set.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="878fd-170">0x80041006</span><span class="sxs-lookup"><span data-stu-id="878fd-170">0x80041006</span></span> | <span data-ttu-id="878fd-171">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="878fd-171">Not enough memory is available to complete the operation.</span></span> |
| `WBEM_E_SHUTTING_DOWN` | <span data-ttu-id="878fd-172">0x80041033</span><span class="sxs-lookup"><span data-stu-id="878fd-172">0x80041033</span></span> | <span data-ttu-id="878fd-173">WMI a probablement été arrêté et redémarré.</span><span class="sxs-lookup"><span data-stu-id="878fd-173">WMI was probably stopped and restarting.</span></span> <span data-ttu-id="878fd-174">Appelez à nouveau [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="878fd-174">Call [ConnectServerWmi](connectserverwmi.md) again.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="878fd-175">0x80041015</span><span class="sxs-lookup"><span data-stu-id="878fd-175">0x80041015</span></span> | <span data-ttu-id="878fd-176">Le lien de l’appel de procédure distante (RPC) entre le processus en cours et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="878fd-176">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="878fd-177">0</span><span class="sxs-lookup"><span data-stu-id="878fd-177">0</span></span> | <span data-ttu-id="878fd-178">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="878fd-178">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="878fd-179">Notes</span><span class="sxs-lookup"><span data-stu-id="878fd-179">Remarks</span></span>

<span data-ttu-id="878fd-180">Cette fonction encapsule un appel à la méthode [IWbemServices ::P utclass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) .</span><span class="sxs-lookup"><span data-stu-id="878fd-180">This function wraps a call to the [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass) method.</span></span>

<span data-ttu-id="878fd-181">L’utilisateur ne peut pas créer de classes dont les noms commencent ou se terminent par un caractère de soulignement.</span><span class="sxs-lookup"><span data-stu-id="878fd-181">The user may not create classes with names that begin or end with an underscore character.</span></span>

<span data-ttu-id="878fd-182">Si l’appel de fonction échoue, vous pouvez obtenir des informations supplémentaires sur l’erreur en appelant la fonction [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="878fd-182">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="requirements"></a><span data-ttu-id="878fd-183">spécifications</span><span class="sxs-lookup"><span data-stu-id="878fd-183">Requirements</span></span>

<span data-ttu-id="878fd-184">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="878fd-184">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="878fd-185">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="878fd-185">**Header:** WMINet_Utils.idl</span></span>

<span data-ttu-id="878fd-186">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="878fd-186">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="878fd-187">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="878fd-187">See also</span></span>

- [<span data-ttu-id="878fd-188">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="878fd-188">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
