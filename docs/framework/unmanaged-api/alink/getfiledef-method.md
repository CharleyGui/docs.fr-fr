---
title: GetFileDef, méthode
ms.date: 03/30/2017
api_name:
- IALink2.GetFileDef
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetFileDef
helpviewer_keywords:
- GetFileDef method
ms.assetid: 4e3fbe6c-b82a-4181-ab17-7faa1263f5b3
topic_type:
- apiref
ms.openlocfilehash: 42935813579d7f1d55a9f1daf9d8c6c1241f85be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684705"
---
# <a name="getfiledef-method"></a>GetFileDef, méthode

Récupère le jeton FileDef réel utilisé dans les métadonnées (par opposition au jeton assigné par ALink).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFileDef(  
    mdAssembly AssemblyID,  
    mdFile TargetFile,  
    mdFile* pScope  
) PURE;  
```  
  
## <a name="parameters"></a>Paramètres  

 `AssemblyID`  
 ID de l’assembly.  
  
 `TargetFile`  
 Jeton du fichier ajouté tel qu’il a été récupéré à partir de la méthode AddFile ou de la méthode AddImport,.  
  
 `pScope`  
 Reçoit le jeton FileDef.  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne S_OK si la méthode est réussie.  
  
## <a name="requirements"></a>Configuration requise  

 Requiert ALink. h  
  
## <a name="see-also"></a>Voir aussi

- [IALink2, interface](ialink2-interface.md)
- [IALink, interface](ialink-interface.md)
- [API ALink](index.md)
