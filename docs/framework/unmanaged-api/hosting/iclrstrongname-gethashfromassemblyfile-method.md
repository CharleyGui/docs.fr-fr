---
title: Méthode ICLRStrongName::GetHashFromAssemblyFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6d5ea24e40357205051188b68de8b973d2cec18
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748251"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="ab5df-102">Méthode ICLRStrongName::GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="ab5df-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="ab5df-103">Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="ab5df-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab5df-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab5df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab5df-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ab5df-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="ab5df-106">[in] Le chemin d’accès au fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="ab5df-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ab5df-107">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="ab5df-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="ab5df-108">Utilisez zéro pour l’algorithme de hachage par défaut.</span><span class="sxs-lookup"><span data-stu-id="ab5df-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ab5df-109">[out] La mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="ab5df-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ab5df-110">[in] La taille maximale demandée de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ab5df-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ab5df-111">[out] L’a retourné la taille, en octets, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ab5df-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab5df-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="ab5df-112">Return Value</span></span>  
 <span data-ttu-id="ab5df-113">`S_OK` Si la méthode a réussi ; Sinon, une valeur HRESULT qui indique un échec (consultez [valeurs HRESULT courantes](https://go.microsoft.com/fwlink/?LinkId=213878) pour obtenir la liste).</span><span class="sxs-lookup"><span data-stu-id="ab5df-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab5df-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ab5df-114">Requirements</span></span>  
 <span data-ttu-id="ab5df-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab5df-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab5df-116">**En-tête :** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="ab5df-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ab5df-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab5df-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab5df-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab5df-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab5df-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab5df-119">See also</span></span>

- [<span data-ttu-id="ab5df-120">GetHashFromAssemblyFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="ab5df-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="ab5df-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ab5df-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
