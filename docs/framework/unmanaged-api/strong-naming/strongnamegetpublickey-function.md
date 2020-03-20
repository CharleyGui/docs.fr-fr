---
title: StrongNameGetPublicKey, fonction
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176927"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="a9df8-102">StrongNameGetPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="a9df8-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="a9df8-103">Obtient la clé publique à partir d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="a9df8-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="a9df8-104">La paire de clés peut être fournie soit comme un nom de conteneur clé au sein d’un fournisseur de services cryptographiques (CSP) ou comme une collection brute d’octets.</span><span class="sxs-lookup"><span data-stu-id="a9df8-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="a9df8-105">Cette fonction a été dépréciée.</span><span class="sxs-lookup"><span data-stu-id="a9df8-105">This function has been deprecated.</span></span> <span data-ttu-id="a9df8-106">Utilisez la méthode [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="a9df8-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9df8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a9df8-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9df8-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a9df8-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="a9df8-109">[dans] Le nom du conteneur clé qui contient la paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="a9df8-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="a9df8-110">S’il `pbKeyBlob` `szKeyContainer` est nul, doit spécifier un conteneur valide dans le CSP.</span><span class="sxs-lookup"><span data-stu-id="a9df8-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="a9df8-111">Dans ce `StrongNameGetPublicKey` cas, extrait la clé publique de la paire de clés stockée dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="a9df8-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="a9df8-112">Si `pbKeyBlob` elle n’est pas nulle, la paire de clés est supposée être contenue dans le grand objet binaire clé (BLOB).</span><span class="sxs-lookup"><span data-stu-id="a9df8-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="a9df8-113">Les clés doivent être 1024 bits Rivest-Shamir-Adleman (RSA) clés de signature.</span><span class="sxs-lookup"><span data-stu-id="a9df8-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="a9df8-114">Aucun autre type de clés n’est pris en charge pour le moment.</span><span class="sxs-lookup"><span data-stu-id="a9df8-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="a9df8-115">[dans] Un pointeur à la paire de clés public/privé.</span><span class="sxs-lookup"><span data-stu-id="a9df8-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="a9df8-116">Cette paire est dans le format `CryptExportKey` créé par la fonction Win32.</span><span class="sxs-lookup"><span data-stu-id="a9df8-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="a9df8-117">S’il `pbKeyBlob` est nul, `szKeyContainer` le conteneur clé spécifié par est supposé contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="a9df8-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="a9df8-118">[dans] La taille, dans les `pbKeyBlob`octets, de .</span><span class="sxs-lookup"><span data-stu-id="a9df8-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="a9df8-119">[out] Le BLOB clé publique retourné.</span><span class="sxs-lookup"><span data-stu-id="a9df8-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="a9df8-120">Le `ppbPublicKeyBlob` paramètre est attribué par l’heure de l’exécution de la langue commune et retourné à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="a9df8-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="a9df8-121">L’appelant doit libérer la mémoire en utilisant la fonction [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="a9df8-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="a9df8-122">[out] La taille de la clé publique retournée BLOB.</span><span class="sxs-lookup"><span data-stu-id="a9df8-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9df8-123">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a9df8-123">Return Value</span></span>  
 <span data-ttu-id="a9df8-124">`true`à la réussite; autrement, `false`.</span><span class="sxs-lookup"><span data-stu-id="a9df8-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9df8-125">Notes </span><span class="sxs-lookup"><span data-stu-id="a9df8-125">Remarks</span></span>  
 <span data-ttu-id="a9df8-126">La clé publique est contenue dans une structure [PublicKeyBlob.](publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="a9df8-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="a9df8-127">Si `StrongNameGetPublicKey` la fonction ne se termine pas avec succès, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="a9df8-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9df8-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a9df8-128">Requirements</span></span>  
 <span data-ttu-id="a9df8-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9df8-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9df8-130">**En-tête:** StrongName.h (en)</span><span class="sxs-lookup"><span data-stu-id="a9df8-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="a9df8-131">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a9df8-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a9df8-132">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9df8-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9df8-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9df8-133">See also</span></span>

- [<span data-ttu-id="a9df8-134">StrongNameGetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="a9df8-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="a9df8-135">StrongNameTokenFromPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="a9df8-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="a9df8-136">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="a9df8-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="a9df8-137">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="a9df8-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
