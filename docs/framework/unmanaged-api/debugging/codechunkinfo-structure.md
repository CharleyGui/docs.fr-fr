---
title: CodeChunkInfo, structure
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
ms.openlocfilehash: d33c8b31473e389e07fb24076dc32272e9dde387
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132401"
---
# <a name="codechunkinfo-structure"></a>CodeChunkInfo, structure

Représente un bloc de code unique en mémoire.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`startAddr`|Valeur `CORDB_ADDRESS` qui spécifie l’adresse de début du bloc.|  
|`length`|Taille, en octets, du segment.|  
  
## <a name="remarks"></a>Notes  
 Le segment de code unique est une région de code natif qui fait partie d’un objet de code tel qu’une fonction.  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** CorDebug. idl  
  
 **Bibliothèque :** CorGuids.lib  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [GetCodeChunks, méthode](icordebugcode2-getcodechunks-method.md)
- [Structures de débogage](debugging-structures.md)
- [Débogage](index.md)
