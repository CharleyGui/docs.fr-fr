---
title: Fonction BlessIWbemServices (référence des API non managées)
description: La fonction BlessIWbemServices indique si les informations d’identification de l’utilisateur autorisent l’accès à une classe IWbemServices.
ms.date: 11/06/2017
api_name:
- BlessIWbemServices
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- BlessIWbemServices
helpviewer_keywords:
- BlessIWbemServices function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: 43ef617ee754c9dcd661b31abba6b17434563c22
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708151"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="9fb8b-103">BlessIWbemServices, fonction</span><span class="sxs-lookup"><span data-stu-id="9fb8b-103">BlessIWbemServices function</span></span>

<span data-ttu-id="9fb8b-104">Indique si les informations d’identification de l’utilisateur autorisent l’accès à la classe [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9fb8b-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="9fb8b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fb8b-105">Syntax</span></span>  
  
```cpp
HRESULT BlessIWbemServices (
   [in] IWbemServices* pIWbemServices,
   [in] BSTR strUser,
   [in] BSTR strPassword,
   [in] BSTR strAuthority,
   [in] DWORD impLevel,
   [in] DWORD authnLevel
);
```  

## <a name="parameters"></a><span data-ttu-id="9fb8b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9fb8b-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="9fb8b-107">dans Pointeur vers l’objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) pour lequel des autorisations sont requises.</span><span class="sxs-lookup"><span data-stu-id="9fb8b-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="9fb8b-108">dans Nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9fb8b-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="9fb8b-109">dans Mot de passe associé à `strUser` .</span><span class="sxs-lookup"><span data-stu-id="9fb8b-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="9fb8b-110">dans Nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="9fb8b-110">[in] The domain name of the user.</span></span> <span data-ttu-id="9fb8b-111">Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="9fb8b-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="9fb8b-112">dans Niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="9fb8b-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="9fb8b-113">dans Niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="9fb8b-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="9fb8b-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9fb8b-114">Return value</span></span>

<span data-ttu-id="9fb8b-115">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *winerror. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="9fb8b-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="9fb8b-116">Constante</span><span class="sxs-lookup"><span data-stu-id="9fb8b-116">Constant</span></span>  |<span data-ttu-id="9fb8b-117">Value</span><span class="sxs-lookup"><span data-stu-id="9fb8b-117">Value</span></span>  |<span data-ttu-id="9fb8b-118">Description</span><span class="sxs-lookup"><span data-stu-id="9fb8b-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="9fb8b-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="9fb8b-119">0x80070057</span></span> | <span data-ttu-id="9fb8b-120">Un ou plusieurs arguments ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="9fb8b-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="9fb8b-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="9fb8b-121">0x80004003</span></span> | <span data-ttu-id="9fb8b-122">`pIWbemServices` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="9fb8b-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="9fb8b-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="9fb8b-123">0x80000008</span></span> | <span data-ttu-id="9fb8b-124">Une erreur inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="9fb8b-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="9fb8b-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="9fb8b-125">0x80000002</span></span> | <span data-ttu-id="9fb8b-126">La mémoire disponible est insuffisante pour effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="9fb8b-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="9fb8b-127">0</span><span class="sxs-lookup"><span data-stu-id="9fb8b-127">0</span></span> | <span data-ttu-id="9fb8b-128">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="9fb8b-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="9fb8b-129">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9fb8b-129">Requirements</span></span>  

 <span data-ttu-id="9fb8b-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fb8b-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fb8b-131">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="9fb8b-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="9fb8b-132">**Versions de .NET Framework :**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9fb8b-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb8b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9fb8b-133">See also</span></span>

- [<span data-ttu-id="9fb8b-134">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="9fb8b-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
