---
title: GetFileVersion, fonction
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1f5508e9ee41d8670b43d5b219846237e11fc8f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778148"
---
# <a name="getfileversion-function"></a><span data-ttu-id="9315f-102">GetFileVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="9315f-102">GetFileVersion Function</span></span>
<span data-ttu-id="9315f-103">Obtient les informations de version common language runtime (CLR) du fichier spécifié, à l’aide de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9315f-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="9315f-104">Cette fonction a été déconseillée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9315f-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9315f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9315f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9315f-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9315f-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="9315f-107">[in] Le chemin d’accès du fichier doit être examinée.</span><span class="sxs-lookup"><span data-stu-id="9315f-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="9315f-108">[in, out] La mémoire tampon allouée pour les informations de version qui sont retournées.</span><span class="sxs-lookup"><span data-stu-id="9315f-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="9315f-109">[in] La taille, en caractères larges, de `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="9315f-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="9315f-110">[out] La taille, en octets, de retourné `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="9315f-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9315f-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9315f-111">Requirements</span></span>  
 <span data-ttu-id="9315f-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9315f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9315f-113">**En-tête :** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9315f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9315f-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9315f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9315f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9315f-115">See also</span></span>

- [<span data-ttu-id="9315f-116">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="9315f-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
