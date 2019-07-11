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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d98ebed2eb853d5dc8177b0b044bf654c3978494
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744347"
---
# <a name="symlinedelta-structure"></a>SYMLINEDELTA, structure
Fournit des informations pour le Gestionnaire de symboles sur les méthodes qui ont été déplacées à la suite de modifications.  
  
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
|`delta`|Le nombre de lignes de que la méthode a été déplacée.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym.idl  
  
## <a name="see-also"></a>Voir aussi

- [Structures du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
