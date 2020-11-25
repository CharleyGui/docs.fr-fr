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
ms.openlocfilehash: 3a84221f94bad76d69f0dc67fe695ada3f3862f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732240"
---
# <a name="strongnamegetblobfromimage-function"></a><span data-ttu-id="c5f3d-102">StrongNameGetBlobFromImage, fonction</span><span class="sxs-lookup"><span data-stu-id="c5f3d-102">StrongNameGetBlobFromImage Function</span></span>

<span data-ttu-id="c5f3d-103">Obtient une représentation binaire de l’image de l’assembly à l’adresse mémoire spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c5f3d-103">Gets a binary representation of the assembly image at the specified memory address.</span></span>  
  
 <span data-ttu-id="c5f3d-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="c5f3d-104">This function has been deprecated.</span></span> <span data-ttu-id="c5f3d-105">Utilisez la méthode [ICLRStrongName :: StrongNameGetBlobFromImage (](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="c5f3d-105">Use the [ICLRStrongName::StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5f3d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5f3d-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5f3d-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c5f3d-107">Parameters</span></span>  

 `pbBase`  
 <span data-ttu-id="c5f3d-108">dans Adresse mémoire du manifeste de l’assembly mappé.</span><span class="sxs-lookup"><span data-stu-id="c5f3d-108">[in] The memory address of the mapped assembly manifest.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="c5f3d-109">dans Taille, en octets, de l’image à `pbBase` .</span><span class="sxs-lookup"><span data-stu-id="c5f3d-109">[in] The size, in bytes, of the image at `pbBase`.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="c5f3d-110">dans Mémoire tampon destinée à contenir la représentation binaire de l’image.</span><span class="sxs-lookup"><span data-stu-id="c5f3d-110">[in] A buffer to contain the binary representation of the image.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="c5f3d-111">[in, out] Taille maximale demandée, en octets, de `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="c5f3d-111">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="c5f3d-112">Lors du retour, taille réelle, en octets, de `pbBlob` .</span><span class="sxs-lookup"><span data-stu-id="c5f3d-112">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5f3d-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c5f3d-113">Return Value</span></span>  

 <span data-ttu-id="c5f3d-114">`true` en cas de réussite de l’opération ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="c5f3d-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5f3d-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="c5f3d-115">Remarks</span></span>  

 <span data-ttu-id="c5f3d-116">Si la `StrongNameGetBlobFromImage` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="c5f3d-116">If the `StrongNameGetBlobFromImage` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5f3d-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c5f3d-117">Requirements</span></span>  

 <span data-ttu-id="c5f3d-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5f3d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5f3d-119">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="c5f3d-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c5f3d-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5f3d-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c5f3d-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5f3d-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5f3d-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5f3d-122">See also</span></span>

- [<span data-ttu-id="c5f3d-123">StrongNameGetBlobFromImage, méthode</span><span class="sxs-lookup"><span data-stu-id="c5f3d-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="c5f3d-124">StrongNameGetBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="c5f3d-124">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="c5f3d-125">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="c5f3d-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
