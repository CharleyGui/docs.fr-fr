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
ms.openlocfilehash: 989e99198efd1519f607a2e3164ff4de584e88af
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679882"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a>\_AxlPublicKeyBlobToPublicKeyToken fonction)

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
  
## <a name="return-value"></a>Valeur renvoyée  

 `S_OK` si la fonction réussit ; sinon `S_FALSE`.  
  
## <a name="see-also"></a>Voir aussi

- [Authenticode](index.md)
