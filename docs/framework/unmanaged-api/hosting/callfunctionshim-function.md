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
ms.openlocfilehash: f72c987294d7768eacf112c622ab15494fb75e34
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685784"
---
# <a name="callfunctionshim-function"></a><span data-ttu-id="faad5-102">CallFunctionShim, fonction</span><span class="sxs-lookup"><span data-stu-id="faad5-102">CallFunctionShim Function</span></span>

<span data-ttu-id="faad5-103">Effectue un appel à la fonction qui a le nom et les paramètres spécifiés dans la bibliothèque spécifiée.</span><span class="sxs-lookup"><span data-stu-id="faad5-103">Makes a call to the function that has the specified name and parameters in the specified library.</span></span>  
  
 <span data-ttu-id="faad5-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="faad5-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faad5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faad5-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="faad5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="faad5-106">Parameters</span></span>  

 `szDllName`  
 <span data-ttu-id="faad5-107">dans Nom de la bibliothèque contenant la fonction.</span><span class="sxs-lookup"><span data-stu-id="faad5-107">[in] The name of the library containing the function.</span></span>  
  
 `szFunctionName`  
 <span data-ttu-id="faad5-108">dans Nom de la fonction.</span><span class="sxs-lookup"><span data-stu-id="faad5-108">[in] The name of the function.</span></span>  
  
 `lpvArgument1`  
 <span data-ttu-id="faad5-109">dans Premier argument à passer à la fonction.</span><span class="sxs-lookup"><span data-stu-id="faad5-109">[in] The first argument to pass to the function.</span></span>  
  
 `lpvArgument2`  
 <span data-ttu-id="faad5-110">dans Deuxième argument à passer à la fonction.</span><span class="sxs-lookup"><span data-stu-id="faad5-110">[in] The second argument to pass to the function.</span></span>  
  
 `szVersion`  
 <span data-ttu-id="faad5-111">dans Version de la bibliothèque qui contient la fonction.</span><span class="sxs-lookup"><span data-stu-id="faad5-111">[in] The version of the library that contains the function.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="faad5-112">[in] Réservé pour une future utilisation.</span><span class="sxs-lookup"><span data-stu-id="faad5-112">[in] Reserved for future use.</span></span> <span data-ttu-id="faad5-113">Transmettez zéro dans ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="faad5-113">Pass zero in this parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faad5-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="faad5-114">Requirements</span></span>  

 <span data-ttu-id="faad5-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faad5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faad5-116">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="faad5-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="faad5-117">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="faad5-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="faad5-118">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faad5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faad5-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="faad5-119">See also</span></span>

- [<span data-ttu-id="faad5-120">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="faad5-120">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
