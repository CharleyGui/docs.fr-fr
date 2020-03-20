---
title: GetCORVersion, fonction
ms.date: 03/30/2017
api_name:
- GetCORVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORVersion
helpviewer_keywords:
- GetCORVersion function [.NET Framework hosting]
ms.assetid: 2f09cd37-bf3a-4cc5-87b0-adc42a7eed31
topic_type:
- apiref
ms.openlocfilehash: 1f40f27651d2d75cf2c3e4d7d1c21e1f47d402af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178188"
---
# <a name="getcorversion-function"></a><span data-ttu-id="2d463-102">GetCORVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="2d463-102">GetCORVersion Function</span></span>
<span data-ttu-id="2d463-103">Retourne le numéro de version de l’heure d’exécution de langue commune (CLR) qui est en cours d’exécution dans le processus actuel.</span><span class="sxs-lookup"><span data-stu-id="2d463-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="2d463-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="2d463-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d463-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d463-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,
    [out] DWORD*  dwlength  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="2d463-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2d463-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="2d463-107">Un pointeur vers un tampon dans lequel le CLR renvoie une chaîne spécifiant la version du temps d’exécution qui est actuellement chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="2d463-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="2d463-108">La corde retournée prend la même forme que les cordes passées à [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), par exemple, "v1.0.1216".</span><span class="sxs-lookup"><span data-stu-id="2d463-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="2d463-109">Si le temps d’exécution n’a pas encore été chargé dans le processus, la fonction renvoie les informations d’annuaire appropriées pour la dernière version du temps d’exécution installé sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2d463-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2d463-110">Le nombre de`WCHAR`caractères (s) `pbuffer`qui peuvent être conservés dans .</span><span class="sxs-lookup"><span data-stu-id="2d463-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="2d463-111">Un pointeur sur le nombre `pbuffer`de caractères effectivement retourné dans .</span><span class="sxs-lookup"><span data-stu-id="2d463-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="2d463-112">S’il `pbuffer` s’agit d’un pointeur nul, le temps de course revient E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="2d463-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="2d463-113">Si le nombre de caractères `pbuffer` est plus élevé, puis la longueur de , le temps d’exécution retourne ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="2d463-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d463-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2d463-114">Requirements</span></span>  
 <span data-ttu-id="2d463-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d463-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d463-116">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="2d463-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d463-117">**Bibliothèque:** MSCorEE.dll MSCorEE.dll MSCorEE.dll MSCor</span><span class="sxs-lookup"><span data-stu-id="2d463-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d463-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d463-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d463-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d463-119">See also</span></span>

- [<span data-ttu-id="2d463-120">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="2d463-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
