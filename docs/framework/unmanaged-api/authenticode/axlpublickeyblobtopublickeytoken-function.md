---
title: _AxlPublicKeyBlobToPublicKeyToken, fonction
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
ms.openlocfilehash: 33b8f47813a3bf43bd69741c9febb150fa3a92e3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099908"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="768ba-102">\_fonction AxlPublicKeyBlobToPublicKeyToken</span><span class="sxs-lookup"><span data-stu-id="768ba-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>
<span data-ttu-id="768ba-103">Calcule le jeton de clé publique de nom fort à partir d'un format CSP PUBLICKEYBLOB.</span><span class="sxs-lookup"><span data-stu-id="768ba-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="768ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="768ba-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="768ba-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="768ba-105">Parameters</span></span>  
 `pCspPublicKeyBlob`  
 <span data-ttu-id="768ba-106">[en entrée] L'objet blob de clé publique CSP.</span><span class="sxs-lookup"><span data-stu-id="768ba-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="768ba-107">[en sortie] Un pointeur vers WCHAR \* pour recevoir le hachage de clé publique codé au format hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="768ba-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="768ba-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="768ba-108">Return Value</span></span>  
 <span data-ttu-id="768ba-109">`S_OK` si la fonction réussit ; sinon `S_FALSE`.</span><span class="sxs-lookup"><span data-stu-id="768ba-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="768ba-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="768ba-110">See also</span></span>

- [<span data-ttu-id="768ba-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="768ba-111">Authenticode</span></span>](index.md)
