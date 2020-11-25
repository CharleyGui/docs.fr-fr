---
title: Application d'attributs d'interopérabilité
description: Cet article résume les attributs COM Interop de l’espace de noms System. Runtime. InteropServices, y compris les attributs de l’outil de conversion et de la conception.
ms.date: 03/30/2017
helpviewer_keywords:
- design-time attributes
- .NET, exposing components to COM
- attributes [.NET], design-time functionality
- conversion-tool attributes
- attributes [.NET], interop-specific
- attributes [.NET], conversion-tool
- interoperation with unmanaged code, applying attributes
- interoperation with unmanaged code, exposing .NET components
- COM interop, exposing COM components
- COM interop, applying attributes
ms.assetid: b6014613-641c-4912-9e2f-83a99210a037
ms.openlocfilehash: 38632c5a1f462c3a7b537978fde81424916746da
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706292"
---
# <a name="applying-interop-attributes"></a>Application d'attributs d'interopérabilité

L’espace de noms <xref:System.Runtime.InteropServices> propose trois catégories d’attributs spécifiques à l’interopérabilité : ceux que vous appliquez au moment du design, ceux que les interfaces API et les outils de COM Interop appliquent au cours du processus de conversion et ceux que vous appliquez ou que COM Interop applique.  
  
 Si vous n’êtes pas habitué aux tâches relatives à l’application d’attributs à du code managé, consultez [Extension des métadonnées à l’aide des attributs](../attributes/index.md). Comme pour les autres attributs personnalisés, vous pouvez appliquer des attributs spécifiques à l’interopérabilité à des types, à des méthodes, à des paramètres, à des propriétés, à des champs et à d’autres membres.  
  
## <a name="design-time-attributes"></a>Attributs au moment du design  

 Vous pouvez ajuster le résultat du processus de conversion effectué par les interfaces API et les outils de COM Interop à l’aide d’attributs au moment du design. Le tableau suivant décrit les attributs que vous pouvez appliquer à votre code source managé. Les outils de COM Interop peuvent également parfois appliquer les attributs décrits dans ce tableau.  
  
|Attribut|Description|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.AutomationProxyAttribute>|Indique si le type doit être marshalé en utilisant Automation Marshaler ou un proxy et un stub personnalisés.|  
|<xref:System.Runtime.InteropServices.ClassInterfaceAttribute>|Contrôle le type d’interface généré pour une classe.|  
|<xref:System.Runtime.InteropServices.CoClassAttribute>|Identifie le CLSID de la coclasse d’origine importée à partir d’une bibliothèque de types.<br /><br /> Les outils de COM Interop appliquent généralement cet attribut.|  
|<xref:System.Runtime.InteropServices.ComImportAttribute>|Indique qu’une définition d’interface ou de coclasse a été importée à partir d’une bibliothèque de types COM. Le runtime utilise cet indicateur pour savoir comment activer et marshaler le type. Cet attribut interdit au type d’être de nouveau exporté vers une bibliothèque de types.<br /><br /> Les outils de COM Interop appliquent généralement cet attribut.|  
|<xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute>|Indique qu’une méthode doit être appelée quand l’assembly est inscrit en vue de son utilisation à partir de COM, de sorte que le code écrit par l’utilisateur puisse être exécuté au cours du processus d’inscription.|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|Identifie les interfaces qui sont des sources d’événements pour la classe.<br /><br /> Les outils de COM Interop peuvent appliquer cet attribut.|  
|<xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute>|Indique qu’une méthode doit être appelée quand l’inscription de l’assembly dans COM est annulée, de sorte que le code écrit par l’utilisateur puisse s’exécuter au cours du processus.|  
|<xref:System.Runtime.InteropServices.ComVisibleAttribute>|Rend les types invisibles à COM quand l’attribut a la valeur **false**. Cet attribut peut être appliqué à un type individuel ou à l’intégralité de l’assembly pour contrôler la visibilité COM. Par défaut, tous les types publics managés sont visibles ; l’attribut n’est pas nécessaire pour les rendre visibles.|  
|<xref:System.Runtime.InteropServices.DispIdAttribute>|Spécifie l’identificateur de répartition COM (DISPID) d’une méthode ou d’un champ. Cet attribut contient le DISPID de la méthode, du champ ou de la propriété qu’il décrit.<br /><br /> Les outils de COM Interop peuvent appliquer cet attribut.|
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute>|Indique l’interface par défaut pour une classe COM implémentée dans .NET.<br /><br /> Les outils de COM Interop peuvent appliquer cet attribut.|
|<xref:System.Runtime.InteropServices.FieldOffsetAttribute>|Indique la position physique de chaque champ dans une classe en cas d’utilisation avec **StructLayoutAttribute** et d’affectation d’Explicit à **LayoutKind**.|  
|<xref:System.Runtime.InteropServices.GuidAttribute>|Spécifie l’identificateur global unique (GUID) d’une classe, d’une interface ou d’une bibliothèque de types toute entière. La chaîne doit être passée à l’attribut sous la forme d’un argument de constructeur acceptable pour le type **System.Guid**.<br /><br /> Les outils de COM Interop peuvent appliquer cet attribut.|  
|<xref:System.Runtime.InteropServices.IDispatchImplAttribute>|Indique l’implémentation d’interface **IDispatch** utilisée par le common language runtime lors de l’exposition d’interfaces Dual et de dispinterfaces à COM.|  
|<xref:System.Runtime.InteropServices.InAttribute>|Indique que des données doivent être marshalées dans l’appelant. Peut s’utiliser pour attribuer des paramètres.|  
|<xref:System.Runtime.InteropServices.InterfaceTypeAttribute>|Contrôle le mode d’exposition d’une interface managée à des clients COM (Dual, dérivée d’IUnknown ou IDispatch uniquement).<br /><br /> Les outils de COM Interop peuvent appliquer cet attribut.|  
|<xref:System.Runtime.InteropServices.LCIDConversionAttribute>|Indique que la signature d’une méthode non managée attend un paramètre LCID.<br /><br /> Les outils de COM Interop peuvent appliquer cet attribut.|  
|<xref:System.Runtime.InteropServices.MarshalAsAttribute>|Indique le mode de marshaling des données figurant dans des champs ou des paramètres entre du code managé et non managé. L’attribut est toujours facultatif, car chaque type de données possède un comportement de marshaling par défaut.<br /><br /> Les outils de COM Interop peuvent appliquer cet attribut.|  
|<xref:System.Runtime.InteropServices.OptionalAttribute>|Indique qu'un paramètre est facultatif.<br /><br /> Les outils de COM Interop peuvent appliquer cet attribut.|  
|<xref:System.Runtime.InteropServices.OutAttribute>|Indique que les données d’un champ ou d’un paramètre doivent être remarshalées depuis un objet appelé vers son appelant.|  
|<xref:System.Runtime.InteropServices.PreserveSigAttribute>|Supprime la transformation de la signature HRESULT ou retval qui s’effectue normalement au cours des appels d’interopérabilité. Cet attribut affecte le marshaling ainsi que l’exportation des bibliothèques de types.<br /><br /> Les outils de COM Interop peuvent appliquer cet attribut.|  
|<xref:System.Runtime.InteropServices.ProgIdAttribute>|Spécifie le ProgID d’une classe .NET. Peut s’utiliser pour attribuer des classes.|  
|<xref:System.Runtime.InteropServices.StructLayoutAttribute>|Contrôle la disposition physique des champs d’une classe.<br /><br /> Les outils de COM Interop peuvent appliquer cet attribut.|  
  
