---
title: StrongNameGetBlobFromImage, fonction
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
ms.openlocfilehash: 41226cd909900bd2da7bdcf9b9a49567d3042b01
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73094879"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="9f72a-102">StrongNameGetBlobFromImage, fonction</span><span class="sxs-lookup"><span data-stu-id="9f72a-102">StrongNameGetBlobFromImage Function</span></span>
<span data-ttu-id="9f72a-103">Obtient une représentation binaire de l’image de l’assembly à l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9f72a-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="9f72a-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="9f72a-104">This function has been deprecated.</span></span> <span data-ttu-id="9f72a-105">Utilisez la méthode [ICLRStrongName :: StrongNameGetBlobFromImage (](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="9f72a-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f72a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f72a-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f72a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9f72a-107">Parameters</span></span>  
 `pbBase`  
 <span data-ttu-id="9f72a-108">dans Adresse mémoire du manifeste de l’assembly mappé.</span><span class="sxs-lookup"><span data-stu-id="9f72a-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="9f72a-109">dans Taille, en octets, de l’image à `pbBase`.</span><span class="sxs-lookup"><span data-stu-id="9f72a-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="9f72a-110">dans Mémoire tampon destinée à contenir la représentation binaire de l’image.</span><span class="sxs-lookup"><span data-stu-id="9f72a-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="9f72a-111">[in, out] Taille maximale demandée, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="9f72a-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="9f72a-112">Lors du retour, taille réelle, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="9f72a-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f72a-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9f72a-113">Return Value</span></span>  
 <span data-ttu-id="9f72a-114">`true` en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="9f72a-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f72a-115">Notes</span><span class="sxs-lookup"><span data-stu-id="9f72a-115">Remarks</span></span>  
 <span data-ttu-id="9f72a-116">Si la fonction `StrongNameGetBlobFromImage` ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="9f72a-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f72a-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="9f72a-117">Requirements</span></span>  
 <span data-ttu-id="9f72a-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f72a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f72a-119">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="9f72a-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9f72a-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9f72a-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f72a-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f72a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f72a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f72a-122">See also</span></span>

- [<span data-ttu-id="9f72a-123">StrongNameGetBlobFromImage, méthode</span><span class="sxs-lookup"><span data-stu-id="9f72a-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="9f72a-124">StrongNameGetBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="9f72a-124">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="9f72a-125">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="9f72a-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
