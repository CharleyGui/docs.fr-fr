---
title: CreateICeeFileGen, fonction
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
ms.openlocfilehash: 454cfa2dd1b676f32649050625b1074fbd776d54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673330"
---
# <a name="createiceefilegen-function"></a>CreateICeeFileGen, fonction

Crée un objet [ICeeFileGen](iceefilegen-class.md) .  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `ceeFileGen`  
 à Pointeur vers l’adresse d’un nouvel `ICeeFileGen` objet.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Cette méthode retourne des codes d’erreur COM standard.  
  
## <a name="remarks"></a>Remarques  

 L' `ICeeFileGen` objet permet de créer des fichiers exécutables portables (PE, Portable Executable) Common Language Runtime (CLR).  
  
 Appelez la fonction [DestroyICeeFileGen,](destroyiceefilegen-function.md) pour détruire l' `ICeeFileGen` objet une fois l’opération terminée.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** ICeeFileGen. h  
  
 **Bibliothèque :** MSCorPE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
