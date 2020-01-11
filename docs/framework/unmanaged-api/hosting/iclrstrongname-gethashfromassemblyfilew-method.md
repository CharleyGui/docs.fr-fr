---
title: Méthode ICLRStrongName::GetHashFromAssemblyFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
ms.openlocfilehash: d98181e0d43206bfbf96182d7e4acf33da486348
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901174"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="2419f-102">Méthode ICLRStrongName::GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="2419f-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="2419f-103">Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="2419f-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2419f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2419f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2419f-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="2419f-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="2419f-106">dans Chemin d’accès au fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="2419f-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="2419f-107">Ce paramètre doit être une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="2419f-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2419f-108">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="2419f-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2419f-109">Utilisez zéro pour l’algorithme de hachage par défaut.</span><span class="sxs-lookup"><span data-stu-id="2419f-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2419f-110">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="2419f-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2419f-111">dans Taille maximale de `pbHash`demandée.</span><span class="sxs-lookup"><span data-stu-id="2419f-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2419f-112">à Taille retournée, en octets, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2419f-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2419f-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2419f-113">Return Value</span></span>  
 <span data-ttu-id="2419f-114">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="2419f-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2419f-115">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="2419f-115">Requirements</span></span>  
 <span data-ttu-id="2419f-116">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2419f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2419f-117">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="2419f-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2419f-118">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2419f-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2419f-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2419f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2419f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2419f-120">See also</span></span>

- [<span data-ttu-id="2419f-121">GetHashFromAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="2419f-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="2419f-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="2419f-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
