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
ms.openlocfilehash: 6c58a0726e0869178838999c6b000e0ad975f145
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140605"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="05cd1-102">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="05cd1-102">PublicKeyBlob Structure</span></span>
<span data-ttu-id="05cd1-103">Représente, au format binaire, la clé publique d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="05cd1-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05cd1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05cd1-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a><span data-ttu-id="05cd1-105">Membres</span><span class="sxs-lookup"><span data-stu-id="05cd1-105">Members</span></span>  
  
|<span data-ttu-id="05cd1-106">Membre</span><span class="sxs-lookup"><span data-stu-id="05cd1-106">Member</span></span>|<span data-ttu-id="05cd1-107">Description</span><span class="sxs-lookup"><span data-stu-id="05cd1-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="05cd1-108">Identificateur de l’algorithme de signature (de type `ALG_ID`, tel que défini dans WinCrypt. h) de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="05cd1-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="05cd1-109">Identificateur de l’algorithme de hachage (de type `ALG_ID`, tel que défini dans WinCrypt. h) de la clé publique.</span><span class="sxs-lookup"><span data-stu-id="05cd1-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="05cd1-110">Longueur de la clé, en octets.</span><span class="sxs-lookup"><span data-stu-id="05cd1-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="05cd1-111">Tableau d’octets de longueur variable qui contient la valeur de clé dans le format retourné par l’CryptoAPI.</span><span class="sxs-lookup"><span data-stu-id="05cd1-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05cd1-112">Notes</span><span class="sxs-lookup"><span data-stu-id="05cd1-112">Remarks</span></span>  
 <span data-ttu-id="05cd1-113">La structure `PublicKeyBlob` est utilisée par [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)et d’autres fonctions Strong Name pour représenter la clé publique d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="05cd1-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05cd1-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="05cd1-114">Requirements</span></span>  
 <span data-ttu-id="05cd1-115">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05cd1-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05cd1-116">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="05cd1-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="05cd1-117">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="05cd1-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="05cd1-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05cd1-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05cd1-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="05cd1-119">See also</span></span>

- [<span data-ttu-id="05cd1-120">StrongNameGetPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="05cd1-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="05cd1-121">StrongNameSignatureGeneration, fonction</span><span class="sxs-lookup"><span data-stu-id="05cd1-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
