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
# <a name="_axlpublickeyblobtopublickeytoken-function"></a>\_fonction AxlPublicKeyBlobToPublicKeyToken
Calcule le jeton de clé publique de nom fort à partir d'un format CSP PUBLICKEYBLOB.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `pCspPublicKeyBlob`  
 [en entrée] L'objet blob de clé publique CSP.  
  
 `ppwszPublicKeyHash`  
 [en sortie] Un pointeur vers WCHAR * pour recevoir le hachage de clé publique codé au format hexadécimal.  
  
## <a name="return-value"></a>Valeur de retour  
 `S_OK` si la fonction réussit ; sinon `S_FALSE`.  
  
## <a name="see-also"></a>Voir aussi

- [Authenticode](index.md)
