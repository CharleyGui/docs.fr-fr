---
title: PublicKeyBlob, structure
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e66196e2bd2cb326ca3f5badc67bcf8d81e5fc3c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799162"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="ad836-102">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="ad836-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="ad836-103">Représente, au format binaire, la clé publique d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="ad836-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad836-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad836-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="ad836-105">Membres</span><span class="sxs-lookup"><span data-stu-id="ad836-105">Members</span></span>  
  
|<span data-ttu-id="ad836-106">Membre</span><span class="sxs-lookup"><span data-stu-id="ad836-106">Member</span></span>|<span data-ttu-id="ad836-107">Description</span><span class="sxs-lookup"><span data-stu-id="ad836-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="ad836-108">Identificateur de l’algorithme de signature (de type `ALG_ID`, tel que défini dans wincrypt. h) de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="ad836-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="ad836-109">Identificateur de l’algorithme de hachage (de type `ALG_ID`, tel que défini dans wincrypt. h) de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="ad836-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="ad836-110">Longueur de la clé, en octets.</span><span class="sxs-lookup"><span data-stu-id="ad836-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="ad836-111">Tableau d’octets de longueur variable qui contient la valeur de clé dans le format retourné par l’CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="ad836-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ad836-112">Notes</span><span class="sxs-lookup"><span data-stu-id="ad836-112">Remarks</span></span>  
 <span data-ttu-id="ad836-113">La `PublicKeyBlob` structure est utilisée par [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)et d’autres fonctions de nom fort pour représenter la clé publique d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="ad836-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad836-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ad836-114">Requirements</span></span>  
 <span data-ttu-id="ad836-115">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad836-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad836-116">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ad836-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ad836-117">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ad836-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad836-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad836-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad836-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad836-119">See also</span></span>

- [<span data-ttu-id="ad836-120">StrongNameGetPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="ad836-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="ad836-121">StrongNameSignatureGeneration, fonction</span><span class="sxs-lookup"><span data-stu-id="ad836-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
