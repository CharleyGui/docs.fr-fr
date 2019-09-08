---
title: StrongNameSignatureSize, fonction
ms.date: 03/30/2017
api_name:
- StrongNameSignatureSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureSize
helpviewer_keywords:
- StrongNameSignatureSize function [.NET Framework strong naming]
ms.assetid: 4fde4cd0-f53e-4411-a2fe-fc5c54472f95
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38f98b971e430a2c35a4c484f4f9c4bf387c640c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798954"
---
# <a name="strongnamesignaturesize-function"></a>StrongNameSignatureSize, fonction
Retourne la taille de la signature de nom fort. `StrongNameSignatureSize`est généralement utilisé par les compilateurs pour déterminer la quantité d’espace à réserver dans le fichier lors de la création d’un assembly à signature différée.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameSignatureSize (](../hosting/iclrstrongname-strongnamesignaturesize-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameSignatureSize (   
    [in]  BYTE   *pbPublicKeyBlob,  
    [in]  ULONG  cbPublicKeyBlob,   
    [in]  DWORD  *pcbSize  
);   
```  
  
## <a name="parameters"></a>Paramètres  
 `pbPublicKeyBlob`  
 dans Structure de type [publicKeyBlob](publickeyblob-structure.md) qui contient la partie publique de la paire de clés utilisée pour générer la signature de nom fort.  
  
 `cbPublicKeyBlob`  
 dans Taille, en octets, de `pbPublicKeyBlob`.  
  
 `pcbSize`  
 dans Nombre d’octets requis pour stocker la signature de nom fort.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`en cas de réussite de l’opération ; Sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Si la `StrongNameSignatureSize` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameSignatureSize, méthode](../hosting/iclrstrongname-strongnamesignaturesize-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
