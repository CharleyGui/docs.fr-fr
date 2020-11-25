---
title: Méthode ICLRStrongName::GetHashFromFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: ff346d8f7ba321904a8d91079298b58039e6eb54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727599"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="cdbcd-102">Méthode ICLRStrongName::GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="cdbcd-102">ICLRStrongName::GetHashFromFile Method</span></span>

<span data-ttu-id="cdbcd-103">Génère un hachage sur le contenu du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdbcd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdbcd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdbcd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cdbcd-105">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="cdbcd-106">dans Nom du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="cdbcd-107">[in, out] Algorithme à utiliser lors de la génération du hachage.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="cdbcd-108">Les algorithmes valides sont ceux définis par l’CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="cdbcd-109">Si `piHashAlg` a la valeur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="cdbcd-110">à Tableau d’octets contenant le hachage généré.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="cdbcd-111">dans Taille maximale de la mémoire tampon `pbHash` vers laquelle pointe.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="cdbcd-112">à Taille, en octets, du retourné `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="cdbcd-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdbcd-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="cdbcd-113">Return Value</span></span>  

 <span data-ttu-id="cdbcd-114">`S_OK` Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="cdbcd-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdbcd-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="cdbcd-115">Remarks</span></span>  

 <span data-ttu-id="cdbcd-116">Cette méthode est la même que la méthode [ICLRStrongName :: GetHashFromFileW (](iclrstrongname-gethashfromfilew-method.md) , à ceci près que la spécification de nom de fichier est ANSI au lieu de Unicode.</span><span class="sxs-lookup"><span data-stu-id="cdbcd-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdbcd-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cdbcd-117">Requirements</span></span>  

 <span data-ttu-id="cdbcd-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdbcd-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdbcd-119">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="cdbcd-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="cdbcd-120">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="cdbcd-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cdbcd-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdbcd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdbcd-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdbcd-122">See also</span></span>

- [<span data-ttu-id="cdbcd-123">GetHashFromFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="cdbcd-123">GetHashFromFileW Method</span></span>](iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="cdbcd-124">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="cdbcd-124">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
