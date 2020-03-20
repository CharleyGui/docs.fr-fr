---
title: Méthode ICLRStrongName::StrongNameSignatureSize
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureSize
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureSize method [.NET Framework hosting]
- StrongNameSignatureSize method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 76d4f93a-5e25-4399-abcc-a1389549481d
topic_type:
- apiref
ms.openlocfilehash: e789996af3aedd17251fc52cde52a336f65053ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176342"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="c7902-102">Méthode ICLRStrongName::StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="c7902-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="c7902-103">Retourne la taille de la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="c7902-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="c7902-104">Cette méthode est généralement utilisée par les compilateurs pour déterminer combien d’espace réserver dans le fichier lors de la création d’un assemblage signé retard.</span><span class="sxs-lookup"><span data-stu-id="c7902-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7902-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7902-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="c7902-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7902-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="c7902-107">[dans] Une structure de type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="c7902-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="c7902-108">[dans] La taille, dans les `pbPublicKeyBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="c7902-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="c7902-109">[dans] Le nombre d’octets requis pour stocker la signature du nom fort.</span><span class="sxs-lookup"><span data-stu-id="c7902-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7902-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c7902-110">Return Value</span></span>  
 <span data-ttu-id="c7902-111">`S_OK`si la méthode est terminée avec succès; autrement, une valeur HRESULT qui indique l’échec (voir [valeurs RHESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="c7902-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7902-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c7902-112">Requirements</span></span>  
 <span data-ttu-id="c7902-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7902-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7902-114">**En-tête:** MetaHost.h MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c7902-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c7902-115">**Bibliothèque:** Inclus comme une ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7902-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7902-116">**.NET Versions-cadre:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7902-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7902-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7902-117">See also</span></span>

- [<span data-ttu-id="c7902-118">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="c7902-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
