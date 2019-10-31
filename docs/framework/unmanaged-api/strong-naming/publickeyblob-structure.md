---
title: PublicKeyBlob, structure
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
ms.openlocfilehash: 6c58a0726e0869178838999c6b000e0ad975f145
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140605"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob, structure
Représente, au format binaire, la clé publique d’une paire de clés publique/privée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;   
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`SigAlgId`|Identificateur de l’algorithme de signature (de type `ALG_ID`, tel que défini dans WinCrypt. h) de la clé publique.|  
|`HashAlgId`|Identificateur de l’algorithme de hachage (de type `ALG_ID`, tel que défini dans WinCrypt. h) de la clé publique.|  
|`cbPublicKey`|Longueur de la clé, en octets.|  
|`PublicKey`|Tableau d’octets de longueur variable qui contient la valeur de clé dans le format retourné par l’CryptoAPI.|  
  
## <a name="remarks"></a>Notes  
 La structure `PublicKeyBlob` est utilisée par [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)et d’autres fonctions Strong Name pour représenter la clé publique d’une paire de clés publique/privée.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameGetPublicKey, fonction](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration, fonction](strongnamesignaturegeneration-function.md)
