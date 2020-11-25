---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset, méthode
ms.date: 03/30/2017
ms.assetid: 92af7896-2201-408d-8b1b-23e28001eeac
ms.openlocfilehash: a37d319a39b959700944f9e111d2945e286c99ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707137"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinecatchhandleriloffset-method"></a>ISymUnmanagedAsyncMethodPropertiesWriter::DefineCatchHandlerILOffset, méthode

Définit l’offset IL pour le gestionnaire catch généré par le compilateur qui encapsule une méthode Async.  
  
 Le décalage IL de l’interception générée est utilisé par le débogueur pour gérer le catch comme s’il s’agissait de code non-utilisateur, même s’il peut se produire dans une méthode de code utilisateur. En particulier, elle est utilisée en réponse à un événement d’exception **CatchHandlerFound** .  
  
## <a name="syntax"></a>Syntaxe  
  
```idl  
HRESULT DefineCatchHandlerILOffset(    [in] ULONG32 catchHandlerOffset);  
```  
  
## <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`catchHandlerOffset`||  
  
## <a name="return-value"></a>Valeur renvoyée  

 Retourne `HRESULT`.  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [ISymUnmanagedAsyncMethodPropertiesWriter, interface](isymunmanagedasyncmethodpropertieswriter-interface.md)
