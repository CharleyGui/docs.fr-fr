---
title: GetCORRequiredVersion, fonction
ms.date: 03/30/2017
api_name:
- GetCORRequiredVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetCORRequiredVersion
helpviewer_keywords:
- GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type:
- apiref
ms.openlocfilehash: 661eb758e1651901bb56810640a68f0de0b4e851
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136478"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="8c603-102">GetCORRequiredVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="8c603-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="8c603-103">Obtient le numéro de version du common language runtime (CLR) requis.</span><span class="sxs-lookup"><span data-stu-id="8c603-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="8c603-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8c603-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c603-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c603-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c603-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c603-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="8c603-107">à Mémoire tampon contenant une chaîne qui spécifie le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="8c603-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="8c603-108">dans Taille, en octets, de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="8c603-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="8c603-109">à Nombre d’octets retournés dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="8c603-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c603-110">spécifications</span><span class="sxs-lookup"><span data-stu-id="8c603-110">Requirements</span></span>  
 <span data-ttu-id="8c603-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c603-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c603-112">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8c603-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c603-113">**Bibliothèque :** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8c603-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c603-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c603-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c603-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c603-115">See also</span></span>

- [<span data-ttu-id="8c603-116">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="8c603-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
