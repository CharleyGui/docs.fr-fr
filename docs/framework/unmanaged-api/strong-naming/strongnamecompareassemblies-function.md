---
title: StrongNameCompareAssemblies, fonction
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0c2e8e46c7bb3a5e693c9ea16e6c5a0722b1898
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799150"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="2ebf1-102">StrongNameCompareAssemblies, fonction</span><span class="sxs-lookup"><span data-stu-id="2ebf1-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="2ebf1-103">Détermine si deux assemblys diffèrent uniquement par leurs signatures avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="2ebf1-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="2ebf1-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="2ebf1-104">This function has been deprecated.</span></span> <span data-ttu-id="2ebf1-105">Utilisez la méthode [ICLRStrongName :: StrongNameCompareAssemblies (](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="2ebf1-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ebf1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ebf1-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ebf1-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2ebf1-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="2ebf1-108">dans Chemin d’accès au premier assembly.</span><span class="sxs-lookup"><span data-stu-id="2ebf1-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="2ebf1-109">dans Chemin d’accès au deuxième assembly.</span><span class="sxs-lookup"><span data-stu-id="2ebf1-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="2ebf1-110">à L’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="2ebf1-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="2ebf1-111">`SN_CMP_DIFFERENT`(0) : spécifie que les assemblys contiennent des données différentes.</span><span class="sxs-lookup"><span data-stu-id="2ebf1-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="2ebf1-112">`SN_CMP_IDENTICAL`(1) : spécifie que les assemblys sont exactement les mêmes, y compris leurs signatures et leur somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="2ebf1-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="2ebf1-113">`SN_CMP_SIGONLY`(2) : spécifie que les assemblys diffèrent uniquement par la signature et la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="2ebf1-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ebf1-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2ebf1-114">Return Value</span></span>  
 <span data-ttu-id="2ebf1-115">`true`en cas de réussite de l’opération ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="2ebf1-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ebf1-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="2ebf1-116">Requirements</span></span>  
 <span data-ttu-id="2ebf1-117">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ebf1-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ebf1-118">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2ebf1-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2ebf1-119">**Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2ebf1-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ebf1-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ebf1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ebf1-121">Notes</span><span class="sxs-lookup"><span data-stu-id="2ebf1-121">Remarks</span></span>  
 <span data-ttu-id="2ebf1-122">La signature de nom fort d’un assembly se compose du nom de texte, de la version, de la culture et du jeton de clé publique de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="2ebf1-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="2ebf1-123">Si la `StrongNameCompareAssemblies` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="2ebf1-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ebf1-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2ebf1-124">See also</span></span>

- [<span data-ttu-id="2ebf1-125">StrongNameCompareAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="2ebf1-125">StrongNameCompareAssemblies Method</span></span>](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="2ebf1-126">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="2ebf1-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
