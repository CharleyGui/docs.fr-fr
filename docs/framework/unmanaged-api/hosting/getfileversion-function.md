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
ms.openlocfilehash: f3b51c1b376fa9c664de53aa76ec724ca305ae6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178177"
---
# <a name="getfileversion-function"></a><span data-ttu-id="23269-102">GetFileVersion, fonction</span><span class="sxs-lookup"><span data-stu-id="23269-102">GetFileVersion Function</span></span>
<span data-ttu-id="23269-103">Obtient les informations courantes de version de l’heure d’exécution de langue (CLR) du fichier spécifié, en utilisant le tampon spécifié.</span><span class="sxs-lookup"><span data-stu-id="23269-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="23269-104">Cette fonction a été dépréciée dans le cadre .NET 4.</span><span class="sxs-lookup"><span data-stu-id="23269-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23269-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23269-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23269-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="23269-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="23269-107">[dans] La voie du dossier à examiner.</span><span class="sxs-lookup"><span data-stu-id="23269-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="23269-108">[dans, dehors] Le tampon alloué pour les informations de version qui sont retournées.</span><span class="sxs-lookup"><span data-stu-id="23269-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="23269-109">[dans] La taille, en caractères larges, de `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="23269-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="23269-110">[out] La taille, dans les octets, du retour `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="23269-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23269-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="23269-111">Requirements</span></span>  
 <span data-ttu-id="23269-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23269-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23269-113">**En-tête:** MSCorEE.h MSCorEE.h MSCorEE.h MSCor</span><span class="sxs-lookup"><span data-stu-id="23269-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23269-114">**.NET Versions-cadre:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23269-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23269-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23269-115">See also</span></span>

- [<span data-ttu-id="23269-116">Fonction d'hébergement du CLR déconseillées</span><span class="sxs-lookup"><span data-stu-id="23269-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
