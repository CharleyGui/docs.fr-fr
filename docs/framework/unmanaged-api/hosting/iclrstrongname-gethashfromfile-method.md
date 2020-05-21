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
ms.openlocfilehash: e4a5f6440a016176cf06704b342c173b29748e78
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762108"
---
# <a name="iclrstrongnamegethashfromfile-method"></a><span data-ttu-id="b1e03-102">Méthode ICLRStrongName::GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="b1e03-102">ICLRStrongName::GetHashFromFile Method</span></span>
<span data-ttu-id="b1e03-103">Génère un hachage sur le contenu du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="b1e03-103">Generates a hash over the contents of the specified file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e03-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1e03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1e03-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b1e03-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="b1e03-106">dans Nom du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="b1e03-106">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="b1e03-107">[in, out] Algorithme à utiliser lors de la génération du hachage.</span><span class="sxs-lookup"><span data-stu-id="b1e03-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="b1e03-108">Les algorithmes valides sont ceux définis par l’CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="b1e03-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="b1e03-109">Si `piHashAlg` a la valeur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b1e03-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="b1e03-110">à Tableau d’octets contenant le hachage généré.</span><span class="sxs-lookup"><span data-stu-id="b1e03-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="b1e03-111">dans Taille maximale de la mémoire tampon `pbHash` vers laquelle pointe.</span><span class="sxs-lookup"><span data-stu-id="b1e03-111">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="b1e03-112">à Taille, en octets, du retourné `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="b1e03-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1e03-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b1e03-113">Return Value</span></span>  
 <span data-ttu-id="b1e03-114">`S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="b1e03-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1e03-115">Notes</span><span class="sxs-lookup"><span data-stu-id="b1e03-115">Remarks</span></span>  
 <span data-ttu-id="b1e03-116">Cette méthode est la même que la méthode [ICLRStrongName :: GetHashFromFileW (](iclrstrongname-gethashfromfilew-method.md) , à ceci près que la spécification de nom de fichier est ANSI au lieu de Unicode.</span><span class="sxs-lookup"><span data-stu-id="b1e03-116">This method is the same as the [ICLRStrongName::GetHashFromFileW](iclrstrongname-gethashfromfilew-method.md) method, except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1e03-117">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="b1e03-117">Requirements</span></span>  
 <span data-ttu-id="b1e03-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1e03-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1e03-119">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="b1e03-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b1e03-120">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1e03-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1e03-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1e03-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1e03-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b1e03-122">See also</span></span>

- [<span data-ttu-id="b1e03-123">GetHashFromFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="b1e03-123">GetHashFromFileW Method</span></span>](iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="b1e03-124">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="b1e03-124">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
