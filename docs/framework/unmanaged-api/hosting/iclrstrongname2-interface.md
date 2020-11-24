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
ms.openlocfilehash: df570f32d694ec21e9642e75b4965e169afaccfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677646"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="054f7-102">ICLRStrongName2, interface</span><span class="sxs-lookup"><span data-stu-id="054f7-102">ICLRStrongName2 Interface</span></span>

<span data-ttu-id="054f7-103">Offre la possibilité de créer des noms forts à l’aide du groupe SHA-2 d’algorithmes de hachage sécurisé (SHA-256, SHA-384 et SHA-512).</span><span class="sxs-lookup"><span data-stu-id="054f7-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="054f7-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="054f7-104">Methods</span></span>  
  
|<span data-ttu-id="054f7-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="054f7-105">Method</span></span>|<span data-ttu-id="054f7-106">Description</span><span class="sxs-lookup"><span data-stu-id="054f7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="054f7-107">StrongNameGetPublicKeyEx, méthode</span><span class="sxs-lookup"><span data-stu-id="054f7-107">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="054f7-108">Obtient la clé publique à partir d’une paire de clés publique/privée et spécifie un algorithme de hachage et un algorithme de signature.</span><span class="sxs-lookup"><span data-stu-id="054f7-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="054f7-109">StrongNameSignatureVerificationEx2, méthode</span><span class="sxs-lookup"><span data-stu-id="054f7-109">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="054f7-110">Vérifie la signature d’un assembly avec un nom fort et fournit un mappage de la clé ECMA à une clé réelle.</span><span class="sxs-lookup"><span data-stu-id="054f7-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="054f7-111">Notes</span><span class="sxs-lookup"><span data-stu-id="054f7-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="054f7-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="054f7-112">Requirements</span></span>  

 <span data-ttu-id="054f7-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="054f7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="054f7-114">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="054f7-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="054f7-115">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="054f7-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="054f7-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="054f7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
