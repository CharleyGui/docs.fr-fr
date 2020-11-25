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
ms.openlocfilehash: 57b30824c7849127f48d4da61872945366e7141e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733241"
---
# <a name="getfileversion-function"></a><span data-ttu-id="c0454-102">GetFileVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="c0454-102">GetFileVersion Function</span></span>

<span data-ttu-id="c0454-103">Obtient les informations de version du common language runtime (CLR) du fichier spécifié, à l’aide de la mémoire tampon spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c0454-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="c0454-104">Cette fonction a été dépréciée dans le .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c0454-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0454-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c0454-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0454-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c0454-106">Parameters</span></span>  

 `szFilename`  
 <span data-ttu-id="c0454-107">dans Chemin d’accès du fichier à examiner.</span><span class="sxs-lookup"><span data-stu-id="c0454-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="c0454-108">[in, out] Mémoire tampon allouée pour les informations de version retournées.</span><span class="sxs-lookup"><span data-stu-id="c0454-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="c0454-109">dans Taille, en caractères larges, de `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="c0454-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="c0454-110">à Taille, en octets, du retourné `szBuffer` .</span><span class="sxs-lookup"><span data-stu-id="c0454-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0454-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c0454-111">Requirements</span></span>  

 <span data-ttu-id="c0454-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0454-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0454-113">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c0454-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c0454-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0454-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0454-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0454-115">See also</span></span>

- [<span data-ttu-id="c0454-116">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="c0454-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
