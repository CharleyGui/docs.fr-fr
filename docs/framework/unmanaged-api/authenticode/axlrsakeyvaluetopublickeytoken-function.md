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
ms.openlocfilehash: eca6c5fc61d4f7e80046102a560d228fc01e5292
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038415"
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
 dans Objet BLOB modulo encodé en base64 (à partir de l' \<élément modulo >).  Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `pExponentBlob`  
 dans Objet blob d’exposant encodé en base64 (à partir de \<l’élément de > exposant). Consultez la structure [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `ppwszPublicKeyToken`  
 [en sortie] Un pointeur vers WCHAR * pour recevoir le jeton de clé publique codé en hexadécimal.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si la fonction réussit. Sinon, retourne un code d'erreur.  
  
## <a name="see-also"></a>Voir aussi

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
