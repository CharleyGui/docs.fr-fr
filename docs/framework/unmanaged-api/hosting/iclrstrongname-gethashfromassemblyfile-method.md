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
ms.openlocfilehash: 8131a9838cc958405ca23c75c702db5ec65a41c8
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901194"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="adb63-102">Méthode ICLRStrongName::GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="adb63-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="adb63-103">Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="adb63-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adb63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adb63-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adb63-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="adb63-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="adb63-106">dans Chemin d’accès au fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="adb63-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="adb63-107">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="adb63-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="adb63-108">Utilisez zéro pour l’algorithme de hachage par défaut.</span><span class="sxs-lookup"><span data-stu-id="adb63-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="adb63-109">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="adb63-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="adb63-110">dans Taille maximale de `pbHash`demandée.</span><span class="sxs-lookup"><span data-stu-id="adb63-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="adb63-111">à Taille retournée, en octets, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="adb63-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adb63-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="adb63-112">Return Value</span></span>  
 <span data-ttu-id="adb63-113">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="adb63-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adb63-114">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="adb63-114">Requirements</span></span>  
 <span data-ttu-id="adb63-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adb63-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adb63-116">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="adb63-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="adb63-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="adb63-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="adb63-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adb63-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adb63-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="adb63-119">See also</span></span>

- [<span data-ttu-id="adb63-120">GetHashFromAssemblyFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="adb63-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="adb63-121">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="adb63-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
