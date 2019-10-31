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
ms.openlocfilehash: e99346ecca651346b46c220a5e427cbc7f4c4697
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095013"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="65d09-102">StrongNameGetBlob, fonction</span><span class="sxs-lookup"><span data-stu-id="65d09-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="65d09-103">Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée.</span><span class="sxs-lookup"><span data-stu-id="65d09-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="65d09-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="65d09-104">This function has been deprecated.</span></span> <span data-ttu-id="65d09-105">Utilisez la méthode [ICLRStrongName :: StrongNameGetBlob (](../hosting/iclrstrongname-strongnamegetblob-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="65d09-105">Use the [ICLRStrongName::StrongNameGetBLob](../hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65d09-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65d09-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65d09-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="65d09-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="65d09-108">dans Chemin d’accès valide au fichier exécutable à charger.</span><span class="sxs-lookup"><span data-stu-id="65d09-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="65d09-109">dans Mémoire tampon dans laquelle charger le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="65d09-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="65d09-110">[in, out] Taille maximale demandée, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="65d09-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="65d09-111">Lors du retour, taille réelle, en octets, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="65d09-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65d09-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="65d09-112">Return Value</span></span>  
 <span data-ttu-id="65d09-113">`true` en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="65d09-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65d09-114">Notes</span><span class="sxs-lookup"><span data-stu-id="65d09-114">Remarks</span></span>  
 <span data-ttu-id="65d09-115">Si la fonction `StrongNameGetBlob` ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="65d09-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65d09-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="65d09-116">Requirements</span></span>  
 <span data-ttu-id="65d09-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65d09-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65d09-118">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="65d09-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="65d09-119">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="65d09-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65d09-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65d09-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65d09-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65d09-121">See also</span></span>

- [<span data-ttu-id="65d09-122">StrongNameGetBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="65d09-122">StrongNameGetBlob Method</span></span>](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="65d09-123">StrongNameGetBlobFromImage, méthode</span><span class="sxs-lookup"><span data-stu-id="65d09-123">StrongNameGetBlobFromImage Method</span></span>](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="65d09-124">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="65d09-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
