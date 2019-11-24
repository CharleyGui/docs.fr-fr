---
title: GetPublicKeyToken, méthode
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
ms.openlocfilehash: 2e7ed4e1529104db30b0b06665f74342d9ca9a01
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447242"
---
# <a name="getpublickeytoken-method"></a>GetPublicKeyToken, méthode
Retrieves the public key token for a given keyfile or key container.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  
 `pszKeyFile`  
 Filename of the key.  
  
 `pszKeyContainer`  
 Name of the key container.  
  
 `pvPublicKeyToken`  
 Address where key token is to be stored.  
  
 `pcbPublicKeyToken`  
 Specifies the size, in bytes, of the buffer indicated by `pvPublicKeyToken`. Upon return, contains actual number of bytes used.  
  
## <a name="return-value"></a>Valeur de retour  
 Returns S_OK if the method succeeds.  
  
## <a name="requirements"></a>spécifications  
 Requires alink.h.  
  
## <a name="see-also"></a>Voir aussi

- [IALink2, interface](ialink2-interface.md)
- [IALink, interface](ialink-interface.md)
- [API ALink](index.md)
