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
ms.openlocfilehash: 1283abaf6b08af1d842d8fe4469f7f6c15e38ec5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136420"
---
# <a name="getcorversion-function"></a><span data-ttu-id="9d7f6-102">GetCORVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="9d7f6-102">GetCORVersion Function</span></span>
<span data-ttu-id="9d7f6-103">Retourne le numéro de version du common language runtime (CLR) qui s’exécute dans le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-103">Returns the version number of the common language runtime (CLR) that is running in the current process.</span></span>  
  
 <span data-ttu-id="9d7f6-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d7f6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d7f6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORVersion (  
    [in] LPWSTR  pbuffer,  
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="9d7f6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d7f6-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="9d7f6-107">Pointeur vers une mémoire tampon dans laquelle le CLR retourne une chaîne spécifiant la version du runtime actuellement chargée dans le processus.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-107">A pointer to a buffer in which the CLR returns a string specifying the version of the runtime that is currently loaded into the process.</span></span> <span data-ttu-id="9d7f6-108">La chaîne retournée prend la même forme que les chaînes passées à [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), par exemple, « v 1.0.1216 ».</span><span class="sxs-lookup"><span data-stu-id="9d7f6-108">The returned string takes the same form as strings passed to [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md), for example, "v1.0.1216".</span></span> <span data-ttu-id="9d7f6-109">Si le runtime n’a pas encore été chargé dans le processus, la fonction retourne les informations de répertoire appropriées pour la version la plus récente du runtime installée sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-109">If the runtime has not yet been loaded into the process, the function returns the appropriate directory information for the latest version of the runtime installed on the computer.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="9d7f6-110">Nombre de caractères (`WCHAR`s) qui peuvent être contenus dans `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-110">The number of characters (`WCHAR`s) that can be held in `pbuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="9d7f6-111">Pointeur vers le nombre de caractères réellement retournés dans `pbuffer`.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-111">A pointer to the number of characters actually returned in `pbuffer`.</span></span> <span data-ttu-id="9d7f6-112">Si `pbuffer` est un pointeur null, le runtime retourne E_POINTER.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-112">If `pbuffer` is a null pointer, the runtime returns E_POINTER.</span></span> <span data-ttu-id="9d7f6-113">Si le nombre de caractères est supérieur à la longueur de `pbuffer`, le runtime retourne ERROR_INSUFFICIENT_BUFFER.</span><span class="sxs-lookup"><span data-stu-id="9d7f6-113">If the number of characters is greater then the length of `pbuffer` , the runtime returns ERROR_INSUFFICIENT_BUFFER.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d7f6-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="9d7f6-114">Requirements</span></span>  
 <span data-ttu-id="9d7f6-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d7f6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d7f6-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9d7f6-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9d7f6-117">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9d7f6-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9d7f6-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d7f6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d7f6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d7f6-119">See also</span></span>

- [<span data-ttu-id="9d7f6-120">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="9d7f6-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
