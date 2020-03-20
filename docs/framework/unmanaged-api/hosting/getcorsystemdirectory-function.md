---
title: GetCORSystemDirectory, fonction
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
ms.openlocfilehash: bdafacfe52d678aacfcd44de1e924bcb88547424
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178206"
---
# <a name="getcorsystemdirectory-function"></a><span data-ttu-id="e1302-102">GetCORSystemDirectory, fonction</span><span class="sxs-lookup"><span data-stu-id="e1302-102">GetCORSystemDirectory Function</span></span>
<span data-ttu-id="e1302-103">Retourne le répertoire d’installation de l’heure de course de langue commune (CLR) qui est chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e1302-103">Returns the installation directory of the common language runtime (CLR) that is loaded into the process.</span></span> <span data-ttu-id="e1302-104">L’annuaire d’installation est entièrement qualifié, par exemple, "c:'windows’microsoft.net’framework’v1.0.3705".</span><span class="sxs-lookup"><span data-stu-id="e1302-104">The installation directory is fully qualified, for example, "c:\windows\microsoft.net\framework\v1.0.3705".</span></span>  
  
 <span data-ttu-id="e1302-105">Cette fonction est déconseillée.</span><span class="sxs-lookup"><span data-stu-id="e1302-105">This function is deprecated.</span></span> <span data-ttu-id="e1302-106">Il est remplacé par [l’ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) méthode fournie dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="e1302-106">It is superseded by the [ICLRRuntimeInfo::GetRuntimeDirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md) method provided in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1302-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1302-107">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (
    [out] LPWSTR  pbuffer,
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="e1302-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e1302-108">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="e1302-109">[out] Un tampon dans lequel le temps d’exécution renvoie une chaîne qui contient le nom entièrement qualifié de l’annuaire d’installation pour le temps d’exécution qui est chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e1302-109">[out] A buffer in which the runtime returns a string that contains the fully qualified name of the installation directory for the runtime that is loaded into the process.</span></span> <span data-ttu-id="e1302-110">Si le temps d’exécution n’a pas encore été chargé dans le processus, la fonction renvoie les informations d’annuaire appropriées pour la dernière version du temps d’exécution installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e1302-110">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="e1302-111">[dans] La taille, dans les `pbuffer`octets, de .</span><span class="sxs-lookup"><span data-stu-id="e1302-111">[in] The size, in bytes, of `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="e1302-112">[out] Le nombre de `pbuffer`caractères retournés dans .</span><span class="sxs-lookup"><span data-stu-id="e1302-112">[out] The number of characters returned in `pbuffer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1302-113">Notes </span><span class="sxs-lookup"><span data-stu-id="e1302-113">Remarks</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e1302-114">N’utilisez pas cette fonction dans les processus qui exécutent la version 4 du CLR.</span><span class="sxs-lookup"><span data-stu-id="e1302-114">Do not use this function in processes that are running version 4 of the CLR.</span></span> <span data-ttu-id="e1302-115">Si une version antérieure du CLR est installée sur l’ordinateur, cette fonction renvoie le répertoire d’installation pour cette version.</span><span class="sxs-lookup"><span data-stu-id="e1302-115">If an earlier version of the CLR is installed on the computer, this function returns the installation directory for that version.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1302-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="e1302-116">Requirements</span></span>  
 <span data-ttu-id="e1302-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1302-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1302-118">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="e1302-118">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e1302-119">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="e1302-119">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e1302-120">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1302-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1302-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1302-121">See also</span></span>

- [<span data-ttu-id="e1302-122">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="e1302-122">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
