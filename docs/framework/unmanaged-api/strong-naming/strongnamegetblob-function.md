---
title: StrongNameGetBlob, fonction
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d5b3d1d39b5d4c5b7d4db073b3ffaf1c6b88373
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799100"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="e6752-102">StrongNameGetBlob, fonction</span><span class="sxs-lookup"><span data-stu-id="e6752-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="e6752-103">Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="e6752-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="e6752-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="e6752-104">This function has been deprecated.</span></span> <span data-ttu-id="e6752-105">Utilisez la méthode [ICLRStrongName :: StrongNameGetBlob (](../hosting/iclrstrongname-strongnamegetblob-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="e6752-105">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6752-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6752-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6752-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e6752-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="e6752-108">dans Chemin d’accès valide au fichier exécutable à charger.</span><span class="sxs-lookup"><span data-stu-id="e6752-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="e6752-109">dans Mémoire tampon dans laquelle charger le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="e6752-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="e6752-110">[in, out] Taille maximale demandée, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="e6752-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="e6752-111">Lors du retour, taille réelle, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="e6752-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6752-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e6752-112">Return Value</span></span>  
 <span data-ttu-id="e6752-113">`true`en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="e6752-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e6752-114">Notes</span><span class="sxs-lookup"><span data-stu-id="e6752-114">Remarks</span></span>  
 <span data-ttu-id="e6752-115">Si la `StrongNameGetBlob` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="e6752-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6752-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e6752-116">Requirements</span></span>  
 <span data-ttu-id="e6752-117">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6752-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6752-118">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e6752-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e6752-119">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e6752-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e6752-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6752-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6752-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6752-121">See also</span></span>

- [<span data-ttu-id="e6752-122">StrongNameGetBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="e6752-122">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="e6752-123">StrongNameGetBlobFromImage, méthode</span><span class="sxs-lookup"><span data-stu-id="e6752-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="e6752-124">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="e6752-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
