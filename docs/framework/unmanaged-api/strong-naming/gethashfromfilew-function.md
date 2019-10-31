---
title: GetHashFromFileW, fonction
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
ms.openlocfilehash: db6f39119d143d27c0d3a80a9c65565d4dfd0d39
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140673"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="0511a-102">GetHashFromFileW, fonction</span><span class="sxs-lookup"><span data-stu-id="0511a-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="0511a-103">Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="0511a-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="0511a-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="0511a-104">This function has been deprecated.</span></span> <span data-ttu-id="0511a-105">Utilisez la méthode [ICLRStrongName :: GetHashFromFileW (](../hosting/iclrstrongname-gethashfromfilew-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="0511a-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0511a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0511a-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="0511a-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0511a-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="0511a-108">dans Nom Unicode du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="0511a-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="0511a-109">[in, out] Algorithme à utiliser lors de la génération du hachage.</span><span class="sxs-lookup"><span data-stu-id="0511a-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="0511a-110">Les algorithmes valides sont ceux définis par l’CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="0511a-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="0511a-111">Si `piHashAlg` a la valeur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="0511a-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="0511a-112">à Tableau d’octets contenant le hachage généré.</span><span class="sxs-lookup"><span data-stu-id="0511a-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="0511a-113">dans Taille maximale de la mémoire tampon vers laquelle pointe `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="0511a-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="0511a-114">à Taille, en octets, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="0511a-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0511a-115">Notes</span><span class="sxs-lookup"><span data-stu-id="0511a-115">Remarks</span></span>  
 <span data-ttu-id="0511a-116">Cette fonction est identique à [GetHashFromFile (](gethashfromfile-function.md), à ceci près que la spécification de nom de fichier est au format Unicode au lieu de ANSI.</span><span class="sxs-lookup"><span data-stu-id="0511a-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0511a-117">spécifications</span><span class="sxs-lookup"><span data-stu-id="0511a-117">Requirements</span></span>  
 <span data-ttu-id="0511a-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0511a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0511a-119">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="0511a-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="0511a-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0511a-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0511a-121">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0511a-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0511a-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0511a-122">See also</span></span>

- [<span data-ttu-id="0511a-123">GetHashFromFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="0511a-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="0511a-124">GetHashFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="0511a-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="0511a-125">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="0511a-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
