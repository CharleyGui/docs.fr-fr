---
title: RunDll32ShimW, fonction
ms.date: 03/30/2017
api_name:
- RunDll32ShimW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- RunDll32ShimW
helpviewer_keywords:
- RunDll32ShimW function [.NET Framework hosting]
ms.assetid: 9ea07b57-96e2-44df-8711-8fe6c119087f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 569efa9d14ef10d8c5cf735091778a6c78882815
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781164"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="251a3-102">RunDll32ShimW, fonction</span><span class="sxs-lookup"><span data-stu-id="251a3-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="251a3-103">Exécute la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="251a3-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="251a3-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="251a3-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="251a3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="251a3-105">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="251a3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="251a3-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="251a3-107">[in] Un handle de fenêtre dans lequel la sortie de commande s’affiche.</span><span class="sxs-lookup"><span data-stu-id="251a3-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="251a3-108">[in] Handle vers la bibliothèque qui contient la commande.</span><span class="sxs-lookup"><span data-stu-id="251a3-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="251a3-109">[in] Chaîne qui spécifie la commande à exécuter.</span><span class="sxs-lookup"><span data-stu-id="251a3-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="251a3-110">[in] Entier qui spécifie le mode d’affichage de la fenêtre de sortie.</span><span class="sxs-lookup"><span data-stu-id="251a3-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="251a3-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="251a3-111">Requirements</span></span>  
 <span data-ttu-id="251a3-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="251a3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="251a3-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="251a3-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="251a3-114">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="251a3-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="251a3-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="251a3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="251a3-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="251a3-116">See also</span></span>

- [<span data-ttu-id="251a3-117">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="251a3-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
