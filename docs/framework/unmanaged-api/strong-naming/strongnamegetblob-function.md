---
title: StrongNameGetBlob, fonction
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
ms.openlocfilehash: 8f5cb89294004dfb1f020627ceb1edb58735f72c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732279"
---
# <a name="strongnamegetblob-function"></a>StrongNameGetBlob, fonction

Remplit la mémoire tampon spécifiée avec la représentation binaire du fichier exécutable à l’adresse spécifiée.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameGetBlob (](../hosting/iclrstrongname-strongnamegetblob-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `wszFilePath`  
 dans Chemin d’accès valide au fichier exécutable à charger.  
  
 `pbBlob`  
 dans Mémoire tampon dans laquelle charger le fichier exécutable.  
  
 `pcbBlob`  
 [in, out] Taille maximale demandée, en octets, de `pbBlob` . Lors du retour, taille réelle, en octets, de `pbBlob` .  
  
## <a name="return-value"></a>Valeur renvoyée  

 `true` en cas de réussite de l’opération ; Sinon, `false` .  
  
## <a name="remarks"></a>Remarques  

 Si la `StrongNameGetBlob` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameGetBlob, méthode](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [StrongNameGetBlobFromImage, méthode](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
