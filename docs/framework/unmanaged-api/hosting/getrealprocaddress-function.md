---
title: GetRealProcAddress, fonction
ms.date: 03/30/2017
api_name:
- GetRealProcAddress
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetRealProcAddress
helpviewer_keywords:
- GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type:
- apiref
ms.openlocfilehash: 4c914e00987053b1c1e9e00bf8e54632175e1de8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178162"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="3e6b1-102">GetRealProcAddress, fonction</span><span class="sxs-lookup"><span data-stu-id="3e6b1-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="3e6b1-103">Obtient l’adresse de la fonction spécifiée qui est exportée à partir de la dernière version installée de l’heure de fonctionnement de langue commune (CLR).</span><span class="sxs-lookup"><span data-stu-id="3e6b1-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="3e6b1-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e6b1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3e6b1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e6b1-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3e6b1-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="3e6b1-107">[dans] Le nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="3e6b1-108">[out] L’emplacement qui reçoit un pointeur à l’adresse de la fonction.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3e6b1-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="3e6b1-109">Return Value</span></span>  
 <span data-ttu-id="3e6b1-110">Cette méthode renvoie les codes d’erreur standard du modèle d’objet composant (COM), tels que définis dans WinError.h, en plus des valeurs suivantes définies dans CorError.h.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="3e6b1-111">Code de retour</span><span class="sxs-lookup"><span data-stu-id="3e6b1-111">Return code</span></span>|<span data-ttu-id="3e6b1-112">Description</span><span class="sxs-lookup"><span data-stu-id="3e6b1-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="3e6b1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="3e6b1-113">S_OK</span></span>|<span data-ttu-id="3e6b1-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="3e6b1-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="3e6b1-115">E_POINTER</span></span>|<span data-ttu-id="3e6b1-116">`ppv` n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="3e6b1-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="3e6b1-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="3e6b1-118">La fonction n’est pas exportée à partir du temps d’exécution.</span><span class="sxs-lookup"><span data-stu-id="3e6b1-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3e6b1-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3e6b1-119">Requirements</span></span>  
 <span data-ttu-id="3e6b1-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e6b1-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e6b1-121">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="3e6b1-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e6b1-122">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="3e6b1-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e6b1-123">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e6b1-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e6b1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e6b1-124">See also</span></span>

- [<span data-ttu-id="3e6b1-125">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="3e6b1-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
