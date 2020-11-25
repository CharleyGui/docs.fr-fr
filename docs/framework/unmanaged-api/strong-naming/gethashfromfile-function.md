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
ms.openlocfilehash: ee9f9cd9a9f35c6c54497ad382bb6f9817d186bd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732370"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="ad272-102">GetHashFromFile, fonction</span><span class="sxs-lookup"><span data-stu-id="ad272-102">GetHashFromFile Function</span></span>

<span data-ttu-id="ad272-103">Génère un hachage sur le contenu du fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="ad272-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="ad272-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="ad272-104">This function has been deprecated.</span></span> <span data-ttu-id="ad272-105">Utilisez la méthode [ICLRStrongName :: GetHashFromFile (](../hosting/iclrstrongname-gethashfromfile-method.md) à la place.</span><span class="sxs-lookup"><span data-stu-id="ad272-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad272-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad272-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad272-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ad272-107">Parameters</span></span>  

 `szFilePath`  
 <span data-ttu-id="ad272-108">dans Nom du fichier à hacher.</span><span class="sxs-lookup"><span data-stu-id="ad272-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ad272-109">[in, out] Algorithme à utiliser lors de la génération du hachage.</span><span class="sxs-lookup"><span data-stu-id="ad272-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="ad272-110">Les algorithmes valides sont ceux définis par l’CryptoAPI Win32.</span><span class="sxs-lookup"><span data-stu-id="ad272-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="ad272-111">Si `piHashAlg` a la valeur 0, l’algorithme par défaut CALG_SHA-1 est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ad272-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ad272-112">à Tableau d’octets contenant le hachage généré.</span><span class="sxs-lookup"><span data-stu-id="ad272-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ad272-113">dans Taille maximale de la mémoire tampon `pbHash` vers laquelle pointe.</span><span class="sxs-lookup"><span data-stu-id="ad272-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ad272-114">à Taille, en octets, du retourné `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="ad272-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad272-115">Remarques</span><span class="sxs-lookup"><span data-stu-id="ad272-115">Remarks</span></span>  

 <span data-ttu-id="ad272-116">Cette fonction est identique à [GetHashFromFileW (](gethashfromfilew-function.md), à ceci près que la spécification de nom de fichier est ANSI au lieu de Unicode.</span><span class="sxs-lookup"><span data-stu-id="ad272-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad272-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ad272-117">Requirements</span></span>  

 <span data-ttu-id="ad272-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad272-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad272-119">**En-tête :** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="ad272-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ad272-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad272-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ad272-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad272-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad272-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad272-122">See also</span></span>

- [<span data-ttu-id="ad272-123">GetHashFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="ad272-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="ad272-124">GetHashFromFileW, méthode</span><span class="sxs-lookup"><span data-stu-id="ad272-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="ad272-125">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="ad272-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
