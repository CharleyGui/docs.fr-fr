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
ms.openlocfilehash: 7ae978f5d2c9f7e90f4549c15a3935b441eabf04
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434008"
---
# <a name="isymunmanagedreader-interface"></a>ISymUnmanagedReader, interface
Représente un lecteur de symboles qui fournit l’accès aux documents, aux méthodes et aux variables dans un magasin de symboles.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetDocument, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Recherche un document.|  
|[GetDocuments, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Retourne un tableau de tous les documents définis dans le magasin de symboles.|  
|[GetDocumentVersion, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Obtient la version spécifiée du document spécifié.|  
|[GetGlobalVariables, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Retourne toutes les variables globales.|  
|[GetMethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode.|  
|[GetMethodByVersion, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Obtient une méthode de lecteur de symboles, en fonction d’un jeton de méthode et d’un numéro de version de modification et de copie.|  
|[GetMethodFromDocumentPosition, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Retourne la méthode qui contient le point d’arrêt à la position donnée dans un document.|  
|[GetMethodsFromDocumentPosition, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Retourne un tableau de méthodes, chacune contenant le point d’arrêt à la position donnée dans un document.|  
|[GetMethodVersion, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Obtient la version de la méthode.|  
|[GetNamespaces, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Obtient les espaces de noms définis au niveau de la portée globale dans ce magasin de symboles.|  
|[GetSymAttribute, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Obtient un attribut personnalisé en fonction de son nom.|  
|[GetSymbolStoreFileName, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Fournit le nom de fichier sur disque du magasin de symboles.|  
|[GetUserEntryPoint, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Retourne la méthode spécifiée en tant que point d’entrée utilisateur pour le module, le cas échéant.|  
|[GetVariables, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Retourne une variable non locale, en fonction de son parent et de son nom.|  
|[Initialize, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Initialise le lecteur de symboles avec l’interface de l’importateur de métadonnées à laquelle ce lecteur sera associé, ainsi que le nom de fichier du module.|  
|[ReplaceSymbolStore, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|Remplace le magasin de symboles existant par un magasin de symboles delta.|  
|[UpdateSymbolStore, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|Met à jour le magasin de symboles existant avec un magasin de symboles delta.|  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
