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
ms.openlocfilehash: 63719d0c6e13768e9dc7ed80e52e2a293e32a8a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449343"
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
