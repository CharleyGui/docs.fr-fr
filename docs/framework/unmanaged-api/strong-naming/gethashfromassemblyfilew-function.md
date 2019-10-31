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
ms.openlocfilehash: cf7667f0f2a0f77cd793e00a5de8b030b0c53ec8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140702"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="2efa5-102">GetHashFromAssemblyFileW, fonction</span><span class="sxs-lookup"><span data-stu-id="2efa5-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="2efa5-103">Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="2efa5-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="2efa5-104">Le chemin d’accès au fichier d’assembly doit être spécifié sous la forme d’une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="2efa5-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="2efa5-105">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="2efa5-105">This function has been deprecated.</span></span> <span data-ttu-id="2efa5-106">Utilisez la méthode [ICLRStrongName :: GetHashFromAssemblyFileW (](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="2efa5-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2efa5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2efa5-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2efa5-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2efa5-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="2efa5-109">dans Chemin d’accès au fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="2efa5-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="2efa5-110">Ce paramètre doit être une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="2efa5-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="2efa5-111">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="2efa5-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="2efa5-112">Utilisez zéro pour l’algorithme de hachage par défaut.</span><span class="sxs-lookup"><span data-stu-id="2efa5-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="2efa5-113">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="2efa5-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="2efa5-114">dans Taille maximale de `pbHash`demandée.</span><span class="sxs-lookup"><span data-stu-id="2efa5-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="2efa5-115">à Taille retournée, en octets, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="2efa5-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2efa5-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="2efa5-116">Requirements</span></span>  
 <span data-ttu-id="2efa5-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2efa5-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2efa5-118">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="2efa5-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2efa5-119">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2efa5-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2efa5-120">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2efa5-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2efa5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2efa5-121">See also</span></span>

- [<span data-ttu-id="2efa5-122">GetHashFromAssemblyFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="2efa5-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="2efa5-123">GetHashFromAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="2efa5-123">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="2efa5-124">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="2efa5-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
