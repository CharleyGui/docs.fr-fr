---
title: Interfaces du magasin de symboles de diagnostics
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: bdb691570a9a2bf7bd2bb21af500b06c10b0bc53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448528"
---
# <a name="diagnostics-symbol-store-interfaces"></a>Interfaces du magasin de symboles de diagnostics
Cette rubrique décrit les interfaces non managées qui permettent à un compilateur de générer des informations de symbole pour une utilisation par un débogueur.  
  
## <a name="in-this-section"></a>Dans cette section  
 [IBindingDisplay, interface](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 Fournit des méthodes qui affichent les informations de liaison actuelles sur l’application en cours d’exécution.  
  
 [IDebugAutoAttach, interface](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 Définit l’interface pour un attachement automatique du débogueur appelé par le serveur.  
  
 [INotifyConnection2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 Déclare des méthodes pour l’inscription et l’annulation de l’inscription d’une source de notification de connexion.  
  
 [INotifySink2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 Déclare des méthodes pour la notification du récepteur.  
  
 [INotifySource2, interface](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 Déclare une méthode pour définir des filtres de notification.  
  
 [ISymENCUnmanagedMethod, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 Fournit des informations pour la fonctionnalité modifier et continuer.  
  
 [ISymUnmanagedAsyncMethod, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 Cette interface est le complément de lecture de l' [interface ISymUnmanagedAsyncMethodPropertiesWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 Autorise la définition d’informations de méthode Async facultatives par symbole de méthode. Doit utiliser avec une méthode ouverte (c’est-à-dire entre les appels à la [méthode OpenMethod,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)et la [méthode CloseMethod,](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).  
  
 [ISymUnmanagedBinder, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 Représente un Binder de symboles pour du code non managé.  
  
 [ISymUnmanagedBinder2, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 Représente un Binder de symboles pour du code non managé et étend l’interface `ISymUnmanagedBinder`.  
  
 [ISymUnmanagedBinder3, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 Représente un Binder de symboles pour du code non managé et étend l’interface `ISymUnmanagedBinder`.  
  
 [ISymUnmanagedConstant, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 Fournit l’accès aux constantes non managées.  
  
 [ISymUnmanagedDispose, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 Supprime les ressources non managées.  
  
 [ISymUnmanagedDocument, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 Représente un document référencé par un magasin de symboles.  
  
 [ISymUnmanagedDocumentWriter, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 Fournit des méthodes d'écriture dans un document référencé par un magasin de symboles.  
  
 [ISymUnmanagedENCUpdate, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 Fournit des méthodes pour la fonctionnalité modifier et continuer.  
  
 [ISymUnmanagedMethod, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 Représente une méthode dans le magasin de symboles.  
  
 [ISymUnmanagedNamespace, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 Représente un espace de noms.  
  
 [ISymUnmanagedReader, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 Représente un lecteur de symboles qui fournit l’accès aux documents, aux méthodes et aux variables dans un magasin de symboles.  
  
 [ISymUnmanagedReader2, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 Obtient une méthode de lecteur de symboles en fonction d’un jeton de méthode et d’un numéro de version de modification et de copie.  
  
 [ISymUnmanagedReaderSymbolSearchInfo, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 Fournit des méthodes qui obtiennent des informations de recherche de symboles.  
  
 [ISymUnmanagedScope, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 Représente une portée lexicale dans une méthode.  
  
 [ISymUnmanagedScope2, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 Représente une portée lexicale dans une méthode et étend l’interface de `ISymUnmanagedScope` avec des méthodes qui obtiennent des informations sur les constantes définies dans la portée.  
  
 [ISymUnmanagedSourceServerModule, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 Fournit les données du serveur source pour un module.  
  
 [ISymUnmanagedSymbolSearchInfo, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 Fournit des méthodes qui obtiennent des informations sur le chemin de recherche.  
  
 [ISymUnmanagedVariable, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 Représente une variable, telle qu’un paramètre, une variable locale ou un champ.  
  
 [ISymUnmanagedWriter, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables.  
  
 [ISymUnmanagedWriter2, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables. Étend l’interface `ISymUnmanagedWriter`.  
  
 [ISymUnmanagedWriter3, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 Représente un writer de symboles et fournit des méthodes pour définir des documents, des points de séquence, des étendues lexicales et des variables. Étend l’interface `ISymUnmanagedWriter`.  
  
 [ISymUnmanagedWriter4, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 Interface Isymunmanagedwriter4,.  
  
 [ISymUnmanagedWriter5, interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 Interface ISymUnmanagedWriter5.  
  
## <a name="related-sections"></a>Sections connexes  
 [Énumérations du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [Structures du magasin de symboles de diagnostics](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [Débogage](../../../../docs/framework/unmanaged-api/debugging/index.md)
