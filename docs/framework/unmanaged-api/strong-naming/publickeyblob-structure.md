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
ms.openlocfilehash: 3b00bf8295a635871bd7263928ff21c97053cc39
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176953"
---
# <a name="publickeyblob-structure"></a>PublicKeyBlob, structure
Représente, en format binaire, la clé publique d’une paire de clés public/privé.  
  
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
|`SigAlgId`|L’identifiant pour l’algorithme `ALG_ID`de signature (de type , tel que défini dans WinCrypt.h) de la clé publique.|  
|`HashAlgId`|L’identifiant pour l’algorithme `ALG_ID`de hachage (de type , tel que défini dans WinCrypt.h) de la clé publique.|  
|`cbPublicKey`|La longueur de la clé dans les octets.|  
|`PublicKey`|Un tableau d’endlète à longueur variable qui contient la valeur clé dans le format retourné par le CryptoAPI.|  
  
## <a name="remarks"></a>Notes   
 La `PublicKeyBlob` structure est utilisée par [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), et d’autres fonctions de nom forte pour représenter la clé publique d’une paire de clés public/privé.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** StrongName.h (en)  
  
 **Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameGetPublicKey, fonction](strongnamegetpublickey-function.md)
- [StrongNameSignatureGeneration, fonction](strongnamesignaturegeneration-function.md)
