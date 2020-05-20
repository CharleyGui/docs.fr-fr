---
title: ISymUnmanagedReader2, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: d4c5ff46d37b1292059b18920abd8042c18bbf31
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615395"
---
# <a name="isymunmanagedreader2-interface"></a>ISymUnmanagedReader2, interface
Représente un lecteur de symboles qui fournit l’accès aux documents, aux méthodes et aux variables dans un magasin de symboles. Cette interface étend l’interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) .  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetMethodByVersionPreRemap, méthode](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|Obtenir une méthode de lecteur de symboles, en fonction d’un jeton de méthode et d’un numéro de version modifier & continuer.|  
|[GetMethodsInDocument, méthode](isymunmanagedreader2-getmethodsindocument-method.md)|Obtient toutes les méthodes qui ont des informations de ligne dans le document fourni.|  
|[GetSymAttributePreRemap, méthode](isymunmanagedreader2-getsymattributepreremap-method.md)|Obtient un attribut personnalisé en fonction de son nom.|  
  
## <a name="requirements"></a>Conditions requises  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader, interface](isymunmanagedreader-interface.md)
