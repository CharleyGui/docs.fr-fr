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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8597b68b75d2b5f77f68fc13c3fb78bfdae46178
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736291"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="ace9e-102">GetCORRequiredVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="ace9e-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="ace9e-103">Obtient le numéro de version de runtime (CLR) de langage commun requis.</span><span class="sxs-lookup"><span data-stu-id="ace9e-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="ace9e-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ace9e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ace9e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ace9e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ace9e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ace9e-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="ace9e-107">[out] Une mémoire tampon qui contient une chaîne qui spécifie le numéro de version.</span><span class="sxs-lookup"><span data-stu-id="ace9e-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="ace9e-108">[in] La taille, en octets, de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="ace9e-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="ace9e-109">[out] Le nombre d’octets retournés dans la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="ace9e-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ace9e-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ace9e-110">Requirements</span></span>  
 <span data-ttu-id="ace9e-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ace9e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ace9e-112">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ace9e-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ace9e-113">**Bibliothèque :** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ace9e-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ace9e-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ace9e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace9e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ace9e-115">See also</span></span>

- [<span data-ttu-id="ace9e-116">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="ace9e-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
