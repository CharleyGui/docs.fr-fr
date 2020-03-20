---
title: StrongNameSignatureGeneration, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176901"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="83de6-102">StrongNameSignatureGeneration, fonction</span><span class="sxs-lookup"><span data-stu-id="83de6-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="83de6-103">Génère une signature de nom fort pour l’assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="83de6-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="83de6-104">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="83de6-104">This function has been deprecated.</span></span> <span data-ttu-id="83de6-105">Utilisez la méthode [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="83de6-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83de6-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83de6-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83de6-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="83de6-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="83de6-108">[dans] Le chemin vers le fichier qui contient le manifeste de l’assemblage pour lequel la signature du nom fort sera générée.</span><span class="sxs-lookup"><span data-stu-id="83de6-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="83de6-109">[dans] Le nom du conteneur clé qui contient la paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="83de6-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="83de6-110">S’il `pbKeyBlob` `wszKeyContainer` est nul, doit spécifier un conteneur valide au sein du fournisseur de services cryptographiques (CSP).</span><span class="sxs-lookup"><span data-stu-id="83de6-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="83de6-111">Dans ce cas, la paire de clés stockée dans le conteneur est utilisée pour signer le fichier.</span><span class="sxs-lookup"><span data-stu-id="83de6-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="83de6-112">Si `pbKeyBlob` elle n’est pas nulle, la paire de clés est supposée être contenue dans le grand objet binaire clé (BLOB).</span><span class="sxs-lookup"><span data-stu-id="83de6-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="83de6-113">Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature.</span><span class="sxs-lookup"><span data-stu-id="83de6-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="83de6-114">Aucun autre type de clés n’est pris en charge pour le moment.</span><span class="sxs-lookup"><span data-stu-id="83de6-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="83de6-115">[dans] Un pointeur à la paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="83de6-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="83de6-116">Cette paire est dans le format `CryptExportKey` créé par la fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="83de6-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="83de6-117">S’il `pbKeyBlob` est nul, `wszKeyContainer` le conteneur clé spécifié par est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="83de6-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="83de6-118">[dans] La taille, dans les `pbKeyBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="83de6-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="83de6-119">[out] Un pointeur à l’endroit où le temps d’exécution de langue commune renvoie la signature.</span><span class="sxs-lookup"><span data-stu-id="83de6-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="83de6-120">Si `ppbSignatureBlob` elle est nulle, le temps d’exécution stocke la signature dans le fichier spécifié par `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="83de6-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="83de6-121">Si `ppbSignatureBlob` elle n’est pas nulle, le runtime de langue commune alloue l’espace pour retourner la signature.</span><span class="sxs-lookup"><span data-stu-id="83de6-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="83de6-122">L’appelant doit libérer cet espace en utilisant la fonction [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="83de6-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="83de6-123">[out] La taille, dans les octets, de la signature retournée.</span><span class="sxs-lookup"><span data-stu-id="83de6-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="83de6-124">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="83de6-124">Return Value</span></span>  
 <span data-ttu-id="83de6-125">`true`à la réussite; autrement, `false`.</span><span class="sxs-lookup"><span data-stu-id="83de6-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83de6-126">Notes </span><span class="sxs-lookup"><span data-stu-id="83de6-126">Remarks</span></span>  
 <span data-ttu-id="83de6-127">Spécifier null pour `wszFilePath` calculer la taille de la signature sans créer la signature.</span><span class="sxs-lookup"><span data-stu-id="83de6-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="83de6-128">La signature peut être stockée directement dans le fichier, soit retournée à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="83de6-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="83de6-129">Si `StrongNameSignatureGeneration` la fonction ne se termine pas avec succès, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="83de6-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83de6-130">Spécifications</span><span class="sxs-lookup"><span data-stu-id="83de6-130">Requirements</span></span>  
 <span data-ttu-id="83de6-131">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83de6-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83de6-132">**En-tête:** StrongName.h (en)</span><span class="sxs-lookup"><span data-stu-id="83de6-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="83de6-133">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="83de6-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83de6-134">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83de6-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83de6-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83de6-135">See also</span></span>

- [<span data-ttu-id="83de6-136">StrongNameSignatureGeneration, méthode</span><span class="sxs-lookup"><span data-stu-id="83de6-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="83de6-137">StrongNameSignatureGenerationEx, méthode</span><span class="sxs-lookup"><span data-stu-id="83de6-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="83de6-138">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="83de6-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
