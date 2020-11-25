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
ms.openlocfilehash: d48106fca6008955409581ad9ac202aebe785cb4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733223"
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="d3ea5-102">GetRealProcAddress, fonction</span><span class="sxs-lookup"><span data-stu-id="d3ea5-102">GetRealProcAddress Function</span></span>

<span data-ttu-id="d3ea5-103">Obtient l’adresse de la fonction spécifiée qui est exportée à partir de la dernière version installée du common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="d3ea5-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="d3ea5-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d3ea5-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3ea5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3ea5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,
    [out] VOID  **ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3ea5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d3ea5-106">Parameters</span></span>  

 `pwszProcName`  
 <span data-ttu-id="d3ea5-107">dans Nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d3ea5-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="d3ea5-108">à Emplacement qui reçoit un pointeur vers l’adresse de la fonction.</span><span class="sxs-lookup"><span data-stu-id="d3ea5-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d3ea5-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d3ea5-109">Return Value</span></span>  

 <span data-ttu-id="d3ea5-110">Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes définies dans CorError. h.</span><span class="sxs-lookup"><span data-stu-id="d3ea5-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="d3ea5-111">Code de retour</span><span class="sxs-lookup"><span data-stu-id="d3ea5-111">Return code</span></span>|<span data-ttu-id="d3ea5-112">Description</span><span class="sxs-lookup"><span data-stu-id="d3ea5-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d3ea5-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="d3ea5-113">S_OK</span></span>|<span data-ttu-id="d3ea5-114">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="d3ea5-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="d3ea5-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="d3ea5-115">E_POINTER</span></span>|<span data-ttu-id="d3ea5-116">`ppv` n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="d3ea5-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="d3ea5-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="d3ea5-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="d3ea5-118">La fonction n’est pas exportée à partir du Runtime.</span><span class="sxs-lookup"><span data-stu-id="d3ea5-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3ea5-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d3ea5-119">Requirements</span></span>  

 <span data-ttu-id="d3ea5-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3ea5-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3ea5-121">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d3ea5-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3ea5-122">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d3ea5-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3ea5-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3ea5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3ea5-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d3ea5-124">See also</span></span>

- [<span data-ttu-id="d3ea5-125">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="d3ea5-125">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
