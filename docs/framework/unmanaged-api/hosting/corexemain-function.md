---
title: _CorExeMain, fonction
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
ms.openlocfilehash: 935ac478fb966315e81fdcc004761038b28e3178
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616588"
---
# <a name="_corexemain-function"></a>_CorExeMain, fonction
Initialise le common language runtime (CLR), localise le point d’entrée managé dans l’en-tête CLR de l’assembly exécutable et commence l’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a>Notes  
 Cette fonction est appelée par le chargeur dans les processus créés à partir d’assemblys exécutables managés. Pour les assemblys DLL, le chargeur appelle à la place la fonction [_CorDllMain](cordllmain-function.md) .  
  
 Le chargeur du système d’exploitation appelle cette méthode quel que soit le point d’entrée spécifié dans le fichier image.  
  
 Dans Windows 98, Windows ME, Windows NT et Windows 2000, la `_CorExeMain` fonction est appelée indirectement via une correction dans le chargeur du système d’exploitation. Dans toutes les autres versions de Windows, il est appelé directement par le chargeur du système d’exploitation.  
  
 Pour plus d’informations, consultez la section Notes de la rubrique [_CorValidateImage](corvalidateimage-function.md) .  
  
## <a name="requirements"></a>Conditions requises  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales des métadonnées](../metadata/metadata-global-static-functions.md)
