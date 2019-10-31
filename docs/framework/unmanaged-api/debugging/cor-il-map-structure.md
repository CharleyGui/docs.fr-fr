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
ms.openlocfilehash: c37f039d9636854c464e7981693c573bd60deab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132344"
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
|`oldOffset`|Ancien offset MSIL (Microsoft Intermediate Language) par rapport au début de la fonction.|  
|`newOffset`|Nouveau décalage MSIL par rapport au début de la fonction.|  
|`fAccurate`|`true` si le mappage est reconnu comme étant exact ; Sinon, `false`.|  
  
## <a name="remarks"></a>Notes  
 Le format du mappage est le suivant : le débogueur suppose que `oldOffset` fait référence à un décalage MSIL dans le code MSIL non modifié d’origine. Le paramètre `newOffset` fait référence à l’offset MSIL correspondant dans le nouveau code instrumenté.  
  
 Pour que l’exécution pas à pas fonctionne correctement, les conditions suivantes doivent être remplies :  
  
- La carte doit être triée par ordre croissant.  
  
- Le code MSIL instrumenté ne doit pas être réorganisé.  
  
- Le code MSIL d’origine ne doit pas être supprimé.  
  
- Le mappage doit inclure des entrées pour mapper tous les points de séquence à partir du fichier de base de données du programme (PDB).  
  
 Le mappage n’interpole pas les entrées manquantes. L’exemple suivant montre un mappage et ses résultats.  
  
 Canal  
  
- 0 ancien décalage, 0 nouveau décalage  
  
- 5 ancien décalage, 10 nouveaux décalages  
  
- 9 ancien décalage, 20 nouveau décalage  
  
 About  
  
- Un ancien décalage de 0, 1, 2, 3 ou 4 sera mappé à un nouveau décalage de 0.  
  
- Un ancien décalage de 5, 6, 7 ou 8 sera mappé au nouveau décalage 10.  
  
- Un ancien décalage de 9 ou plus sera mappé au nouveau décalage 20.  
  
- Un nouveau décalage de 0, 1, 2, 3, 4, 5, 6, 7, 8 ou 9 sera mappé à l’ancien décalage 0.  
  
- Un nouveau décalage de 10, 11, 12, 13, 14, 15, 16, 17, 18 ou 19 sera mappé à l’ancien décalage 5.  
  
- Un nouveau décalage de 20 ou plus sera mappé à l’ancien décalage 9.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl, CorProf. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
