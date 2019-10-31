---
title: CallFunctionShim, fonction
ms.date: 03/30/2017
api_name:
- CallFunctionShim
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CallFunctionShim
helpviewer_keywords:
- CallfunctionShim function [.NET Framework hosting]
ms.assetid: 37118465-ddf3-41f0-bf27-335b72777e63
topic_type:
- apiref
ms.openlocfilehash: d39e15a2ba71ba0c0147482259f5618dcb5d298b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192092"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="6b7b3-102">CallFunctionShim, fonction</span><span class="sxs-lookup"><span data-stu-id="6b7b3-102">CallFunctionShim Function</span></span>
<span data-ttu-id="6b7b3-103">Effectue un appel à la fonction qui a le nom et les paramètres spécifiés dans la bibliothèque spécifiée.</span><span class="sxs-lookup"><span data-stu-id="6b7b3-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="6b7b3-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="6b7b3-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b7b3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b7b3-105">Syntax</span></span>  
  
```cpp  
HRESULT CallFunctionShim (  
    [in] LPCWSTR     szDllName,  
    [in] LPCSTR      szFunctionName,  
    [in] LPVOID      lpvArgument1,  
    [in] LPVOID      lpvArgument2,  
    [in] LPCWSTR     szVersion,  
    [in] LPVOID      pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b7b3-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6b7b3-106">Parameters</span></span>  
 `szDllName`  
 <span data-ttu-id="6b7b3-107">dans Nom de la bibliothèque contenant la fonction.</span><span class="sxs-lookup"><span data-stu-id="6b7b3-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="6b7b3-108">dans Nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="6b7b3-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="6b7b3-109">dans Premier argument à passer à la fonction.</span><span class="sxs-lookup"><span data-stu-id="6b7b3-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="6b7b3-110">dans Deuxième argument à passer à la fonction.</span><span class="sxs-lookup"><span data-stu-id="6b7b3-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="6b7b3-111">dans Version de la bibliothèque qui contient la fonction.</span><span class="sxs-lookup"><span data-stu-id="6b7b3-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="6b7b3-112">dans Réservé pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="6b7b3-112">[in] Reserved for future use.</span></span> <span data-ttu-id="6b7b3-113">Transmettez zéro dans ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="6b7b3-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b7b3-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="6b7b3-114">Requirements</span></span>  
 <span data-ttu-id="6b7b3-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b7b3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b7b3-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6b7b3-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b7b3-117">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="6b7b3-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b7b3-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b7b3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b7b3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b7b3-119">See also</span></span>

- [<span data-ttu-id="6b7b3-120">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="6b7b3-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
