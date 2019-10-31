---
title: Méthode ICLRStrongName::StrongNameCompareAssemblies
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameCompareAssemblies
helpviewer_keywords:
- ICLRStrongName::StrongNameCompareAssemblies method [.NET Framework hosting]
- StrongNameCompareAssemblies method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: b1fb356c-72cf-4aa4-8376-f291a6d97c01
topic_type:
- apiref
ms.openlocfilehash: fdca03b781e07b709cbc54e673dbaa2a1130fbe3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135148"
---
# <a name="iclrstrongnamestrongnamecompareassemblies-method"></a><span data-ttu-id="940ac-102">Méthode ICLRStrongName::StrongNameCompareAssemblies</span><span class="sxs-lookup"><span data-stu-id="940ac-102">ICLRStrongName::StrongNameCompareAssemblies Method</span></span>
<span data-ttu-id="940ac-103">Détermine si deux assemblys diffèrent uniquement par leurs signatures avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="940ac-103">Determines whether two assemblies differ only by their strong name signatures.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="940ac-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="940ac-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="940ac-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="940ac-105">Parameters</span></span>  
 `wszAssembly1`  
 <span data-ttu-id="940ac-106">dans Chemin d’accès au premier assembly.</span><span class="sxs-lookup"><span data-stu-id="940ac-106">[in] The path to the first assembly.</span></span>  
  
 `wszAssembly2`  
 <span data-ttu-id="940ac-107">dans Chemin d’accès au deuxième assembly.</span><span class="sxs-lookup"><span data-stu-id="940ac-107">[in] The path to the second assembly.</span></span>  
  
 `pdwResult`  
 <span data-ttu-id="940ac-108">à L’une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="940ac-108">[out] One of the following values:</span></span>  
  
- <span data-ttu-id="940ac-109">`SN_CMP_DIFFERENT` (0) : spécifie que les assemblys contiennent des données différentes.</span><span class="sxs-lookup"><span data-stu-id="940ac-109">`SN_CMP_DIFFERENT` (0) - Specifies that the assemblies contain different data.</span></span>  
  
- <span data-ttu-id="940ac-110">`SN_CMP_IDENTICAL` (1) : spécifie que les assemblys sont exactement les mêmes, y compris leurs signatures et leur somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="940ac-110">`SN_CMP_IDENTICAL` (1) - Specifies that the assemblies are exactly the same, including their signatures and checksum.</span></span>  
  
- <span data-ttu-id="940ac-111">`SN_CMP_SIGONLY` (2) : spécifie que les assemblys diffèrent uniquement par la signature et la somme de contrôle.</span><span class="sxs-lookup"><span data-stu-id="940ac-111">`SN_CMP_SIGONLY` (2) - Specifies that the assemblies differ only by signature and checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="940ac-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="940ac-112">Return Value</span></span>  
 <span data-ttu-id="940ac-113">`S_OK` si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](https://go.microsoft.com/fwlink/?LinkId=213878) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="940ac-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="940ac-114">spécifications</span><span class="sxs-lookup"><span data-stu-id="940ac-114">Requirements</span></span>  
 <span data-ttu-id="940ac-115">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="940ac-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="940ac-116">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="940ac-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="940ac-117">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="940ac-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="940ac-118">**Versions du .NET Framework :** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="940ac-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="940ac-119">Notes</span><span class="sxs-lookup"><span data-stu-id="940ac-119">Remarks</span></span>  
 <span data-ttu-id="940ac-120">La signature de nom fort d’un assembly se compose du nom de texte, de la version, de la culture et du jeton de clé publique de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="940ac-120">The strong name signature of an assembly consists of the assembly's text name, version, culture, and public key token.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="940ac-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="940ac-121">See also</span></span>

- [<span data-ttu-id="940ac-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="940ac-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
