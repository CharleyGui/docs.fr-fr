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
ms.openlocfilehash: 7f6865c3d6dffa3b551d4e5e0636b1e386be8baa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134982"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="a1c55-102">Méthode ICLRStrongName::StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="a1c55-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="a1c55-103">Retourne la taille de la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="a1c55-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="a1c55-104">Cette méthode est généralement utilisée par les compilateurs pour déterminer la quantité d’espace à réserver dans le fichier lors de la création d’un assembly à signature différée.</span><span class="sxs-lookup"><span data-stu-id="a1c55-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1c55-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1c55-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="a1c55-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1c55-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="a1c55-107">dans Structure de type [publicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="a1c55-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="a1c55-108">dans Taille, en octets, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="a1c55-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="a1c55-109">dans Nombre d’octets requis pour stocker la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="a1c55-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1c55-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a1c55-110">Return Value</span></span>  
 <span data-ttu-id="a1c55-111">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](https://go.microsoft.com/fwlink/?LinkId=213878) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="a1c55-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1c55-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="a1c55-112">Requirements</span></span>  
 <span data-ttu-id="a1c55-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1c55-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1c55-114">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="a1c55-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a1c55-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a1c55-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1c55-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1c55-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1c55-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1c55-117">See also</span></span>

- [<span data-ttu-id="a1c55-118">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="a1c55-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
