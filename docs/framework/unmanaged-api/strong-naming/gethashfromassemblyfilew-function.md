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
ms.openlocfilehash: b895c77850c0457fd2a152c1128c016093599f76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730979"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="0d813-102">GetHashFromAssemblyFileW, fonction</span><span class="sxs-lookup"><span data-stu-id="0d813-102">GetHashFromAssemblyFileW Function</span></span>

<span data-ttu-id="0d813-103">Obtient un hachage du fichier d’assembly spécifié, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="0d813-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="0d813-104">Le chemin d’accès au fichier d’assembly doit être spécifié sous la forme d’une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="0d813-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="0d813-105">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="0d813-105">This function has been deprecated.</span></span> <span data-ttu-id="0d813-106">Utilisez la méthode [ICLRStrongName :: GetHashFromAssemblyFileW (](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="0d813-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d813-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d813-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d813-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0d813-108">Parameters</span></span>  

 `wszFilePath`  
 <span data-ttu-id="0d813-109">dans Chemin d’accès au fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="0d813-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="0d813-110">Ce paramètre doit être une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="0d813-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="0d813-111">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="0d813-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="0d813-112">Utilisez zéro pour l’algorithme de hachage par défaut.</span><span class="sxs-lookup"><span data-stu-id="0d813-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="0d813-113">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="0d813-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="0d813-114">dans Taille maximale demandée de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="0d813-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="0d813-115">à Taille retournée, en octets, de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="0d813-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d813-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0d813-116">Requirements</span></span>  

 <span data-ttu-id="0d813-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d813-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d813-118">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="0d813-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0d813-119">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d813-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d813-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d813-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d813-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d813-121">See also</span></span>

- [<span data-ttu-id="0d813-122">GetHashFromAssemblyFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="0d813-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="0d813-123">GetHashFromAssemblyFile, méthode</span><span class="sxs-lookup"><span data-stu-id="0d813-123">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="0d813-124">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="0d813-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
