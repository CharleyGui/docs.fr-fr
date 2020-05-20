---
title: SYMLINEDELTA, structure
ms.date: 03/30/2017
api_name:
- SYMLINEDELTA
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SYMLINEDELTA
helpviewer_keywords:
- SYMLINEDELTA structure [.NET Framework debugging]
ms.assetid: 9634e995-d46d-4397-ab66-cc5781d11e4e
topic_type:
- apiref
ms.openlocfilehash: fb3b89d25b4c2e23c3980b167db4279246c4d27b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609298"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA, structure
Fournit des informations au gestionnaire de symboles sur les méthodes qui ont été déplacées suite à des modifications.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _SYMLINEDELTA  
    {  
        mdMethodDef  mdMethod;  
        INT32        delta;  
    } SYMLINEDELTA;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`mdMethod`|Jeton de métadonnées de la méthode.|  
|`delta`|Nombre de lignes dans lesquelles la méthode a été déplacée.|  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl  
  
## <a name="see-also"></a>Voir aussi

- [Structures du magasin de symboles de diagnostics](diagnostics-symbol-store-structures.md)
