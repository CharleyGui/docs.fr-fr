---
title: GetHashFromFile, fonction
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
ms.openlocfilehash: ea2b70f37668587fb02513ab54da6c1915e2918d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176979"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="b870c-102">GetHashFromFile, fonction</span><span class="sxs-lookup"><span data-stu-id="b870c-102">GetHashFromFile Function</span></span>
<span data-ttu-id="b870c-103">Génère un hachage sur le contenu du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="b870c-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="b870c-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="b870c-104">This function has been deprecated.</span></span> <span data-ttu-id="b870c-105">Utilisez la méthode [ICLRStrongName::GetHashDeFile](../hosting/iclrstrongname-gethashfromfile-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="b870c-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b870c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b870c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b870c-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b870c-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="b870c-108">[dans] Le nom du fichier au hachage.</span><span class="sxs-lookup"><span data-stu-id="b870c-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b870c-109">[dans, dehors] L’algorithme à utiliser lors de la génération du hachage.</span><span class="sxs-lookup"><span data-stu-id="b870c-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="b870c-110">Les algorithmes valides sont ceux définis par le CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="b870c-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="b870c-111">Si `piHashAlg` l’algorithme par défaut CALG_SHA-1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b870c-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b870c-112">[out] Un tableau d’en-lieu contenant le hachage généré.</span><span class="sxs-lookup"><span data-stu-id="b870c-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b870c-113">[dans] La taille maximale du `pbHash` tampon qui indique.</span><span class="sxs-lookup"><span data-stu-id="b870c-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b870c-114">[out] La taille, dans les octets, du retour `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="b870c-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b870c-115">Notes </span><span class="sxs-lookup"><span data-stu-id="b870c-115">Remarks</span></span>  
 <span data-ttu-id="b870c-116">Cette fonction est la même que [GetHashFromFileW](gethashfromfilew-function.md), sauf que la spécification nom de fichier est ANSI au lieu d’Unicode.</span><span class="sxs-lookup"><span data-stu-id="b870c-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b870c-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="b870c-117">Requirements</span></span>  
 <span data-ttu-id="b870c-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b870c-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b870c-119">**En-tête:** StrongName.h (en)</span><span class="sxs-lookup"><span data-stu-id="b870c-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b870c-120">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b870c-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b870c-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b870c-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b870c-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b870c-122">See also</span></span>

- [<span data-ttu-id="b870c-123">GetHashFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="b870c-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="b870c-124">GetHashFromFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="b870c-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="b870c-125">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="b870c-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
