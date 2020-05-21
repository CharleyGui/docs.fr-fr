---
title: Méthode ICLRStrongName::GetHashFromFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromFileW method [.NET Framework hosting]
ms.assetid: c6ff45fc-905d-4c6e-b00c-97c6c7c55d99
topic_type:
- apiref
ms.openlocfilehash: 6dbb3360132186c38c007fb5fa12a3724ca145aa
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762095"
---
# <a name="iclrstrongnamegethashfromfilew-method"></a><span data-ttu-id="f85b3-102">Méthode ICLRStrongName::GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="f85b3-102">ICLRStrongName::GetHashFromFileW Method</span></span>
<span data-ttu-id="f85b3-103">Génère un hachage sur le contenu du fichier spécifié par une chaîne Unicode.</span><span class="sxs-lookup"><span data-stu-id="f85b3-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f85b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f85b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="f85b3-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f85b3-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f85b3-106">dans Nom Unicode du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="f85b3-106">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f85b3-107">[in, out] Algorithme à utiliser lors de la génération du hachage.</span><span class="sxs-lookup"><span data-stu-id="f85b3-107">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="f85b3-108">Les algorithmes valides sont ceux définis par l’CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="f85b3-108">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="f85b3-109">Si `piHashAlg` a la valeur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f85b3-109">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f85b3-110">à Tableau d’octets contenant le hachage généré.</span><span class="sxs-lookup"><span data-stu-id="f85b3-110">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f85b3-111">dans Taille maximale de la mémoire tampon vers laquelle pointe `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="f85b3-111">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f85b3-112">à Taille, en octets, de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="f85b3-112">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f85b3-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="f85b3-113">Return Value</span></span>  
 <span data-ttu-id="f85b3-114">`S_OK`Si la méthode s’est terminée avec succès ; Sinon, valeur HRESULT qui indique un échec (consultez les [valeurs HRESULT communes](/windows/win32/seccrypto/common-hresult-values) pour une liste).</span><span class="sxs-lookup"><span data-stu-id="f85b3-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f85b3-115">Notes</span><span class="sxs-lookup"><span data-stu-id="f85b3-115">Remarks</span></span>  
 <span data-ttu-id="f85b3-116">Cette méthode est la même que la méthode [ICLRStrongName :: GetHashFromFile (](iclrstrongname-gethashfromfile-method.md) , à ceci près que la spécification de nom de fichier est au format Unicode au lieu de ANSI.</span><span class="sxs-lookup"><span data-stu-id="f85b3-116">This method is the same as the [ICLRStrongName::GetHashFromFile](iclrstrongname-gethashfromfile-method.md) method, except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f85b3-117">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="f85b3-117">Requirements</span></span>  
 <span data-ttu-id="f85b3-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f85b3-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f85b3-119">**En-tête :** Metahost. h</span><span class="sxs-lookup"><span data-stu-id="f85b3-119">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f85b3-120">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f85b3-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f85b3-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f85b3-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f85b3-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f85b3-122">See also</span></span>

- [<span data-ttu-id="f85b3-123">GetHashFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="f85b3-123">GetHashFromFile Method</span></span>](iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="f85b3-124">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="f85b3-124">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
