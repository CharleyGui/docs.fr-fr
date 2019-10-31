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
ms.openlocfilehash: a8856790b655f071df704879a247169f456ae2f5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130872"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="c770e-102">StrongNameSignatureSize, fonction</span><span class="sxs-lookup"><span data-stu-id="c770e-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="c770e-103">Retourne la taille de la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="c770e-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="c770e-104">`StrongNameSignatureSize` est généralement utilisé par les compilateurs pour déterminer la quantité d’espace à réserver dans le fichier lors de la création d’un assembly à signature différée.</span><span class="sxs-lookup"><span data-stu-id="c770e-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="c770e-105">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="c770e-105">This function has been deprecated.</span></span> <span data-ttu-id="c770e-106">Utilisez la méthode [ICLRStrongName :: StrongNameSignatureSize (](../hosting/iclrstrongname-strongnamesignaturesize-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="c770e-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c770e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c770e-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="c770e-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c770e-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="c770e-109">dans Structure de type [publicKeyBlob](publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="c770e-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="c770e-110">dans Taille, en octets, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="c770e-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="c770e-111">dans Nombre d’octets requis pour stocker la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="c770e-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c770e-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c770e-112">Return Value</span></span>  
 <span data-ttu-id="c770e-113">`true` en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="c770e-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c770e-114">Notes</span><span class="sxs-lookup"><span data-stu-id="c770e-114">Remarks</span></span>  
 <span data-ttu-id="c770e-115">Si la fonction `StrongNameSignatureSize` ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="c770e-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c770e-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="c770e-116">Requirements</span></span>  
 <span data-ttu-id="c770e-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c770e-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c770e-118">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="c770e-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c770e-119">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c770e-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c770e-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c770e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c770e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c770e-121">See also</span></span>

- [<span data-ttu-id="c770e-122">StrongNameSignatureSize, méthode</span><span class="sxs-lookup"><span data-stu-id="c770e-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="c770e-123">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="c770e-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
