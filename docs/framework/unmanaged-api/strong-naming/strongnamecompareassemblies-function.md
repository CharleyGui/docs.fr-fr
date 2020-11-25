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
ms.openlocfilehash: e7292635ea0344f1c77c8d44908a9a811e464ff9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732305"
---
# <a name="strongnamecompareassemblies-function"></a><span data-ttu-id="7c965-102">StrongNameCompareAssemblies, fonction</span><span class="sxs-lookup"><span data-stu-id="7c965-102">StrongNameCompareAssemblies Function</span></span>

<span data-ttu-id="7c965-103">Détermine si deux assemblys diffèrent uniquement par leurs signatures avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="7c965-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
 <span data-ttu-id="7c965-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="7c965-104">This function has been deprecated.</span></span> <span data-ttu-id="7c965-105">Utilisez la méthode [ICLRStrongName :: StrongNameCompareAssemblies (](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="7c965-105">Use the [ICLRStrongName::StrongNameCompareAssemblies](../hosting/iclrstrongname-strongnamecompareassemblies-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c965-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c965-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c965-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7c965-107">Parameters</span></span>  

 `wszAssembly1`  
 <span data-ttu-id="7c965-108">dans Chemin d’accès au premier assembly.</span><span class="sxs-lookup"><span data-stu-id="7c965-108">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="7c965-109">dans Chemin d’accès au deuxième assembly.</span><span class="sxs-lookup"><span data-stu-id="7c965-109">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="7c965-110">à L’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="7c965-110">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="7c965-111">`SN_CMP_DIFFERENT` (0) : spécifie que les assemblys contiennent des données différentes.</span><span class="sxs-lookup"><span data-stu-id="7c965-111">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="7c965-112">`SN_CMP_IDENTICAL` (1) : spécifie que les assemblys sont exactement les mêmes, y compris leurs signatures et leur somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="7c965-112">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="7c965-113">`SN_CMP_SIGONLY` (2) : spécifie que les assemblys diffèrent uniquement par la signature et la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="7c965-113">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c965-114">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="7c965-114">Return Value</span></span>  

 <span data-ttu-id="7c965-115">`true` en cas de réussite de l’opération ; Sinon, `false` .</span><span class="sxs-lookup"><span data-stu-id="7c965-115">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c965-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7c965-116">Requirements</span></span>  

 <span data-ttu-id="7c965-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c965-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c965-118">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="7c965-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="7c965-119">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c965-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c965-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c965-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c965-121">Remarques</span><span class="sxs-lookup"><span data-stu-id="7c965-121">Remarks</span></span>  

 <span data-ttu-id="7c965-122">La signature de nom fort d’un assembly se compose du nom de texte, de la version, de la culture et du jeton de clé publique de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="7c965-122">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
 <span data-ttu-id="7c965-123">Si la `StrongNameCompareAssemblies` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="7c965-123">If the `StrongNameCompareAssemblies` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c965-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c965-124">See also</span></span>

- [<span data-ttu-id="7c965-125">StrongNameCompareAssemblies, méthode</span><span class="sxs-lookup"><span data-stu-id="7c965-125">StrongNameCompareAssemblies Method</span></span>](../hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [<span data-ttu-id="7c965-126">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="7c965-126">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