## <a name="conversion-tool-attributes"></a>Attributs d’outils de conversion  

 Le tableau suivant décrit les attributs que les outils de COM Interop appliquent au cours du processus de conversion. Vous n’appliquez pas ces attributs au moment du design.  
  
|Attribut|Description|  
|---------------|-----------------|  
|<xref:System.Runtime.InteropServices.ComAliasNameAttribute>|Indique l’alias COM pour un type de paramètre ou de champ. Peut s’utiliser pour attribuer des paramètres, champs ou valeurs de retour.|  
|<xref:System.Runtime.InteropServices.ComConversionLossAttribute>|Indique que des informations sur une classe ou une interface ont été perdues lors de leur importation d’une bibliothèque de types vers un assembly.|  
|<xref:System.Runtime.InteropServices.ComEventInterfaceAttribute>|Identifie l’interface source et la classe qui implémente les méthodes de l’interface d’événement.|  
|<xref:System.Runtime.InteropServices.ImportedFromTypeLibAttribute>|Indique que l’assembly a été importé à l’origine à partir d’une bibliothèque de types COM. Cet attribut contient la définition de la bibliothèque de types d’origine.|  
|<xref:System.Runtime.InteropServices.TypeLibFuncAttribute>|Contient les **FUNCFLAGS** qui ont été importés à l’origine pour cette fonction à partir de la bibliothèque de types COM.|  
|<xref:System.Runtime.InteropServices.TypeLibTypeAttribute>|Contient les **TYPEFLAGS** qui ont été importés à l’origine pour ce type à partir de la bibliothèque de types COM.|  
|<xref:System.Runtime.InteropServices.TypeLibVarAttribute>|Contient les **VARFLAGS** qui ont été importés à l’origine pour cette variable à partir de la bibliothèque de types COM.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices>
- [Exposition de composants .NET Framework à COM](../../framework/interop/exposing-dotnet-components-to-com.md)
- [Attributs](../attributes/index.md)
- [Qualification des types .NET pour l’interopérabilité](qualify-net-types-for-interoperation.md)
- [Empaquetage d’un assembly .NET Framework pour COM](../../framework/interop/packaging-an-assembly-for-com.md)
