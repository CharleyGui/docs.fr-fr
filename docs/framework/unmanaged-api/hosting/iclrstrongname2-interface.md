---
title: ICLRStrongName2, interface
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
ms.openlocfilehash: bc871c29f53a9ea4451a0fc1c747939724b0da87
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092244"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="37c5a-102">ICLRStrongName2, interface</span><span class="sxs-lookup"><span data-stu-id="37c5a-102">ICLRStrongName2 Interface</span></span>
<span data-ttu-id="37c5a-103">Offre la possibilité de créer des noms forts à l’aide du groupe SHA-2 d’algorithmes de hachage sécurisé (SHA-256, SHA-384 et SHA-512).</span><span class="sxs-lookup"><span data-stu-id="37c5a-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37c5a-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="37c5a-104">Methods</span></span>  
  
|<span data-ttu-id="37c5a-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="37c5a-105">Method</span></span>|<span data-ttu-id="37c5a-106">Description</span><span class="sxs-lookup"><span data-stu-id="37c5a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37c5a-107">StrongNameGetPublicKeyEx, méthode</span><span class="sxs-lookup"><span data-stu-id="37c5a-107">StrongNameGetPublicKeyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|<span data-ttu-id="37c5a-108">Obtient la clé publique à partir d’une paire de clés publique/privée et spécifie un algorithme de hachage et un algorithme de signature.</span><span class="sxs-lookup"><span data-stu-id="37c5a-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="37c5a-109">StrongNameSignatureVerificationEx2, méthode</span><span class="sxs-lookup"><span data-stu-id="37c5a-109">StrongNameSignatureVerificationEx2 Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|<span data-ttu-id="37c5a-110">Vérifie la signature d’un assembly avec un nom fort et fournit un mappage de la clé ECMA à une clé réelle.</span><span class="sxs-lookup"><span data-stu-id="37c5a-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37c5a-111">Notes</span><span class="sxs-lookup"><span data-stu-id="37c5a-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37c5a-112">spécifications</span><span class="sxs-lookup"><span data-stu-id="37c5a-112">Requirements</span></span>  
 <span data-ttu-id="37c5a-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37c5a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37c5a-114">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="37c5a-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="37c5a-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="37c5a-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37c5a-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37c5a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
