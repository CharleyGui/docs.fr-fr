---
title: StrongNameSignatureSize, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
ms.openlocfilehash: a19d875b8fb81f2af3821e69452f0f0ed591cd22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176888"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="82955-102">StrongNameSignatureSize, fonction</span><span class="sxs-lookup"><span data-stu-id="82955-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="82955-103">Retourne la taille de la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="82955-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="82955-104">`StrongNameSignatureSize`est généralement utilisé par les compilateurs pour déterminer combien d’espace réserver dans le fichier lors de la création d’un assemblage signé retard.</span><span class="sxs-lookup"><span data-stu-id="82955-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="82955-105">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="82955-105">This function has been deprecated.</span></span> <span data-ttu-id="82955-106">Utilisez la méthode [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="82955-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82955-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82955-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,
    [in]  DWORD  *pcbSize  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="82955-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="82955-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="82955-109">[dans] Une structure de type [PublicKeyBlob](publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="82955-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="82955-110">[dans] La taille, dans les `pbPublicKeyBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="82955-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="82955-111">[dans] Le nombre d’octets requis pour stocker la signature du nom fort.</span><span class="sxs-lookup"><span data-stu-id="82955-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82955-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="82955-112">Return Value</span></span>  
 <span data-ttu-id="82955-113">`true`à la réussite; autrement, `false`.</span><span class="sxs-lookup"><span data-stu-id="82955-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82955-114">Notes </span><span class="sxs-lookup"><span data-stu-id="82955-114">Remarks</span></span>  
 <span data-ttu-id="82955-115">Si `StrongNameSignatureSize` la fonction ne se termine pas avec succès, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="82955-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82955-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="82955-116">Requirements</span></span>  
 <span data-ttu-id="82955-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82955-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82955-118">**En-tête:** StrongName.h (en)</span><span class="sxs-lookup"><span data-stu-id="82955-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="82955-119">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="82955-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82955-120">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82955-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82955-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82955-121">See also</span></span>

- [<span data-ttu-id="82955-122">StrongNameSignatureSize, méthode</span><span class="sxs-lookup"><span data-stu-id="82955-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="82955-123">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="82955-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
