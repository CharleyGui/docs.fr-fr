---
title: Qualification des types .NET en vue de l’interopérabilité COM
description: Cet article fournit des instructions pour vous aider à exposer les types d’un assembly .NET aux applications COM pour COM Interop.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
ms.openlocfilehash: 5b122befffbcad39258393462c75ac20431d9136
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420498"
---
# <a name="qualifying-net-types-for-com-interoperation"></a>Qualification des types .NET en vue de l’interopérabilité COM
Si vous envisagez d’exposer les types d’un assembly à des applications COM, prenez en compte les exigences COM Interop au moment de la conception. Les types managés (classe, interface, structure et énumération) s’intègrent parfaitement aux types COM lorsque vous respectez les consignes suivantes :  
  
- Les classes doivent implémenter les interfaces de manière explicite.  
  
     Même si COM Interop fournit un mécanisme permettant de générer automatiquement une interface contenant tous les membres de la classe et de sa classe de base, il est fortement recommandé de fournir des interfaces explicites. L’interface générée automatiquement est appelée « interface de classe ». Pour obtenir des instructions, consultez [Présentation de l’interface de classe](com-callable-wrapper.md#introducing-the-class-interface).  
  
     Vous pouvez utiliser Visual Basic, C# et C++ pour incorporer des définitions d’interface dans votre code, au lieu du langage IDL (ou équivalent). Pour plus d’informations sur la syntaxe, consultez la documentation relative à votre langage.  
  
- Les types managés doivent être publics.  
  
     Seuls les types publics d’un assembly sont inscrits et exportés vers la bibliothèque de types. Par conséquent, seuls les types publics sont visibles par COM.  
  
     Les types managés exposent des fonctionnalités à un autre code managé qui peut ne pas être exposé à COM. Par exemple, les constructeurs paramétrables, les méthodes statiques et les champs constants ne sont pas exposés aux clients COM. De plus, comme le runtime marshale les données d’un type à un autre, les données peuvent être copiées ou transformées.  
  
- Les méthodes, les propriétés, les champs et les événements doivent être publics.  
  
     Les membres des types publics doivent également être publics pour être visibles par COM. Vous pouvez restreindre la visibilité d’un assembly, d’un type public ou de membres publics d’un type public en appliquant <xref:System.Runtime.InteropServices.ComVisibleAttribute>. Par défaut, tous les membres et types publics sont visibles.  
  
- Les types doivent avoir un constructeur sans paramètre public pour être activés dans COM.  
  
     Les types publics managés sont visibles par COM. Toutefois, sans constructeur public sans paramètre (constructeur sans arguments), les clients COM ne peuvent pas créer le type. Les clients COM peuvent toujours utiliser le type s’il est activé par d’autres moyens.  
  
- Les types ne peuvent pas être abstraits.  
  
     Ni les clients COM ni les clients .NET ne peuvent créer de types abstraits.  
  
 Lors de l’exportation vers COM, la hiérarchie d’héritage d’un type managé est aplatie. Le contrôle de version est également différent dans les environnements managés et non managés. Les types exposés à COM n’ont pas les mêmes caractéristiques de contrôle de version que les autres types managés.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [Exposition de composants .NET Framework à COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [Présentation de l'interface de classe](com-callable-wrapper.md#introducing-the-class-interface)
- [Application d’attributs d’interopérabilité](../../../docs/standard/native-interop/apply-interop-attributes.md)
- [Empaquetage d’un assembly .NET Framework pour COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
