---
title: CloneEnumWbemClassObject fonction (référence API non géré)
description: La fonction CloneEnumWbemClassObject fait une copie logique d’un enumérateur.
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
ms.openlocfilehash: f2a3a7e848108e50c04f0ec70cf42586755a0a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175016"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="e54a0-103">CloneEnumWbemClassObject, fonction</span><span class="sxs-lookup"><span data-stu-id="e54a0-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="e54a0-104">Effectue une copie logique d’un énumérateur, en conservant sa position actuelle dans une énumération.</span><span class="sxs-lookup"><span data-stu-id="e54a0-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="e54a0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e54a0-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="e54a0-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e54a0-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="e54a0-107">[out] Reçoit un pointeur à un nouveau [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="e54a0-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="e54a0-108">[dans] Le niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="e54a0-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="e54a0-109">[dans] Le niveau d’usurpation d’identité.</span><span class="sxs-lookup"><span data-stu-id="e54a0-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="e54a0-110">[out] Un pointeur à l’instance [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) à cloner.</span><span class="sxs-lookup"><span data-stu-id="e54a0-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="e54a0-111">[dans] Le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e54a0-111">[in] The user name.</span></span> <span data-ttu-id="e54a0-112">Consultez la fonction [ConnectServerWmi](connectserverwmi.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="e54a0-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="e54a0-113">[dans] Le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e54a0-113">[in] The password.</span></span> <span data-ttu-id="e54a0-114">Consultez la fonction [ConnectServerWmi](connectserverwmi.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="e54a0-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strAuthority`\
<span data-ttu-id="e54a0-115">[dans] Le nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e54a0-115">[in] The domain name of the user.</span></span> <span data-ttu-id="e54a0-116">Consultez la fonction [ConnectServerWmi](connectserverwmi.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="e54a0-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="e54a0-117">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="e54a0-117">Return value</span></span>

<span data-ttu-id="e54a0-118">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="e54a0-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="e54a0-119">Constant</span><span class="sxs-lookup"><span data-stu-id="e54a0-119">Constant</span></span>  |<span data-ttu-id="e54a0-120">Valeur</span><span class="sxs-lookup"><span data-stu-id="e54a0-120">Value</span></span>  |<span data-ttu-id="e54a0-121">Description</span><span class="sxs-lookup"><span data-stu-id="e54a0-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="e54a0-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="e54a0-122">0x80041001</span></span> | <span data-ttu-id="e54a0-123">Il y a eu un échec général.</span><span class="sxs-lookup"><span data-stu-id="e54a0-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="e54a0-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="e54a0-124">0x80041008</span></span> | <span data-ttu-id="e54a0-125">Un paramètre est invalide.</span><span class="sxs-lookup"><span data-stu-id="e54a0-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="e54a0-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="e54a0-126">0x80041006</span></span> | <span data-ttu-id="e54a0-127">Pas assez de mémoire est disponible compléter l’opération.</span><span class="sxs-lookup"><span data-stu-id="e54a0-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="e54a0-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="e54a0-128">0x80041015</span></span> | <span data-ttu-id="e54a0-129">Le lien d’appel à distance (RPC) entre le processus actuel et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="e54a0-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="e54a0-130">0</span><span class="sxs-lookup"><span data-stu-id="e54a0-130">0</span></span> | <span data-ttu-id="e54a0-131">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="e54a0-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="e54a0-132">Notes </span><span class="sxs-lookup"><span data-stu-id="e54a0-132">Remarks</span></span>

<span data-ttu-id="e54a0-133">Cette fonction enveloppe un appel à [l’IEnumWbemClassObject::Méthode Clone.](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone)</span><span class="sxs-lookup"><span data-stu-id="e54a0-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="e54a0-134">Cette méthode ne fait qu’une copie du « meilleur effort ».</span><span class="sxs-lookup"><span data-stu-id="e54a0-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="e54a0-135">En raison de la nature dynamique de nombreux objets CIM, il est possible que le nouvel énumérateur n’énumère pas le même ensemble d’objets que l’enumérateur source.</span><span class="sxs-lookup"><span data-stu-id="e54a0-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="e54a0-136">Si l’appel de fonction échoue, vous pouvez obtenir des informations d’erreur supplémentaires en appelant la fonction [GetErrorInfo.](geterrorinfo.md)</span><span class="sxs-lookup"><span data-stu-id="e54a0-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="e54a0-137"> Exemple</span><span class="sxs-lookup"><span data-stu-id="e54a0-137">Example</span></span>

<span data-ttu-id="e54a0-138">Par exemple, voir la méthode [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) méthode.</span><span class="sxs-lookup"><span data-stu-id="e54a0-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e54a0-139">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e54a0-139">Requirements</span></span>
 <span data-ttu-id="e54a0-140">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e54a0-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="e54a0-141">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="e54a0-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="e54a0-142">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e54a0-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="e54a0-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e54a0-143">See also</span></span>

- [<span data-ttu-id="e54a0-144">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="e54a0-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
