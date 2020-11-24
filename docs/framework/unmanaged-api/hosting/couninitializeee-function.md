---
title: CoUninitializeEE, fonction
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: e6616392eaa23f8ba40247c5aabd12e4d530cea1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687845"
---
# <a name="couninitializeee-function"></a>CoUninitializeEE, fonction

`CoUninitializeEE` est obsolète et ne fournit aucune fonctionnalité.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a>Notes  

 Le moteur d’exécution de common language runtime ne peut pas être déchargé d’un processus. Pour arrêter l’appel du moteur d’exécution [CorExitProcess,](corexitprocess-function.md).  
  
## <a name="see-also"></a>Voir aussi

- [CoInitializeEE, fonction](coinitializeee-function.md)
- [Fonctions statiques globales des métadonnées](../metadata/metadata-global-static-functions.md)
