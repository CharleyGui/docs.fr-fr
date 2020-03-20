---
title: BlessIWbemServicesObject fonction (Référence API non gestion)
description: La fonction BlessIWbemServicesObject indique si les informations d’identification des utilisateurs permettent l’accès à un objet IWbemServices
ms.date: 11/06/2017
api_name:
- BlessIWbemServicesObject
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServicesObject
helpviewer_keywords:
- BlessIWbemServicesObject function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: fd822f78d29ad3a75fb5e57dd7c23b7049d445b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175029"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="66e62-103">BlessIWbemServicesObject, fonction</span><span class="sxs-lookup"><span data-stu-id="66e62-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="66e62-104">Indique si les informations d’identification de l’utilisateur permettent l’accès à un objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) spécifié.</span><span class="sxs-lookup"><span data-stu-id="66e62-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span>

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="66e62-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66e62-105">Syntax</span></span>

```cpp
HRESULT BlessIWbemServicesObject (
   [in] IUnknown* pIUnknown,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```

## <a name="parameters"></a><span data-ttu-id="66e62-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66e62-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="66e62-107">[dans] Un pointeur vers un objet de service WMI.</span><span class="sxs-lookup"><span data-stu-id="66e62-107">[in] A pointer to a WMI service object.</span></span>

`strUser`\
<span data-ttu-id="66e62-108">[dans] Le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="66e62-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="66e62-109">[dans] Le mot `strUser`de passe associé à .</span><span class="sxs-lookup"><span data-stu-id="66e62-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="66e62-110">[dans] Le nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="66e62-110">[in] The domain name of the user.</span></span> <span data-ttu-id="66e62-111">Consultez la fonction [ConnectServerWmi](connectserverwmi.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="66e62-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="66e62-112">[dans] Le niveau d’usurpation d’identité.</span><span class="sxs-lookup"><span data-stu-id="66e62-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="66e62-113">[dans] Le niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="66e62-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="66e62-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="66e62-114">Return value</span></span>

<span data-ttu-id="66e62-115">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WinError.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="66e62-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="66e62-116">Constant</span><span class="sxs-lookup"><span data-stu-id="66e62-116">Constant</span></span>  |<span data-ttu-id="66e62-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="66e62-117">Value</span></span>  |<span data-ttu-id="66e62-118">Description</span><span class="sxs-lookup"><span data-stu-id="66e62-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="66e62-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="66e62-119">0x80070057</span></span> | <span data-ttu-id="66e62-120">Un ou plusieurs arguments sont invalides.</span><span class="sxs-lookup"><span data-stu-id="66e62-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="66e62-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="66e62-121">0x80004003</span></span> | <span data-ttu-id="66e62-122">`pIWbemServices` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="66e62-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="66e62-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="66e62-123">0x80000008</span></span> | <span data-ttu-id="66e62-124">Une erreur inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="66e62-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="66e62-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="66e62-125">0x80000002</span></span> | <span data-ttu-id="66e62-126">Une mémoire insuffisante est disponible pour effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="66e62-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="66e62-127">0</span><span class="sxs-lookup"><span data-stu-id="66e62-127">0</span></span> | <span data-ttu-id="66e62-128">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="66e62-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="66e62-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="66e62-129">Requirements</span></span>

 <span data-ttu-id="66e62-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66e62-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="66e62-131">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="66e62-131">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="66e62-132">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="66e62-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="66e62-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66e62-133">See also</span></span>

- [<span data-ttu-id="66e62-134">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="66e62-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
