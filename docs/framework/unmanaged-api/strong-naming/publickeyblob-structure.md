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
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176953"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="b8fc6-102">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="b8fc6-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="b8fc6-103">Représente, en format binaire, la clé publique d’une paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="b8fc6-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8fc6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8fc6-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="b8fc6-105">Membres</span><span class="sxs-lookup"><span data-stu-id="b8fc6-105">Members</span></span>  
  
|<span data-ttu-id="b8fc6-106">Membre</span><span class="sxs-lookup"><span data-stu-id="b8fc6-106">Member</span></span>|<span data-ttu-id="b8fc6-107">Description</span><span class="sxs-lookup"><span data-stu-id="b8fc6-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="b8fc6-108">L’identifiant pour l’algorithme `ALG_ID`de signature (de type , tel que défini dans WinCrypt.h) de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="b8fc6-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="b8fc6-109">L’identifiant pour l’algorithme `ALG_ID`de hachage (de type , tel que défini dans WinCrypt.h) de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="b8fc6-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="b8fc6-110">La longueur de la clé dans les octets.</span><span class="sxs-lookup"><span data-stu-id="b8fc6-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="b8fc6-111">Un tableau d’endlète à longueur variable qui contient la valeur clé dans le format retourné par le CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="b8fc6-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8fc6-112">Notes </span><span class="sxs-lookup"><span data-stu-id="b8fc6-112">Remarks</span></span>  
 <span data-ttu-id="b8fc6-113">La `PublicKeyBlob` structure est utilisée par [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), et d’autres fonctions de nom forte pour représenter la clé publique d’une paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="b8fc6-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8fc6-114">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b8fc6-114">Requirements</span></span>  
 <span data-ttu-id="b8fc6-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8fc6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8fc6-116">**En-tête:** StrongName.h (en)</span><span class="sxs-lookup"><span data-stu-id="b8fc6-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b8fc6-117">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8fc6-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b8fc6-118">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8fc6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8fc6-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b8fc6-119">See also</span></span>

- [<span data-ttu-id="b8fc6-120">StrongNameGetPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="b8fc6-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="b8fc6-121">StrongNameSignatureGeneration, fonction</span><span class="sxs-lookup"><span data-stu-id="b8fc6-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
