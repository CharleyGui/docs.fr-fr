---
title: Cloneenumwbemclassobject, fonction (référence des API non managées)
description: Cloneenumwbemclassobject, de la fonction effectue une copie logique d’un énumérateur.
ms.date: 11/06/2017
api_name:
- CloneEnumWbemClassObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- CloneEnumWbemClassObject
helpviewer_keywords:
- CloneEnumWbemClassObject function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab660769a49cf12b129cb7f44b8378053a231f8c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761627"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="f2236-103">CloneEnumWbemClassObject, fonction</span><span class="sxs-lookup"><span data-stu-id="f2236-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="f2236-104">Effectue une copie logique d’un énumérateur, en conservant sa position actuelle dans une énumération.</span><span class="sxs-lookup"><span data-stu-id="f2236-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="f2236-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2236-105">Syntax</span></span>

```cpp
HRESULT CloneEnumWbemClassObject (
   [out] IEnumWbemClassObject**  ppEnum, 
   [in] DWORD                    authLevel,
   [in] DWORD                    impLevel,
   [in] IEnumWbemClassObject*    pCurrentEnumWbemClassObject, 
   [in] BSTR                     strUser,
   [in] BSTR                     strPassword,
   [in BSTR]                     strAuthority 
); 
```

## <a name="parameters"></a><span data-ttu-id="f2236-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2236-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="f2236-107">[out] Reçoit un pointeur vers un nouveau [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="f2236-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="f2236-108">[in] Le niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f2236-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="f2236-109">[in] Le niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="f2236-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="f2236-110">[out] Un pointeur vers le [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance à cloner.</span><span class="sxs-lookup"><span data-stu-id="f2236-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="f2236-111">[in] Le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2236-111">[in] The user name.</span></span> <span data-ttu-id="f2236-112">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="f2236-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="f2236-113">[in] Le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="f2236-113">[in] The password.</span></span> <span data-ttu-id="f2236-114">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="f2236-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="f2236-115">`strAuthority`\ [in] le nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2236-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="f2236-116">Consultez le [ConnectServerWmi](connectserverwmi.md) (fonction) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="f2236-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="f2236-117">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f2236-117">Return value</span></span>

<span data-ttu-id="f2236-118">Les valeurs suivantes est retournées par cette fonction sont définies dans le *WbemCli.h* fichier d’en-tête, ou vous pouvez les définir en tant que constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="f2236-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f2236-119">Constante</span><span class="sxs-lookup"><span data-stu-id="f2236-119">Constant</span></span>  |<span data-ttu-id="f2236-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="f2236-120">Value</span></span>  |<span data-ttu-id="f2236-121">Description</span><span class="sxs-lookup"><span data-stu-id="f2236-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="f2236-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="f2236-122">0x80041001</span></span> | <span data-ttu-id="f2236-123">Il y a eu une défaillance générale.</span><span class="sxs-lookup"><span data-stu-id="f2236-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="f2236-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="f2236-124">0x80041008</span></span> | <span data-ttu-id="f2236-125">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="f2236-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="f2236-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="f2236-126">0x80041006</span></span> | <span data-ttu-id="f2236-127">Pas assez de mémoire est disponible d’effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="f2236-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="f2236-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="f2236-128">0x80041015</span></span> | <span data-ttu-id="f2236-129">Le lien remote procedure call (RPC) entre les processus en cours et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="f2236-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="f2236-130">0</span><span class="sxs-lookup"><span data-stu-id="f2236-130">0</span></span> | <span data-ttu-id="f2236-131">L’appel de fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="f2236-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="f2236-132">Notes</span><span class="sxs-lookup"><span data-stu-id="f2236-132">Remarks</span></span>

<span data-ttu-id="f2236-133">Cette fonction encapsule un appel à la [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) (méthode).</span><span class="sxs-lookup"><span data-stu-id="f2236-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="f2236-134">Cette méthode effectue une copie « meilleur effort ».</span><span class="sxs-lookup"><span data-stu-id="f2236-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="f2236-135">En raison de la nature dynamique de nombreux objets CIM, il est possible que le nouvel énumérateur n’énumère pas le même jeu d’objets que l’énumérateur de source.</span><span class="sxs-lookup"><span data-stu-id="f2236-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="f2236-136">Si l’appel de fonction échoue, vous pouvez obtenir des informations d’erreur supplémentaires en appelant le [GetErrorInfo](geterrorinfo.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="f2236-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="f2236-137">Exemples</span><span class="sxs-lookup"><span data-stu-id="f2236-137">Example</span></span>

<span data-ttu-id="f2236-138">Pour obtenir un exemple, consultez le [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) (méthode).</span><span class="sxs-lookup"><span data-stu-id="f2236-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f2236-139">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="f2236-139">Requirements</span></span>
 <span data-ttu-id="f2236-140">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2236-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="f2236-141">**En-tête :** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f2236-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="f2236-142">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f2236-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f2236-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2236-143">See also</span></span>

- [<span data-ttu-id="f2236-144">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="f2236-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
