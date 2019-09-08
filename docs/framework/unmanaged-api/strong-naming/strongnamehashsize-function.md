---
title: StrongNameHashSize, fonction
ms.date: 03/30/2017
api_name:
- StrongNameHashSize
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameHashSize
helpviewer_keywords:
- StrongNameHashSize function [.NET Framework strong naming]
ms.assetid: 738c98d7-a60c-45fe-a296-220af05e6991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53384a5aa7f8d11f868057f892f7b60aac2e9f02
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799042"
---
# <a name="strongnamehashsize-function"></a>StrongNameHashSize, fonction
Obtient la taille de mémoire tampon requise pour un hachage, à l’aide de l’algorithme de hachage spécifié.  
  
 Cette fonction a été dépréciée. Utilisez la méthode [ICLRStrongName :: StrongNameHashSize (](../hosting/iclrstrongname-strongnamehashsize-method.md) à la place.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
BOOLEAN StrongNameHashSize (  
    [in]  ULONG   ulHashAlg,  
    [out] DWORD   *pcbSize  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ulHashAlg`  
 dans Algorithme de hachage utilisé pour calculer la taille de la mémoire tampon.  
  
 `pcbSize`  
 à Taille de la mémoire tampon retournée, en octets.  
  
## <a name="return-value"></a>Valeur de retour  
 `true`en cas de réussite de l’opération ; Sinon, `false`.  
  
## <a name="remarks"></a>Notes  
 Si la `StrongNameHashSize` fonction ne se termine pas correctement, appelez la fonction [StrongNameErrorInfo](strongnameerrorinfo-function.md) pour récupérer la dernière erreur générée.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** StrongName.h  
  
 **Bibliothèque** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [StrongNameHashSize, méthode](../hosting/iclrstrongname-strongnamehashsize-method.md)
- [ICLRStrongName, interface](../hosting/iclrstrongname-interface.md)
