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
ms.openlocfilehash: edce771b3c36f2c56637aa2a21fe524be0ae12c8
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763018"
---
# <a name="iclrstrongnamestrongnamesignaturesize-method"></a><span data-ttu-id="d978e-102">Méthode ICLRStrongName::StrongNameSignatureSize</span><span class="sxs-lookup"><span data-stu-id="d978e-102">ICLRStrongName::StrongNameSignatureSize Method</span></span>
<span data-ttu-id="d978e-103">Retourne la taille de la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="d978e-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="d978e-104">Cette méthode est généralement utilisée par les compilateurs pour déterminer la quantité d’espace à réserver dans le fichier lors de la création d’un assembly à signature différée.</span><span class="sxs-lookup"><span data-stu-id="d978e-104">This method is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d978e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d978e-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="d978e-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d978e-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="d978e-107">dans Structure de type [publicKeyBlob](../strong-naming/publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="d978e-107">[in] A structure of type [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="d978e-108">dans Taille, en octets, de `pbPublicKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="d978e-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="d978e-109">dans Nombre d’octets requis pour stocker la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="d978e-109">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d978e-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d978e-110">Return Value</span></span>  
 <span data-ttu-id="d978e-111">`S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="d978e-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d978e-112">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="d978e-112">Requirements</span></span>  
 <span data-ttu-id="d978e-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d978e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d978e-114">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="d978e-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="d978e-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d978e-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d978e-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d978e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d978e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d978e-117">See also</span></span>

- [<span data-ttu-id="d978e-118">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="d978e-118">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
