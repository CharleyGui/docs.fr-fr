---
title: GetHashFromBlob, fonction
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
ms.openlocfilehash: d1027aea1d800bda1654b223fec992aa70efd4b7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140713"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="4cc8c-102">GetHashFromBlob, fonction</span><span class="sxs-lookup"><span data-stu-id="4cc8c-102">GetHashFromBlob Function</span></span>

<span data-ttu-id="4cc8c-103">Obtient un hachage de l’assembly à l’adresse mémoire spécifiée, à l’aide de l’algorithme de hachage spécifié.</span><span class="sxs-lookup"><span data-stu-id="4cc8c-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>

<span data-ttu-id="4cc8c-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="4cc8c-104">This function has been deprecated.</span></span> <span data-ttu-id="4cc8c-105">Utilisez la méthode [ICLRStrongName :: GetHashFromBlob (](../hosting/iclrstrongname-gethashfromblob-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="4cc8c-105">Use the [ICLRStrongName::GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="4cc8c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cc8c-106">Syntax</span></span>

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a><span data-ttu-id="4cc8c-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4cc8c-107">Parameters</span></span>

`pbBlob`\
<span data-ttu-id="4cc8c-108">dans Pointeur vers l’adresse du bloc de mémoire à hacher.</span><span class="sxs-lookup"><span data-stu-id="4cc8c-108">[in] A pointer to the address of the memory block to be hashed.</span></span>

`cchBlob`\
<span data-ttu-id="4cc8c-109">dans Longueur, en octets, du bloc de mémoire.</span><span class="sxs-lookup"><span data-stu-id="4cc8c-109">[in] The length, in bytes, of the memory block.</span></span>

`piHashAlg`\
<span data-ttu-id="4cc8c-110">[in, out] Constante qui spécifie l’algorithme de hachage.</span><span class="sxs-lookup"><span data-stu-id="4cc8c-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="4cc8c-111">Utilisez zéro pour l’algorithme par défaut.</span><span class="sxs-lookup"><span data-stu-id="4cc8c-111">Use zero for the default algorithm.</span></span>

`pbHash`\
<span data-ttu-id="4cc8c-112">à Mémoire tampon de hachage retournée.</span><span class="sxs-lookup"><span data-stu-id="4cc8c-112">[out] The returned hash buffer.</span></span>

`cchHash`\
<span data-ttu-id="4cc8c-113">dans Taille maximale de `pbHash`demandée.</span><span class="sxs-lookup"><span data-stu-id="4cc8c-113">[in] The requested maximum size of `pbHash`.</span></span>

`pchHash`\
<span data-ttu-id="4cc8c-114">à Taille, en octets, de la `pbHash`retournée.</span><span class="sxs-lookup"><span data-stu-id="4cc8c-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>

## <a name="requirements"></a><span data-ttu-id="4cc8c-115">spécifications</span><span class="sxs-lookup"><span data-stu-id="4cc8c-115">Requirements</span></span>

<span data-ttu-id="4cc8c-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4cc8c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="4cc8c-117">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="4cc8c-117">**Header:** StrongName.h</span></span>

<span data-ttu-id="4cc8c-118">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4cc8c-118">**Library:** Included as a resource in MsCorEE.dll</span></span>

<span data-ttu-id="4cc8c-119">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4cc8c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="4cc8c-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cc8c-120">See also</span></span>

- [<span data-ttu-id="4cc8c-121">GetHashFromBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="4cc8c-121">GetHashFromBlob Method</span></span>](../hosting/iclrstrongname-gethashfromblob-method.md)
- [<span data-ttu-id="4cc8c-122">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="4cc8c-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
