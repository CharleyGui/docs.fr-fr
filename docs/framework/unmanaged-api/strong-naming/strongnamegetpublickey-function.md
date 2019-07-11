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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6e9e5c199ad437290d7bf19d65b5f29a0abed5e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780110"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="c7fd6-102">StrongNameGetPublicKey, fonction</span><span class="sxs-lookup"><span data-stu-id="c7fd6-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="c7fd6-103">Obtient la clé publique à partir d’une paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="c7fd6-104">La paire de clés peut être fournie sous la forme d’un nom de conteneur de clé au sein d’un fournisseur de services de chiffrement (CSP) ou une collection brute d’octets.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="c7fd6-105">Cette fonction a été déconseillée.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-105">This function has been deprecated.</span></span> <span data-ttu-id="c7fd6-106">Utilisez le [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) méthode à la place.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7fd6-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7fd6-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7fd6-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c7fd6-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="c7fd6-109">[in] Le nom du conteneur de clé qui contient la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="c7fd6-110">Si `pbKeyBlob` a la valeur null, `szKeyContainer` doit spécifier un conteneur valid dans le CSP.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="c7fd6-111">Dans ce cas, `StrongNameGetPublicKey` extrait la clé publique de la paire de clés stockée dans le conteneur.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="c7fd6-112">Si `pbKeyBlob` n’est pas null, la paire de clés est supposée être contenue dans l’objet binaire volumineux (BLOB) de clé.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="c7fd6-113">Les clés doivent être Rivest-Shamir-Adleman (RSA 1024 bits) clés de signature.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="c7fd6-114">Aucun autre type de clés n’est pris en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="c7fd6-115">[in] Pointeur vers la paire de clés publique/privée.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="c7fd6-116">Cette paire est au format créé par Win32 `CryptExportKey` (fonction).</span><span class="sxs-lookup"><span data-stu-id="c7fd6-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="c7fd6-117">Si `pbKeyBlob` est null, le conteneur de clé spécifié par `szKeyContainer` est supposée pour contenir la paire de clés.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="c7fd6-118">[in] La taille, en octets, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="c7fd6-119">[out] La clé publique BLOB retournée.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="c7fd6-120">Le `ppbPublicKeyBlob` paramètre est allouée par le common language runtime et retourné à l’appelant.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="c7fd6-121">L’appelant doit libérer la mémoire à l’aide de la [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) (fonction).</span><span class="sxs-lookup"><span data-stu-id="c7fd6-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="c7fd6-122">[out] La taille de la clé publique retournée BLOB.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7fd6-123">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c7fd6-123">Return Value</span></span>  
 <span data-ttu-id="c7fd6-124">`true` de réussite ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7fd6-125">Notes</span><span class="sxs-lookup"><span data-stu-id="c7fd6-125">Remarks</span></span>  
 <span data-ttu-id="c7fd6-126">La clé publique est contenue dans un [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="c7fd6-127">Si le `StrongNameGetPublicKey` (fonction) ne pas aboutir, appelez le [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) fonction pour récupérer la dernière erreur générée.</span><span class="sxs-lookup"><span data-stu-id="c7fd6-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7fd6-128">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c7fd6-128">Requirements</span></span>  
 <span data-ttu-id="c7fd6-129">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7fd6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7fd6-130">**En-tête :** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c7fd6-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c7fd6-131">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7fd6-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c7fd6-132">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7fd6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7fd6-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7fd6-133">See also</span></span>

- [<span data-ttu-id="c7fd6-134">StrongNameGetPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="c7fd6-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="c7fd6-135">StrongNameTokenFromPublicKey, méthode</span><span class="sxs-lookup"><span data-stu-id="c7fd6-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="c7fd6-136">ICLRStrongName, interface</span><span class="sxs-lookup"><span data-stu-id="c7fd6-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="c7fd6-137">PublicKeyBlob, structure</span><span class="sxs-lookup"><span data-stu-id="c7fd6-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
