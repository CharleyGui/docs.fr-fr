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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38f98b971e430a2c35a4c484f4f9c4bf387c640c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798954"
---
# <a name="strongnamesignaturesize-function"></a><span data-ttu-id="24066-102">StrongNameSignatureSize, fonction</span><span class="sxs-lookup"><span data-stu-id="24066-102">StrongNameSignatureSize Function</span></span>
<span data-ttu-id="24066-103">Retourne la taille de la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="24066-103">Returns the size of the strong name signature.</span></span> <span data-ttu-id="24066-104">`StrongNameSignatureSize`est généralement utilisé par les compilateurs pour déterminer la quantité d’espace à réserver dans le fichier lors de la création d’un assembly à signature différée.</span><span class="sxs-lookup"><span data-stu-id="24066-104">`StrongNameSignatureSize` is typically used by compilers to determine how much space to reserve in the file when creating a delay-signed assembly.</span></span>  
  
 <span data-ttu-id="24066-105">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="24066-105">This function has been deprecated.</span></span> <span data-ttu-id="24066-106">Utilisez la méthode [ICLRStrongName :: StrongNameSignatureSize (](../hosting/iclrstrongname-strongnamesignaturesize-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="24066-106">Use the [ICLRStrongName::StrongNameSignatureSize](../hosting/iclrstrongname-strongnamesignaturesize-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24066-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24066-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="24066-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="24066-108">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="24066-109">dans Structure de type [publicKeyBlob](publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="24066-109">[in] A structure of type [PublicKeyBlob](publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="24066-110">dans Taille, en octets, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="24066-110">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `pcbSize`  
 <span data-ttu-id="24066-111">dans Nombre d’octets requis pour stocker la signature de nom fort.</span><span class="sxs-lookup"><span data-stu-id="24066-111">[in] The number of bytes required to store the strong name signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24066-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="24066-112">Return Value</span></span>  
 <span data-ttu-id="24066-113">`true`en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="24066-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24066-114">Notes</span><span class="sxs-lookup"><span data-stu-id="24066-114">Remarks</span></span>  
 <span data-ttu-id="24066-115">Si la `StrongNameSignatureSize` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="24066-115">If the `StrongNameSignatureSize` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24066-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="24066-116">Requirements</span></span>  
 <span data-ttu-id="24066-117">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24066-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24066-118">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="24066-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="24066-119">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="24066-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="24066-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24066-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24066-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24066-121">See also</span></span>

- [<span data-ttu-id="24066-122">StrongNameSignatureSize, méthode</span><span class="sxs-lookup"><span data-stu-id="24066-122">StrongNameSignatureSize Method</span></span>](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [<span data-ttu-id="24066-123">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="24066-123">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
