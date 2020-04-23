---
title: Empaquetage d’un assembly .NET Framework pour COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
ms.openlocfilehash: 6866da283cc7cdd180aada252007d67bd72cd862
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124093"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a>Empaquetage d’un assembly .NET Framework pour COM

Les développeurs COM peuvent tirer parti des informations suivantes sur les types managés qu’ils prévoient d’incorporer dans leur application :

- Une liste des types que les applications COM peuvent consommer

  Certains types managés ne sont pas visibles par COM, certains sont visibles mais ne peuvent pas être créés, et certains sont visibles et peuvent être créés. Un assembly peut comprendre tout combinaison de types invisibles, visibles, ne pouvant pas être créés et pouvant être créés. Par souci d’exhaustivité, identifiez les types dans un assembly que vous prévoyez d’exposer à COM, en particulier quand ces types sont un sous-ensemble des types exposés au .NET Framework.

  Pour plus d’informations, consultez [Qualification des types .NET en vue d’une interopérabilité](../../standard/native-interop/qualify-net-types-for-interoperation.md).

- Instructions de gestion de version

  Les classes managées qui implémentent l’interface de classe (une interface COM générée par interop) sont soumises aux restrictions de gestion de version.

  Pour obtenir des instructions sur l’utilisation de l’interface de classe, consultez [Présentation de l’interface de classe](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).

- Instructions de déploiement

  Les assemblys avec nom fort signés par un serveur de publication peuvent être installés dans le global assembly cache. Les assemblys non signés doivent être installés sur la machine de l’utilisateur en tant qu’assemblys privés.

  Pour plus d’informations, consultez [Aspects de la sécurité des assemblys](../../standard/assembly/security-considerations.md).

- Inclusion de bibliothèque de types

  La plupart des types nécessitent une bibliothèque de types en cas de consommation par une application COM. Vous pouvez générer une bibliothèque de types ou demander aux développeurs COM d’effectuer cette tâche. Le SDK Windows fournit les options suivantes pour générer une bibliothèque de types :

  - [Exportateur de bibliothèques de types](#cpconpackagingassemblyforcomanchor1)

  - [Classe TypeLibConverter](#cpconpackagingassemblyforcomanchor2)

  - [Outil Assembly Registration Tool](#cpconpackagingassemblyforcomanchor3)

  - [Outil .NET Services Installation](#cpconpackagingassemblyforcomanchor4)

  Quel que soit le mécanisme que vous choisissez, seuls les types publics définis dans l’assembly que vous fournissez sont inclus dans la bibliothèque de types générée.

Pour obtenir des instructions, consultez [Guide pratique pour incorporer des bibliothèques de types comme des ressources Win32 dans les applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a>Exportateur de bibliothèques de types

L’outil en ligne de commande [Exporter.exe (exportateur de bibliothèques de types)](../tools/tlbexp-exe-type-library-exporter.md) permet de convertir les classes et les interfaces contenues dans un assembly en une bibliothèque de types COM. Une fois les informations de type de la classe disponibles, les clients COM peuvent créer une instance de la classe .NET et appeler les méthodes de l’instance comme s’il s’agissait d’un objet COM. Tlbexp.exe convertit un assembly entier à la fois. Vous ne pouvez pas utiliser Tlbexp.exe pour générer des informations sur les types pour un sous-ensemble de types définis dans un assembly.

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a>Classe TypeLibConverter

La classe <xref:System.Runtime.InteropServices.TypeLibConverter>, qui se trouve dans l’espace de noms **System.Runtime.Interop**, convertit les classes et interfaces contenues dans un assembly en une bibliothèque de types COM. Cette API produit les mêmes informations de type que l’outil Type Library Exporter décrit dans la section précédente.

La **classe TypeLibConverter** implémente le <xref:System.Runtime.InteropServices.ITypeLibConverter>.

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a>Outil Assembly Registration Tool

L’[outil Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) peut générer et inscrire une bibliothèque de types quand vous appliquez l’option **/tlb:**. Les clients COM exigent que les bibliothèques de types soient installées dans le Registre de Windows. Sans cette option, Regasm.exe inscrit uniquement les types dans un assembly, pas la bibliothèque de types. Inscrire les types dans un assembly et inscrire la bibliothèque de types sont deux activités distinctes.

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a>Outil .NET Services Installation

L’[Outil .NET Services Installation (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) ajoute des classes managées aux Services de composants Windows 2000 et combine plusieurs tâches dans un seul outil. En plus de charger et d’inscrire un assembly, Regsvcs.exe peut générer, inscrire et installer la bibliothèque de types dans une application COM+ 1.0 existante.

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [Exposition de composants .NET Framework à COM](exposing-dotnet-components-to-com.md)
- [Qualification des types .NET pour l’interopérabilité](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [Présentation de l'interface de classe](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [Considérations sur la sécurité des assemblys](../../standard/assembly/security-considerations.md)
- [Tlbexp. exe (exportateur de bibliothèques de types)](../tools/tlbexp-exe-type-library-exporter.md)
- [Inscription d’assemblys dans COM](registering-assemblies-with-com.md)
- [Guide pratique pour incorporer des bibliothèques de types comme des ressources Win32 dans les applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))
