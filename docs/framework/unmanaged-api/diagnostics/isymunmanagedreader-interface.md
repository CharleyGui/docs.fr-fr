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
Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.  
  
## <a name="methods"></a>Méthodes  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetDocument, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|Finds a document.|  
|[GetDocuments, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|Returns an array of all the documents defined in the symbol store.|  
|[GetDocumentVersion, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|Gets the specified version of the specified document.|  
|[GetGlobalVariables, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|Returns all global variables.|  
|[GetMethod, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|Gets a symbol reader method, given a method token.|  
|[GetMethodByVersion, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|Gets a symbol reader method, given a method token and an edit-and-copy version number.|  
|[GetMethodFromDocumentPosition, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|Returns the method that contains the breakpoint at the given position in a document.|  
|[GetMethodsFromDocumentPosition, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|Returns an array of methods, each of which contains the breakpoint at the given position in a document.|  
|[GetMethodVersion, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|Gets the method version.|  
|[GetNamespaces, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|Gets the namespaces defined at global scope within this symbol store.|  
|[GetSymAttribute, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|Gets a custom attribute based upon its name.|  
|[GetSymbolStoreFileName, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|Provides the on-disk file name of the symbol store.|  
|[GetUserEntryPoint, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|Returns the method that was specified as the user entry point for the module, if any.|  
|[GetVariables, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|Return a non-local variable, given its parent and name.|  
|[Initialize, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.|  
|[ReplaceSymbolStore, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|Remplace le magasin de symboles existant par un magasin de symboles delta.|  
|[UpdateSymbolStore, méthode](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|Met à jour le magasin de symboles existant avec un magasin de symboles delta.|  
  
## <a name="requirements"></a>spécifications  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Voir aussi

- [Interfaces du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedReader2, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
