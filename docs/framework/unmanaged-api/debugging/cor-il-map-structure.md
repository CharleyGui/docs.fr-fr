---
title: COR_IL_MAP, structure
ms.date: 03/30/2017
api_name:
- COR_IL_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_IL_MAP
helpviewer_keywords:
- COR_IL_MAP structure [.NET Framework debugging]
ms.assetid: 534ebc17-963d-4b26-8375-8cd940281db3
topic_type:
- apiref
ms.openlocfilehash: 4c79d0e4e37f3f884651e49c8fff6db72fac4f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179293"
---
# <a name="cor_il_map-structure"></a>COR_IL_MAP, structure
Spécifie des modifications dans le décalage relatif d'une fonction.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_IL_MAP {  
    ULONG32 oldOffset;
    ULONG32 newOffset;
    BOOL    fAccurate;  
} COR_IL_MAP;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`oldOffset`|L’ancien langage intermédiaire Microsoft (MSIL) compensé par rapport au début de la fonction.|  
|`newOffset`|Le nouveau RAPPORT MSIL par rapport au début de la fonction.|  
|`fAccurate`|`true`si la cartographie est connue pour être exacte; autrement, `false`.|  
  
## <a name="remarks"></a>Notes   
 Le format de la carte est le suivant : `oldOffset` le débbugeur suppose qu’il s’agit d’un décalage MSIL dans le code MSIL original et non modifié. Le `newOffset` paramètre se réfère à la compensation MSIL correspondante dans le nouveau code instrumenté.  
  
 Pour passer au travail correctement, les exigences suivantes doivent être remplies :  
  
- La carte doit être triée dans l’ordre ascendant.  
  
- Le code MSIL instrumenté ne doit pas être réorganisé.  
  
- Le code MSIL original ne doit pas être supprimé.  
  
- La carte doit inclure des entrées pour cartographier tous les points de séquence du fichier de base de données du programme (PDB).  
  
 La carte n’interpole pas les entrées manquantes. L’exemple suivant montre une carte et ses résultats.  
  
 Carte:  
  
- 0 ancien décalage, 0 nouveau décalage  
  
- 5 vieux décalage, 10 nouveaux décalages  
  
- 9 décalage ancien, 20 nouveaux décalages  
  
 Résultats :  
  
- Un ancien décalage de 0, 1, 2, 3 ou 4 sera cartographié à un nouveau décalage de 0.  
  
- Un ancien décalage de 5, 6, 7 ou 8 sera cartographié à nouveau décalage 10.  
  
- Un ancien décalage de 9 ou plus sera cartographié à nouveau décalage 20.  
  
- Un nouveau décalage de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 sera cartographié à l’ancien décalage 0.  
  
- Un nouveau décalage de 10, 11, 12, 13, 14, 15, 16, 17, 18, ou 19 sera cartographié à l’ancien décalage 5.  
  
- Un nouveau décalage de 20 ou plus sera cartographié à l’ancien décalage 9.  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête:** CorDebug.idl, CorProf.idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
