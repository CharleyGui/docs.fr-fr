---
title: Méthode ICLRStrongName::StrongNameTokenFromAssembly
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
ms.openlocfilehash: 12677799136e9ca887809e58fba838cb421ea183
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901062"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="d212e-102">Méthode ICLRStrongName::StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="d212e-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="d212e-103">Crée un jeton de nom fort à partir du fichier d’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="d212e-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d212e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d212e-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d212e-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d212e-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="d212e-106">dans Chemin d’accès au fichier exécutable portable (PE) pour l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d212e-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="d212e-107">à Jeton de nom fort retourné.</span><span class="sxs-lookup"><span data-stu-id="d212e-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="d212e-108">à Taille, en octets, du jeton de nom fort.</span><span class="sxs-lookup"><span data-stu-id="d212e-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d212e-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d212e-109">Return Value</span></span>  
 <span data-ttu-id="d212e-110">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="d212e-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d212e-111">Notes</span><span class="sxs-lookup"><span data-stu-id="d212e-111">Remarks</span></span>  
 <span data-ttu-id="d212e-112">Un jeton de nom fort est la forme raccourcie d’une clé publique.</span><span class="sxs-lookup"><span data-stu-id="d212e-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="d212e-113">Le jeton est un hachage 64 bits qui est créé à partir de la clé publique utilisée pour signer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d212e-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="d212e-114">Le jeton fait partie du nom fort de l’assembly et peut être lu à partir des métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d212e-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="d212e-115">Une fois le jeton créé, vous devez appeler la méthode [ICLRStrongName :: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) pour libérer la mémoire allouée.</span><span class="sxs-lookup"><span data-stu-id="d212e-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d212e-116">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d212e-116">Requirements</span></span>  
 <span data-ttu-id="d212e-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d212e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d212e-118">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="d212e-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d212e-119">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d212e-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d212e-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d212e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d212e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d212e-121">See also</span></span>

- [<span data-ttu-id="d212e-122">StrongNameTokenFromAssemblyEx, méthode</span><span class="sxs-lookup"><span data-stu-id="d212e-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="d212e-123">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="d212e-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
