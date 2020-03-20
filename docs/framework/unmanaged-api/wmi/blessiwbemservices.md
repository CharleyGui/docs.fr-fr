---
title: Fonction BlessIWbemServices (Référence API non galée)
description: La fonction BlessIWbemServices indique si les informations d’identification des utilisateurs permettent l’accès à une classe IWbemServices.
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
ms.openlocfilehash: 4b15af840cc00b3ec261604db4f3625c6b975d3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176862"
---
# <a name="blessiwbemservices-function"></a><span data-ttu-id="f2229-103">BlessIWbemServices, fonction</span><span class="sxs-lookup"><span data-stu-id="f2229-103">BlessIWbemServices function</span></span>
<span data-ttu-id="f2229-104">Indique si les informations d’identification de l’utilisateur permettent l’accès à la classe [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) spécifiée.</span><span class="sxs-lookup"><span data-stu-id="f2229-104">Indicates whether the user credentials permit access to the specified [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) class.</span></span>
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a><span data-ttu-id="f2229-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2229-105">Syntax</span></span>  
  
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

## <a name="parameters"></a><span data-ttu-id="f2229-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2229-106">Parameters</span></span>

`pIWbemServices`\
<span data-ttu-id="f2229-107">[dans] Un pointeur sur l’objet [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) pour lequel des autorisations sont requises.</span><span class="sxs-lookup"><span data-stu-id="f2229-107">[in] A pointer to the [IWbemServices](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemservices) object for which permissions are required.</span></span>

`strUser`\
<span data-ttu-id="f2229-108">[dans] Le nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2229-108">[in] The user name.</span></span>

`strPassword`\
<span data-ttu-id="f2229-109">[dans] Le mot `strUser`de passe associé à .</span><span class="sxs-lookup"><span data-stu-id="f2229-109">[in] The password associated with `strUser`.</span></span>

`strAuthority`\
<span data-ttu-id="f2229-110">[dans] Le nom de domaine de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f2229-110">[in] The domain name of the user.</span></span> <span data-ttu-id="f2229-111">Consultez la fonction [ConnectServerWmi](connectserverwmi.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="f2229-111">See the [ConnectServerWmi](connectserverwmi.md) function for more information.</span></span>

`impLevel`\
<span data-ttu-id="f2229-112">[dans] Le niveau d’usurpation d’identité.</span><span class="sxs-lookup"><span data-stu-id="f2229-112">[in] The impersonation level.</span></span>

`authnLevel`\
<span data-ttu-id="f2229-113">[dans] Le niveau d’autorisation.</span><span class="sxs-lookup"><span data-stu-id="f2229-113">[in] The authorization level.</span></span>

## <a name="return-value"></a><span data-ttu-id="f2229-114">Valeur retournée</span><span class="sxs-lookup"><span data-stu-id="f2229-114">Return value</span></span>

<span data-ttu-id="f2229-115">Les valeurs suivantes retournées par cette fonction sont définies dans le fichier d’en-tête *WinError.h,* ou vous pouvez les définir comme des constantes dans votre code :</span><span class="sxs-lookup"><span data-stu-id="f2229-115">The following values returned by this function are defined in the *WinError.h* header file, or you can define them as constants in your code:</span></span>

|<span data-ttu-id="f2229-116">Constant</span><span class="sxs-lookup"><span data-stu-id="f2229-116">Constant</span></span>  |<span data-ttu-id="f2229-117">Valeur</span><span class="sxs-lookup"><span data-stu-id="f2229-117">Value</span></span>  |<span data-ttu-id="f2229-118">Description</span><span class="sxs-lookup"><span data-stu-id="f2229-118">Description</span></span>  |
|---------|---------|---------|
| `E_INVALIDARG` | <span data-ttu-id="f2229-119">0x80070057</span><span class="sxs-lookup"><span data-stu-id="f2229-119">0x80070057</span></span> | <span data-ttu-id="f2229-120">Un ou plusieurs arguments sont invalides.</span><span class="sxs-lookup"><span data-stu-id="f2229-120">One or more arguments are invalid.</span></span> |
| `E_POINTER` | <span data-ttu-id="f2229-121">0x80004003</span><span class="sxs-lookup"><span data-stu-id="f2229-121">0x80004003</span></span> | <span data-ttu-id="f2229-122">`pIWbemServices` a la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="f2229-122">`pIWbemServices` is `null`.</span></span> |
| `E_FAIL` | <span data-ttu-id="f2229-123">0x80000008</span><span class="sxs-lookup"><span data-stu-id="f2229-123">0x80000008</span></span> | <span data-ttu-id="f2229-124">Une erreur inconnue s’est produite.</span><span class="sxs-lookup"><span data-stu-id="f2229-124">An unspecified error has occurred.</span></span> |
| `E_OUTOFMEMORY` | <span data-ttu-id="f2229-125">0x80000002</span><span class="sxs-lookup"><span data-stu-id="f2229-125">0x80000002</span></span> | <span data-ttu-id="f2229-126">Une mémoire insuffisante est disponible pour effectuer l’opération.</span><span class="sxs-lookup"><span data-stu-id="f2229-126">Insufficient memory is available to perform the operation.</span></span> |
| `S_OK` | <span data-ttu-id="f2229-127">0</span><span class="sxs-lookup"><span data-stu-id="f2229-127">0</span></span> | <span data-ttu-id="f2229-128">L’appel de fonction a été réussi.</span><span class="sxs-lookup"><span data-stu-id="f2229-128">The function call was successful.</span></span> |

## <a name="requirements"></a><span data-ttu-id="f2229-129">Spécifications</span><span class="sxs-lookup"><span data-stu-id="f2229-129">Requirements</span></span>  

 <span data-ttu-id="f2229-130">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2229-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2229-131">**En-tête:** WMINet_Utils.idl</span><span class="sxs-lookup"><span data-stu-id="f2229-131">**Header:** WMINet_Utils.idl</span></span>  
  
 <span data-ttu-id="f2229-132">**.NET Versions-cadre:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f2229-132">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2229-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2229-133">See also</span></span>

- [<span data-ttu-id="f2229-134">WMI et compteurs de performances (référence des API non managées)</span><span class="sxs-lookup"><span data-stu-id="f2229-134">WMI and Performance Counters (Unmanaged API Reference)</span></span>](index.md)
