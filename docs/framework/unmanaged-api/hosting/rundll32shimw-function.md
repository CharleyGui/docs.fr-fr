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
ms.openlocfilehash: e661bd82ecf6d804e852cca4a4478084edf303c5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141500"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="40c89-102">RunDll32ShimW, fonction</span><span class="sxs-lookup"><span data-stu-id="40c89-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="40c89-103">Exécute la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="40c89-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="40c89-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="40c89-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c89-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40c89-105">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40c89-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="40c89-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="40c89-107">dans Handle d’une fenêtre dans laquelle le résultat de la commande s’affiche.</span><span class="sxs-lookup"><span data-stu-id="40c89-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="40c89-108">dans Handle de la bibliothèque qui contient la commande.</span><span class="sxs-lookup"><span data-stu-id="40c89-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="40c89-109">dans Chaîne qui spécifie la commande à exécuter.</span><span class="sxs-lookup"><span data-stu-id="40c89-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="40c89-110">dans Entier qui spécifie le mode d’affichage pour la fenêtre sortie.</span><span class="sxs-lookup"><span data-stu-id="40c89-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c89-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="40c89-111">Requirements</span></span>  
 <span data-ttu-id="40c89-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40c89-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c89-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40c89-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40c89-114">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="40c89-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40c89-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40c89-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c89-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40c89-116">See also</span></span>

- [<span data-ttu-id="40c89-117">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="40c89-117">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
