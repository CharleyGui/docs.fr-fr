---
title: IValidator::FormatEventInfo, méthode
ms.date: 03/30/2017
api_name:
- IValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- FormatEventInfo
helpviewer_keywords:
- IValidator::FormatEventInfo method [.NET Framework hosting]
- FormatEventInfo method, IValidator interface [.NET Framework hosting]
ms.assetid: 4c0c7477-05ba-461b-b21b-cbfba95f1db1
topic_type:
- apiref
ms.openlocfilehash: 0c60631b5e034bc46d74412440d35d526359d043
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008571"
---
# <a name="ivalidatorformateventinfo-method"></a><span data-ttu-id="59043-102">IValidator::FormatEventInfo, méthode</span><span class="sxs-lookup"><span data-stu-id="59043-102">IValidator::FormatEventInfo Method</span></span>
<span data-ttu-id="59043-103">Obtient le message d’erreur correspondant à l’erreur de validation spécifiée.</span><span class="sxs-lookup"><span data-stu-id="59043-103">Gets the error message corresponding to the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59043-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59043-104">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo(  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59043-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="59043-105">Parameters</span></span>  
 `hVECode`  
 <span data-ttu-id="59043-106">dans Valeur HRESULT qui a été passée au gestionnaire d’erreurs de validation.</span><span class="sxs-lookup"><span data-stu-id="59043-106">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="59043-107">dans `VEContext`Instance qui contient des informations de contexte sur l’erreur de validation.</span><span class="sxs-lookup"><span data-stu-id="59043-107">[in] A `VEContext` instance that contains context information about the validation error.</span></span>  
  
 `msg`  
 <span data-ttu-id="59043-108">[in, out] Chaîne qui contient le message d’erreur retourné.</span><span class="sxs-lookup"><span data-stu-id="59043-108">[in, out] A string that contains the returned error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="59043-109">dans Longueur maximale du message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="59043-109">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="59043-110">dans Tableau sécurisé qui contient des paramètres supplémentaires qui décrivent l’erreur.</span><span class="sxs-lookup"><span data-stu-id="59043-110">[in] A safe array that contains additional parameters describing the error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59043-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="59043-111">Requirements</span></span>  
 <span data-ttu-id="59043-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59043-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59043-113">**En-tête :** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="59043-113">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="59043-114">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="59043-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="59043-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59043-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
