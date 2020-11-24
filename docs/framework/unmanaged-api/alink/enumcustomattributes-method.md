---
title: EnumCustomAttributes, méthode
ms.date: 03/30/2017
api_name:
- EnumCustomAttributes
- IALink.EnumCustomAttributes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EnumCustomAttributes
helpviewer_keywords:
- EnumCustomAttributes method
ms.assetid: 08dff60c-f01b-4050-8865-ea3f95361c9f
topic_type:
- apiref
ms.openlocfilehash: 445c833d10631341ef7ad579eaff8ddd96be3428
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684848"
---
# <a name="enumcustomattributes-method"></a>EnumCustomAttributes, méthode

Récupère des attributs personnalisés au niveau de l’assembly.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumCustomAttributes(  
    HALINKENUM hEnum,  
    mdToken tkType,  
    mdCustomAttribute rCustomValues[],  
    ULONG cMax,  
    ULONG* pcCustomValues  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `hEnum`  
 Handle de l’énumérateur.  
  
 `tkType`  
 Type des attributs à énumérer. Utilisez `mdTokenNill` pour tous les attributs.  
  
 `rCustomValues`  
 Reçoit des jetons d’attributs personnalisés.  
  
 `cMax`  
 Spécifie la taille du `rCustomValues` tableau.  
  
 `pcCustomValues`  
 Reçoit éventuellement le nombre de valeurs de jeton.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink, interface](ialink-interface.md)
- [IALink2, interface](ialink2-interface.md)
- [API ALink](index.md)
