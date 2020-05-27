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
ms.openlocfilehash: 90304eb94e6f53d3132c97f5ababdc45f6053d7c
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006569"
---
# <a name="rundll32shimw-function"></a><span data-ttu-id="fba71-102">RunDll32ShimW, fonction</span><span class="sxs-lookup"><span data-stu-id="fba71-102">RunDll32ShimW Function</span></span>
<span data-ttu-id="fba71-103">Exécute la commande spécifiée.</span><span class="sxs-lookup"><span data-stu-id="fba71-103">Executes the specified command.</span></span>  
  
 <span data-ttu-id="fba71-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="fba71-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fba71-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fba71-105">Syntax</span></span>  
  
```cpp  
HRESULT RunDll32ShimW (  
    [in] HWND        hwnd,  
    [in] HINSTANCE   hinst,  
    [in] LPCWSTR     lpszCmdLine,  
    [in] int         nCmdShow  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fba71-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fba71-106">Parameters</span></span>  
 `hwnd`  
 <span data-ttu-id="fba71-107">dans Handle d’une fenêtre dans laquelle le résultat de la commande s’affiche.</span><span class="sxs-lookup"><span data-stu-id="fba71-107">[in] A handle to a window in which the command output will be displayed.</span></span>  
  
 `hinst`  
 <span data-ttu-id="fba71-108">dans Handle de la bibliothèque qui contient la commande.</span><span class="sxs-lookup"><span data-stu-id="fba71-108">[in] A handle to the library that contains the command.</span></span>  
  
 `lpszCmdLine`  
 <span data-ttu-id="fba71-109">dans Chaîne qui spécifie la commande à exécuter.</span><span class="sxs-lookup"><span data-stu-id="fba71-109">[in] A string that specifies the command to be executed.</span></span>  
  
 `nCmdShow`  
 <span data-ttu-id="fba71-110">dans Entier qui spécifie le mode d’affichage pour la fenêtre sortie.</span><span class="sxs-lookup"><span data-stu-id="fba71-110">[in] An integer that specifies the display mode for the output window.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fba71-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fba71-111">Requirements</span></span>  
 <span data-ttu-id="fba71-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fba71-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fba71-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fba71-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fba71-114">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fba71-114">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fba71-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fba71-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba71-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fba71-116">See also</span></span>

- [<span data-ttu-id="fba71-117">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="fba71-117">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
