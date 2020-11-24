---
title: ISymUnmanagedReader, interface
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
ms.openlocfilehash: bca84fdba575ed9bfe572b9fd7a5869620962de6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675865"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader, interface

Représente un lecteur de symboles qui fournit l’accès aux documents, aux méthodes et aux variables d’un magasin de symboles.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetDocument, méthode](isymunmanagedreader-getdocument-method.md)|Recherche un document.|  
|[GetDocuments, méthode](isymunmanagedreader-getdocuments-method.md)|Retourne un tableau de tous les documents définis dans le magasin de symboles.|  
|[GetDocumentVersion, méthode](isymunmanagedreader-getdocumentversion-method.md)|Obtient la version spécifiée du document spécifié.|  
|[GetGlobalVariables, méthode](isymunmanagedreader-getglobalvariables-method.md)|Retourne toutes les variables globales.|  
|[GetMethod, méthode](isymunmanagedreader-getmethod-method.md)|Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode.|  
|[GetMethodByVersion, méthode](isymunmanagedreader-getmethodbyversion-method.md)|Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et d’un numéro de version de modification et de copie.|  
|[GetMethodFromDocumentPosition, méthode](isymunmanagedreader-getmethodfromdocumentposition-method.md)|Retourne la méthode qui contient le point d’arrêt à la position donnée dans un document.|  
|[GetMethodsFromDocumentPosition, méthode](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Retourne un tableau de méthodes, chacune contenant le point d’arrêt à la position donnée dans un document.|  
|[GetMethodVersion, méthode](isymunmanagedreader-getmethodversion-method.md)|Obtient la version de la méthode.|  
|[GetNamespaces, méthode](isymunmanagedreader-getnamespaces-method.md)|Obtient les espaces de noms définis au niveau de la portée globale dans ce magasin de symboles.|  
|[GetSymAttribute, méthode](isymunmanagedreader-getsymattribute-method.md)|Obtient un attribut personnalisé en fonction de son nom.|  
|[GetSymbolStoreFileName, méthode](isymunmanagedreader-getsymbolstorefilename-method.md)|Fournit le nom de fichier sur disque du magasin de symboles.|  
|[GetUserEntryPoint, méthode](isymunmanagedreader-getuserentrypoint-method.md)|Retourne la méthode spécifiée en tant que point d’entrée utilisateur pour le module, le cas échéant.|  
|[GetVariables, méthode](isymunmanagedreader-getvariables-method.md)|Retourne une variable non locale, en fonction de son parent et de son nom.|  
|[Initialize, méthode](isymunmanagedreader-initialize-method.md)|Initialise le lecteur de symboles avec l’interface de l’importateur de métadonnées à laquelle ce lecteur sera associé, ainsi que le nom de fichier du module.|  
|[ReplaceSymbolStore, méthode](isymunmanagedreader-replacesymbolstore-method.md)|Remplace le magasin de symboles existant par un magasin de symboles delta.|  
|[UpdateSymbolStore, méthode](isymunmanagedreader-updatesymbolstore-method.md)|Met à jour le magasin de symboles existant avec un magasin de symboles delta.|  
  
## <a name="requirements"></a>Configuration requise  

 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2, interface](isymunmanagedreader2-interface.md)
