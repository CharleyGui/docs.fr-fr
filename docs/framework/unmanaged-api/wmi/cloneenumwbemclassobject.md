---
title: Fonction CloneEnumWbemClassObject (référence des API non managées)
description: La fonction CloneEnumWbemClassObject effectue une copie logique d’un énumérateur.
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
ms.openlocfilehash: 9d2442161aaa83693a33f9efc230c09b8c4426e2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128732"
---
# <a name="cloneenumwbemclassobject-function"></a><span data-ttu-id="bc282-103">CloneEnumWbemClassObject, fonction</span><span class="sxs-lookup"><span data-stu-id="bc282-103">CloneEnumWbemClassObject function</span></span>
<span data-ttu-id="bc282-104">Effectue une copie logique d’un énumérateur, en conservant sa position actuelle dans une énumération.</span><span class="sxs-lookup"><span data-stu-id="bc282-104">Makes a logical copy of an enumerator, retaining its current position in an enumeration.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="bc282-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc282-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="bc282-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bc282-106">Parameters</span></span>

`ppEnum`\
<span data-ttu-id="bc282-107">à Reçoit un pointeur vers un nouveau [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span><span class="sxs-lookup"><span data-stu-id="bc282-107">[out] Receives a pointer to a new [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject).</span></span>

`authLevel`\
<span data-ttu-id="bc282-108">dans Niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="bc282-108">[in] The authorization level.</span></span>

`impLevel`\
<span data-ttu-id="bc282-109">dans Niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="bc282-109">[in] The impersonation level.</span></span>

`pCurrentEnumWbemClassObject`\
<span data-ttu-id="bc282-110">à Pointeur vers l’instance [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) à cloner.</span><span class="sxs-lookup"><span data-stu-id="bc282-110">[out] A pointer to the [IEnumWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-ienumwbemclassobject) instance to be cloned.</span></span>

`strUser`\
<span data-ttu-id="bc282-111">dans Nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bc282-111">[in] The user name.</span></span> <span data-ttu-id="bc282-112">Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="bc282-112">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`strPassword`\
<span data-ttu-id="bc282-113">dans Mot de passe.</span><span class="sxs-lookup"><span data-stu-id="bc282-113">[in] The password.</span></span> <span data-ttu-id="bc282-114">Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="bc282-114">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

<span data-ttu-id="bc282-115">`strAuthority`\ [in] nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="bc282-115">`strAuthority`\ [in] The domain name of the user.</span></span> <span data-ttu-id="bc282-116">Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="bc282-116">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

## <a name="return-value"></a><span data-ttu-id="bc282-117">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="bc282-117">Return value</span></span>

<span data-ttu-id="bc282-118">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WbemCli. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="bc282-118">The following values returned by this function are defined in the *WbemCli.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="bc282-119">Constante</span><span class="sxs-lookup"><span data-stu-id="bc282-119">Constant</span></span>  |<span data-ttu-id="bc282-120">valeur</span><span class="sxs-lookup"><span data-stu-id="bc282-120">Value</span></span>  |<span data-ttu-id="bc282-121">Description</span><span class="sxs-lookup"><span data-stu-id="bc282-121">Description</span></span>  |
|---------|---------|---------|
| `WBEM_E_FAILED` | <span data-ttu-id="bc282-122">0x80041001</span><span class="sxs-lookup"><span data-stu-id="bc282-122">0x80041001</span></span> | <span data-ttu-id="bc282-123">Une défaillance générale s’est produite.</span><span class="sxs-lookup"><span data-stu-id="bc282-123">There has been a general failure.</span></span> |
| `WBEM_E_INVALID_PARAMETER` | <span data-ttu-id="bc282-124">0x80041008</span><span class="sxs-lookup"><span data-stu-id="bc282-124">0x80041008</span></span> | <span data-ttu-id="bc282-125">Un paramètre n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="bc282-125">A parameter is invalid.</span></span> |
| `WBEM_E_OUT_OF_MEMORY` | <span data-ttu-id="bc282-126">0x80041006</span><span class="sxs-lookup"><span data-stu-id="bc282-126">0x80041006</span></span> | <span data-ttu-id="bc282-127">La mémoire disponible est insuffisante pour terminer l’opération.</span><span class="sxs-lookup"><span data-stu-id="bc282-127">Not enough memory is available complete the operation.</span></span> |
| `WBEM_E_TRANSPORT_FAILURE` | <span data-ttu-id="bc282-128">0x80041015</span><span class="sxs-lookup"><span data-stu-id="bc282-128">0x80041015</span></span> | <span data-ttu-id="bc282-129">Le lien de l’appel de procédure distante (RPC) entre le processus en cours et WMI a échoué.</span><span class="sxs-lookup"><span data-stu-id="bc282-129">The remote procedure call (RPC) link between the current process and WMI has failed.</span></span> |
| `WBEM_S_NO_ERROR` | <span data-ttu-id="bc282-130">0</span><span class="sxs-lookup"><span data-stu-id="bc282-130">0</span></span> | <span data-ttu-id="bc282-131">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="bc282-131">The function call was successful.</span></span>  |

## <a name="remarks"></a><span data-ttu-id="bc282-132">Notes</span><span class="sxs-lookup"><span data-stu-id="bc282-132">Remarks</span></span>

<span data-ttu-id="bc282-133">Cette fonction encapsule un appel à la méthode [IEnumWbemClassObject :: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="bc282-133">This function wraps a call to the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

<span data-ttu-id="bc282-134">Cette méthode effectue uniquement une copie « meilleur effort ».</span><span class="sxs-lookup"><span data-stu-id="bc282-134">This method makes only a "best effort" copy.</span></span> <span data-ttu-id="bc282-135">En raison de la nature dynamique de nombreux objets CIM, il est possible que le nouvel énumérateur n’énumère pas le même jeu d’objets que l’énumérateur source.</span><span class="sxs-lookup"><span data-stu-id="bc282-135">Due to the dynamic nature of many CIM objects, it is possible that the new enumerator does not enumerate the same set of objects as the source enumerator.</span></span>

<span data-ttu-id="bc282-136">Si l’appel de fonction échoue, vous pouvez obtenir des informations supplémentaires sur l’erreur en appelant la fonction [GetErrorInfo](geterrorinfo.md) .</span><span class="sxs-lookup"><span data-stu-id="bc282-136">If the function call fails, you can obtain additional error information by calling the [GetErrorInfo](geterrorinfo.md) function.</span></span>

## <a name="example"></a><span data-ttu-id="bc282-137">Exemple</span><span class="sxs-lookup"><span data-stu-id="bc282-137">Example</span></span>

<span data-ttu-id="bc282-138">Pour obtenir un exemple, consultez la méthode [IEnumWbemClassObject :: Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) .</span><span class="sxs-lookup"><span data-stu-id="bc282-138">For an example, see the [IEnumWbemClassObject::Clone](/windows/desktop/api/wbemcli/nf-wbemcli-ienumwbemclassobject-clone) method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bc282-139">spécifications</span><span class="sxs-lookup"><span data-stu-id="bc282-139">Requirements</span></span>
 <span data-ttu-id="bc282-140">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc282-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="bc282-141">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="bc282-141">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="bc282-142">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bc282-142">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bc282-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc282-143">See also</span></span>

- [<span data-ttu-id="bc282-144">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="bc282-144">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
