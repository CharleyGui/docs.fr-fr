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
ms.openlocfilehash: d3693a42db8e32a4bb7a399f8c930da011130893
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778729"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="1a1f4-102">StrongNameCompareAssemblies, fonction</span><span class="sxs-lookup"><span data-stu-id="1a1f4-102">StrongNameCompareAssemblies Function</span></span>
<span data-ttu-id="1a1f4-103">Détermine si deux assemblys diffèrent uniquement par leurs signatures avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="1a1f4-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="1a1f4-104">Cette fonction a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="1a1f4-104">This function has been deprecated.</span></span> <span data-ttu-id="1a1f4-105">Utilisez le [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="1a1f4-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a1f4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a1f4-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a1f4-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="1a1f4-107">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="1a1f4-108">[in] Le chemin d’accès à l’assembly en premier.</span><span class="sxs-lookup"><span data-stu-id="1a1f4-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="1a1f4-109">[in] Le chemin d’accès au deuxième assembly.</span><span class="sxs-lookup"><span data-stu-id="1a1f4-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="1a1f4-110">[out] Une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="1a1f4-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="1a1f4-111">`SN_CMP_DIFFERENT` (0) : Spécifie que les assemblys contiennent des données différentes.</span><span class="sxs-lookup"><span data-stu-id="1a1f4-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="1a1f4-112">`SN_CMP_IDENTICAL` (1) - Spécifie que les assemblys sont exactement identiques, y compris leurs signatures et la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="1a1f4-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="1a1f4-113">`SN_CMP_SIGONLY` (2) : Spécifie que les assemblys diffèrent uniquement par la signature et la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="1a1f4-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a1f4-114">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="1a1f4-114">Return Value</span></span>  
 <span data-ttu-id="1a1f4-115">`true` de réussite ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="1a1f4-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a1f4-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="1a1f4-116">Requirements</span></span>  
 <span data-ttu-id="1a1f4-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a1f4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a1f4-118">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="1a1f4-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="1a1f4-119">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1a1f4-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1a1f4-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a1f4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a1f4-121">Notes</span><span class="sxs-lookup"><span data-stu-id="1a1f4-121">Remarks</span></span>  
 <span data-ttu-id="1a1f4-122">La signature de nom fort d’un assembly se compose du nom de texte, version, culture et jeton de clé publique de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1a1f4-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="1a1f4-123">Si le `StrongNameCompareAssemblies` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="1a1f4-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a1f4-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1a1f4-124">See also</span></span>

- [<span data-ttu-id="1a1f4-125">StrongNameCompareAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="1a1f4-125">StrongNameCompareAssemblies Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="1a1f4-126">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="1a1f4-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
