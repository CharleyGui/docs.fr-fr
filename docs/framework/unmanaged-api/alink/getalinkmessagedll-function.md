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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 323e53c45a26d5703548ebe9863978f6d3929f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787482"
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll, fonction
Recherche et charge la DLL du message. Retourne 0 si la DLL du message est introuvable ou n’a pas pu être chargée. La DLL du message doit se trouver dans un sous-répertoire dont le nom est un ID de langue ou dans le répertoire actif.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** ALink. h  
  
 **Bibliothèque**: ALink. dll  
  
## <a name="see-also"></a>Voir aussi

- [Al.exe (Assembly Linker)](../../tools/al-exe-assembly-linker.md)
