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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0027514392dfbb93ab4189eb7c66a380fb77c1ae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778160"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="476e5-102">GetRealProcAddress, fonction</span><span class="sxs-lookup"><span data-stu-id="476e5-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="476e5-103">Obtient l’adresse de la fonction spécifiée qui est exportée à partir de la dernière version installée pour le common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="476e5-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="476e5-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="476e5-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476e5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="476e5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="476e5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="476e5-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="476e5-107">[in] Le nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="476e5-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="476e5-108">[out] L’emplacement qui reçoit un pointeur vers l’adresse de la fonction.</span><span class="sxs-lookup"><span data-stu-id="476e5-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="476e5-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="476e5-109">Return Value</span></span>  
 <span data-ttu-id="476e5-110">Cette méthode retourne des codes d’erreur de composant COM (Object Model) standard, tel que défini dans WinError.h, en plus des valeurs suivantes définies dans CorError.h.</span><span class="sxs-lookup"><span data-stu-id="476e5-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="476e5-111">Code de retour</span><span class="sxs-lookup"><span data-stu-id="476e5-111">Return code</span></span>|<span data-ttu-id="476e5-112">Description</span><span class="sxs-lookup"><span data-stu-id="476e5-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="476e5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="476e5-113">S_OK</span></span>|<span data-ttu-id="476e5-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="476e5-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="476e5-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="476e5-115">E_POINTER</span></span>|<span data-ttu-id="476e5-116">`ppv` n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="476e5-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="476e5-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="476e5-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="476e5-118">La fonction n’est pas exportée à partir de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="476e5-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="476e5-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="476e5-119">Requirements</span></span>  
 <span data-ttu-id="476e5-120">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="476e5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="476e5-121">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="476e5-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="476e5-122">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="476e5-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="476e5-123">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="476e5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="476e5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="476e5-124">See also</span></span>

- [<span data-ttu-id="476e5-125">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="476e5-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
