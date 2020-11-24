---
title: GetALinkMessageDll, fonction
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
ms.openlocfilehash: 554bd32ae965b21a88a09577749bbd7975f5ec7e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684744"
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll, fonction

Recherche et charge la DLL du message. Retourne 0 si la DLL du message est introuvable ou n’a pas pu être chargée. La DLL du message doit se trouver dans un sous-répertoire dont le nom est un ID de langue ou dans le répertoire actif.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** ALink. h  
  
 **Bibliothèque**: alink.dll  
  
## <a name="see-also"></a>Voir aussi

- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
