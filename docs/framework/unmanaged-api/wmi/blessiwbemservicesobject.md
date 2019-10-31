---
title: Fonction BlessIWbemServicesObject (référence des API non managées)
description: La fonction BlessIWbemServicesObject indique si les informations d’identification de l’utilisateur autorisent l’accès à un objet IWbemServices
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
ms.openlocfilehash: f77ff394668a235dd63cf0cddf71ea418a28125b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141685"
---
# <a name="blessiwbemservicesobject-function"></a><span data-ttu-id="23d83-103">BlessIWbemServicesObject, fonction</span><span class="sxs-lookup"><span data-stu-id="23d83-103">BlessIWbemServicesObject function</span></span>
<span data-ttu-id="23d83-104">Indique si les informations d’identification de l’utilisateur autorisent l’accès à un objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) spécifié.</span><span class="sxs-lookup"><span data-stu-id="23d83-104">Indicates whether the user credentials permit access to a specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object.</span></span> 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a><span data-ttu-id="23d83-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23d83-105">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="23d83-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="23d83-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="23d83-107">dans Pointeur vers un objet de service WMI.</span><span class="sxs-lookup"><span data-stu-id="23d83-107">[in] A pointer to a WMI service object.</span></span>

`strUser`\
<span data-ttu-id="23d83-108">dans Nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="23d83-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="23d83-109">dans Mot de passe associé à `strUser`.</span><span class="sxs-lookup"><span data-stu-id="23d83-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="23d83-110">dans Nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="23d83-110">[in] The domain name of the user.</span></span> <span data-ttu-id="23d83-111">Pour plus d’informations, consultez la fonction [ConnectServerWmi](connectserverwmi.md) .</span><span class="sxs-lookup"><span data-stu-id="23d83-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="23d83-112">dans Niveau d’emprunt d’identité.</span><span class="sxs-lookup"><span data-stu-id="23d83-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="23d83-113">dans Niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="23d83-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="23d83-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="23d83-114">Return value</span></span>

<span data-ttu-id="23d83-115">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *winerror. h* , ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="23d83-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="23d83-116">Constante</span><span class="sxs-lookup"><span data-stu-id="23d83-116">Constant</span></span>  |<span data-ttu-id="23d83-117">valeur</span><span class="sxs-lookup"><span data-stu-id="23d83-117">Value</span></span>  |<span data-ttu-id="23d83-118">Description</span><span class="sxs-lookup"><span data-stu-id="23d83-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="23d83-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="23d83-119">0x80070057</span></span> | <span data-ttu-id="23d83-120">Un ou plusieurs arguments ne sont pas valides.</span><span class="sxs-lookup"><span data-stu-id="23d83-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="23d83-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="23d83-121">0x80004003</span></span> | <span data-ttu-id="23d83-122">`pIWbemServices` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="23d83-122">`pIWbemServices` is `null`.</span></span> | 
| `E_FAIL` | <span data-ttu-id="23d83-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="23d83-123">0x80000008</span></span> | <span data-ttu-id="23d83-124">Une erreur non spécifiée s’est produite.</span><span class="sxs-lookup"><span data-stu-id="23d83-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="23d83-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="23d83-125">0x80000002</span></span> | <span data-ttu-id="23d83-126">La mémoire disponible est insuffisante pour effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="23d83-126">Insufficient memory is available to perform the operation.</span></span> | 
| `S_OK` | <span data-ttu-id="23d83-127">0</span><span class="sxs-lookup"><span data-stu-id="23d83-127">0</span></span> | <span data-ttu-id="23d83-128">L’appel de la fonction a réussi.</span><span class="sxs-lookup"><span data-stu-id="23d83-128">The function call was successful.</span></span> | 

## <a name="requirements"></a><span data-ttu-id="23d83-129">spécifications</span><span class="sxs-lookup"><span data-stu-id="23d83-129">Requirements</span></span>

 <span data-ttu-id="23d83-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23d83-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="23d83-131">**En-tête :** WMINet_Utils. idl</span><span class="sxs-lookup"><span data-stu-id="23d83-131">**Header:** WMINet_Utils.idl</span></span>

 <span data-ttu-id="23d83-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="23d83-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="23d83-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23d83-133">See also</span></span>

- [<span data-ttu-id="23d83-134">WMI et compteurs de performance (informations de référence sur les API non managées)</span><span class="sxs-lookup"><span data-stu-id="23d83-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
