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
ms.openlocfilehash: f197c8802bd9e55391b3e3e20c64398736070a16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136333"
---
# <a name="getfileversion-function"></a><span data-ttu-id="faa7e-102">GetFileVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="faa7e-102">GetFileVersion Function</span></span>
<span data-ttu-id="faa7e-103">Obtient les informations de version du common language runtime (CLR) du fichier spécifié, à l’aide de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="faa7e-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="faa7e-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="faa7e-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faa7e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="faa7e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="faa7e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="faa7e-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="faa7e-107">dans Chemin d’accès du fichier à examiner.</span><span class="sxs-lookup"><span data-stu-id="faa7e-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="faa7e-108">[in, out] Mémoire tampon allouée pour les informations de version retournées.</span><span class="sxs-lookup"><span data-stu-id="faa7e-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="faa7e-109">dans Taille, en caractères larges, de `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="faa7e-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="faa7e-110">à Taille, en octets, de la `szBuffer`retournée.</span><span class="sxs-lookup"><span data-stu-id="faa7e-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="faa7e-111">spécifications</span><span class="sxs-lookup"><span data-stu-id="faa7e-111">Requirements</span></span>  
 <span data-ttu-id="faa7e-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="faa7e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="faa7e-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="faa7e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="faa7e-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="faa7e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa7e-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="faa7e-115">See also</span></span>

- [<span data-ttu-id="faa7e-116">Fonctions d’hébergement CLR dépréciées</span><span class="sxs-lookup"><span data-stu-id="faa7e-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
