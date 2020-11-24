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
ms.openlocfilehash: 5c1e2bfc7fd55e807af68744e28faa473daea772
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674214"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a>\_AxlRSAKeyValueToPublicKeyToken fonction)

Convertit un modulo et un exposant en un jeton de clé publique de nom fort.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `pModulusBlob`  
 dans Objet BLOB modulo encodé en base64 (à partir de l' \<Modulus> élément).  Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `pExponentBlob`  
 dans Objet blob d’exposant encodé en base64 (à partir de l' \<Exponent> élément). Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `ppwszPublicKeyToken`  
 [en sortie] Un pointeur vers WCHAR * pour recevoir le jeton de clé publique codé en hexadécimal.  
  
## <a name="return-value"></a>Valeur renvoyée  

 `S_OK` si la fonction réussit. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi

- [Authenticode](index.md)
