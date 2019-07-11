---
title: GetHashFromAssemblyFileW, fonction
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d034f15db8f3d452a055c127bb7095667c089ffe
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772050"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="6c10e-102">GetHashFromAssemblyFileW, fonction</span><span class="sxs-lookup"><span data-stu-id="6c10e-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="6c10e-103">Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="6c10e-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="6c10e-104">Le chemin d’accès au fichier d’assembly doit être spécifié sous forme de chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="6c10e-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="6c10e-105">Cette fonction a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="6c10e-105">This function has been deprecated.</span></span> <span data-ttu-id="6c10e-106">Utilisez le [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="6c10e-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c10e-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c10e-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c10e-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6c10e-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="6c10e-109">[in] Le chemin d’accès au fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="6c10e-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="6c10e-110">Ce paramètre doit être une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="6c10e-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="6c10e-111">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="6c10e-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="6c10e-112">Utilisez zéro pour l’algorithme de hachage par défaut.</span><span class="sxs-lookup"><span data-stu-id="6c10e-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="6c10e-113">[out] La mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="6c10e-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="6c10e-114">[in] La taille maximale demandée de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6c10e-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="6c10e-115">[out] L’a retourné la taille, en octets, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="6c10e-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c10e-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6c10e-116">Requirements</span></span>  
 <span data-ttu-id="6c10e-117">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c10e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c10e-118">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="6c10e-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="6c10e-119">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c10e-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6c10e-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c10e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c10e-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c10e-121">See also</span></span>

- [<span data-ttu-id="6c10e-122">GetHashFromAssemblyFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="6c10e-122">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="6c10e-123">GetHashFromAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="6c10e-123">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="6c10e-124">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="6c10e-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
