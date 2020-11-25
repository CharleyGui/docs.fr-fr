---
title: GetRequestedRuntimeVersion, fonction
ms.date: 03/30/2017
api_name:
- GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeVersion
helpviewer_keywords:
- GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type:
- apiref
ms.openlocfilehash: 6c16b02a5ae323ba80d44937f322810022dfa9f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711635"
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="7583f-102">GetRequestedRuntimeVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="7583f-102">GetRequestedRuntimeVersion Function</span></span>

<span data-ttu-id="7583f-103">Obtient le numéro de version du common language runtime (CLR) demandé par l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7583f-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="7583f-104">Si cette version n’est pas installée, obtient la version la plus récente installée avant la version demandée.</span><span class="sxs-lookup"><span data-stu-id="7583f-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="7583f-105">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7583f-105">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7583f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7583f-106">Syntax</span></span>  
  
```cpp  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,
    [out] LPWSTR  pVersion,
    [in]  DWORD   cchBuffer,
    [out] DWORD  *pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7583f-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7583f-107">Parameters</span></span>  

 `pExe`  
 <span data-ttu-id="7583f-108">dans Nom de l’application.</span><span class="sxs-lookup"><span data-stu-id="7583f-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="7583f-109">à Mémoire tampon qui contient la chaîne de numéro de version en cas de réussite.</span><span class="sxs-lookup"><span data-stu-id="7583f-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7583f-110">dans Longueur de la mémoire tampon de version.</span><span class="sxs-lookup"><span data-stu-id="7583f-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="7583f-111">à Pointeur vers la longueur de la chaîne de numéro de version.</span><span class="sxs-lookup"><span data-stu-id="7583f-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7583f-112">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="7583f-112">Return Value</span></span>  

 <span data-ttu-id="7583f-113">Cette méthode retourne des codes d’erreur COM (Component Object Model) standard, tels que définis dans WinError. h, en plus des valeurs suivantes.</span><span class="sxs-lookup"><span data-stu-id="7583f-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="7583f-114">Code de retour</span><span class="sxs-lookup"><span data-stu-id="7583f-114">Return code</span></span>|<span data-ttu-id="7583f-115">Description</span><span class="sxs-lookup"><span data-stu-id="7583f-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7583f-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="7583f-116">S_OK</span></span>|<span data-ttu-id="7583f-117">La commande s'est correctement terminée.</span><span class="sxs-lookup"><span data-stu-id="7583f-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="7583f-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="7583f-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7583f-119">La mémoire tampon de version n’est pas assez grande pour stocker la chaîne de version.</span><span class="sxs-lookup"><span data-stu-id="7583f-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="7583f-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="7583f-120">E_POINTER</span></span>|<span data-ttu-id="7583f-121">`pdwLength` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="7583f-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7583f-122">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7583f-122">Requirements</span></span>  

 <span data-ttu-id="7583f-123">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7583f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7583f-124">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7583f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7583f-125">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7583f-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7583f-126">**Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7583f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7583f-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7583f-127">See also</span></span>

- [<span data-ttu-id="7583f-128">GetRequestedRuntimeInfo, fonction</span><span class="sxs-lookup"><span data-stu-id="7583f-128">GetRequestedRuntimeInfo Function</span></span>](getrequestedruntimeinfo-function.md)
- [<span data-ttu-id="7583f-129">GetVersionFromProcess, fonction</span><span class="sxs-lookup"><span data-stu-id="7583f-129">GetVersionFromProcess Function</span></span>](getversionfromprocess-function.md)
- [<span data-ttu-id="7583f-130">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="7583f-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
