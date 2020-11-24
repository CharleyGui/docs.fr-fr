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
ms.openlocfilehash: f43a4e65442ca79ece71ce7e5e014309a611d7cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671603"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="d0cff-102">Méthode ICLRStrongName::StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="d0cff-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>

<span data-ttu-id="d0cff-103">Retourne la taille de la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="d0cff-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="d0cff-104">Cette méthode est généralement utilisée par les compilateurs pour déterminer la quantité d’espace à réserver dans le fichier lors de la création d’un assembly à signature différée.</span><span class="sxs-lookup"><span data-stu-id="d0cff-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0cff-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0cff-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d0cff-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d0cff-106">Parameters</span></span>  

 `pbPublicKeyBlob`  
 <span data-ttu-id="d0cff-107">dans Structure de type [publicKeyBlob](../strong-naming/publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="d0cff-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="d0cff-108">dans Taille, en octets, de `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="d0cff-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="d0cff-109">dans Nombre d’octets requis pour stocker la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="d0cff-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0cff-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d0cff-110">Return Value</span></span>  

 <span data-ttu-id="d0cff-111">`S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="d0cff-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0cff-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d0cff-112">Requirements</span></span>  

 <span data-ttu-id="d0cff-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0cff-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0cff-114">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="d0cff-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d0cff-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d0cff-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0cff-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0cff-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0cff-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0cff-117">See also</span></span>

- [<span data-ttu-id="d0cff-118">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="d0cff-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
