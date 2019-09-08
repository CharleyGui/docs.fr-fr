---
title: _AxlRSAKeyValueToPublicKeyToken fonction)
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 690035ffe0724d3987a198c78bf14e668527b98a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787021"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="81e09-102">\_AxlRSAKeyValueToPublicKeyToken fonction)</span><span class="sxs-lookup"><span data-stu-id="81e09-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="81e09-103">Convertit un modulo et un exposant en un jeton de clé publique de nom fort.</span><span class="sxs-lookup"><span data-stu-id="81e09-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81e09-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81e09-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="81e09-105">Parameters</span></span>  
 `pModulusBlob`  
 <span data-ttu-id="81e09-106">dans Objet BLOB modulo encodé en base64 (à partir de l' \<élément modulo >).</span><span class="sxs-lookup"><span data-stu-id="81e09-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="81e09-107">Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="81e09-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="81e09-108">dans Objet blob d’exposant encodé en base64 (à partir de \<l’élément de > exposant).</span><span class="sxs-lookup"><span data-stu-id="81e09-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="81e09-109">Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .</span><span class="sxs-lookup"><span data-stu-id="81e09-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="81e09-110">[en sortie] Un pointeur vers WCHAR \* pour recevoir le jeton de clé publique codé en hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="81e09-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81e09-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="81e09-111">Return Value</span></span>  
 <span data-ttu-id="81e09-112">`S_OK` si la fonction réussit.</span><span class="sxs-lookup"><span data-stu-id="81e09-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="81e09-113">Sinon, retourne un code d'erreur.</span><span class="sxs-lookup"><span data-stu-id="81e09-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e09-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="81e09-114">See also</span></span>

- [<span data-ttu-id="81e09-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="81e09-115">Authenticode</span></span>](index.md)
