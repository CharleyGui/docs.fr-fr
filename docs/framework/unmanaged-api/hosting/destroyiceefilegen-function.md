---
title: DestroyICeeFileGen, fonction
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
ms.openlocfilehash: ff7e7b299d185b8db263d2076c1e075b87b487fc
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616396"
---
# <a name="destroyiceefilegen-function"></a>DestroyICeeFileGen, fonction
Détruit un objet [ICeeFileGen](iceefilegen-class.md) .  
  
 Cette fonction a été dépréciée dans le .NET Framework 4.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `ceeFileGen`  
 dans `ICeeFileGen`Objet à détruire.  
  
## <a name="return-value"></a>Valeur de retour  
 Cette méthode retourne des codes d’erreur COM standard.  
  
## <a name="remarks"></a>Notes  
 `DestroyICeeFileGen`détruit l' `ICeeFileGen` objet créé par la fonction [CreateICeeFileGen,](createiceefilegen-function.md) .  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** ICeeFileGen. h  
  
 **Bibliothèque :** MSCorPE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonction d'hébergement du CLR déconseillées](deprecated-clr-hosting-functions.md)
