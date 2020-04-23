---
title: Importation d'une bibliothèque de types sous la forme d'un assembly
ms.date: 03/30/2017
helpviewer_keywords:
- importing type library
- type metadata
- custom wrappers
- metadata
- exposing COM components to .NET Framework
- Type Library Importer
- interoperation with unmanaged code, importing type library
- interoperation with unmanaged code, exposing COM components
- type libraries
- TypeLibConverter class, importing type library as assembly
- COM interop, importing type library
- COM interop, exposing COM components
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
ms.openlocfilehash: e1a21175bcabc72b86a328d4f73ecec37140c304
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107598"
---
# <a name="importing-a-type-library-as-an-assembly"></a>Importation d'une bibliothèque de types sous la forme d'un assembly

Les définitions des types COM résident généralement dans une bibliothèque de types. Les compilateurs conformes CLS produisent quant à eux les métadonnées des types dans un assembly. Ces deux sources d’informations sur les types sont assez différentes. Cette rubrique décrit des techniques permettant de générer des métadonnées à partir d’une bibliothèque de types. L’assembly résultant est appelé assembly d’interopérabilité, et les informations de type qu’il contient permettent aux applications .NET Framework d’utiliser des types COM.

Il existe deux façons de mettre ces informations de type à la disposition de votre application :

- À l’aide des assemblys d’interopérabilité au moment du design : à partir du .NET Framework 4, vous pouvez indiquer au compilateur d’incorporer les informations de type de l’assembly d’interopérabilité dans votre fichier exécutable. Le compilateur incorpore uniquement les informations de type que votre application utilise. Vous n’avez pas à déployer l’assembly d’interopérabilité avec votre application. Il s’agit de la technique recommandée.

- En déployant des assemblys d’interopérabilité : vous pouvez créer une référence standard à l’assembly d’interopérabilité. Dans ce cas, l’assembly d’interopérabilité doit être déployé avec votre application. Si vous utilisez cette technique et que vous n’utilisez pas un composant COM privé, référencez toujours l’assembly PIA (Primary Interop Assembly) publié par l’auteur du composant COM que vous prévoyez d’incorporer dans votre code managé. Pour plus d’informations sur la production et l’utilisation d’assemblys PIA (Primary Interop Assembly), consultez [Assemblys PIA (Primary Interop Assembly)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/aax7sdch(v=vs.100)).

Quand vous utilisez des assemblys d’interopérabilité au moment du design, vous pouvez incorporer les informations de type de l’assembly PIA publié par l’auteur du composant COM. Toutefois, vous n’avez pas à déployer l’assembly PIA avec votre application.

L’utilisation d’assemblys d’interopérabilité au moment du design réduit la taille de votre application, car la plupart des applications n’utilisent pas toutes les fonctionnalités d’un composant COM. Le compilateur est très efficace quand il incorpore les informations de type ; si votre application utilise uniquement certaines des méthodes sur une interface COM, le compilateur n’incorpore pas les méthodes inutilisées. Lorsqu’une application qui a incorporé les informations de type interagit avec une autre application du même type, ou interagit avec une application qui utilise un assembly PIA, le common language runtime utilise des règles d’équivalence du type pour déterminer si deux types avec le même nom représentent le même type COM. Vous n’avez pas à connaître ces règles pour utiliser des objets COM. Toutefois, si vous vous intéressez aux règles, consultez [Équivalence de type et types interop incorporés](type-equivalence-and-embedded-interop-types.md).

## <a name="generating-metadata"></a>Génération de métadonnées

Les bibliothèques de types COM peuvent être des fichiers autonomes qui ont une extension .tlb, comme Loanlib.tlb. Certaines bibliothèques de types sont incorporées dans la section de ressources d’un fichier .dll ou .exe. D’autres sources d’informations de bibliothèques de types sont les fichiers .olb et .ocx.

Une fois que vous avez trouvé la bibliothèque de types qui contient l’implémentation de votre type COM cible, vous disposez des options suivantes pour générer un assembly d’interopérabilité contenant des métadonnées de type :

- Visual Studio

  Visual Studio convertit automatiquement des types COM dans une bibliothèque de types en métadonnées dans un assembly. Pour obtenir des instructions, consultez [Comment : ajouter des références aux bibliothèques de types](how-to-add-references-to-type-libraries.md).

- [Importateur de bibliothèques de types (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md)

  Cet importateur fournit des options de ligne de commande pour ajuster les métadonnées dans le fichier d’interopérabilité résultant, importe des types d’une bibliothèque de types existante et génère un assembly d’interopérabilité et un espace de noms. Pour obtenir des instructions, consultez [Guide pratique pour générer des assemblys d’interopérabilité à partir de bibliothèques de types](how-to-generate-interop-assemblies-from-type-libraries.md).

- Classe <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=nameWithType>

  Cette classe fournit des méthodes pour convertir des coclasses et des interfaces dans une bibliothèque de types en métadonnées dans un assembly. Elle produit la même sortie de métadonnées que Tlbimp.exe. Toutefois, la classe <xref:System.Runtime.InteropServices.TypeLibConverter> peut convertir une bibliothèque de types en mémoire en métadonnées contrairement à Tlbimp.exe.

- Wrappers personnalisés

  Quand une bibliothèque de types est indisponible ou incorrecte, vous pouvez opter pour la création d’une définition dupliquée de la classe ou de l’interface dans du code source managé. Vous pouvez ensuite compiler le code source avec un compilateur qui cible le runtime pour produire des métadonnées dans un assembly.

  Pour définir manuellement des types COM, vous devez avoir accès aux éléments suivants :

  - des descriptions précises des coclasses et des interfaces qui sont définies ;

  - un compilateur, tel que le compilateur C#, pouvant générer les définitions des classes .NET Framework appropriées ;

  - une connaissance des règles de conversion de bibliothèque de types en assembly.

  L’écriture d’un wrapper personnalisé est une technique avancée. Pour obtenir des informations supplémentaires sur la manière de générer un wrapper personnalisé, consultez [Personnalisation de wrappers standard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100)).

 Pour plus d’informations sur le processus d’importation COM Interop, consultez [Résumé de la conversion d’une bibliothèque de types en assembly](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100)).

## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- [Exposition de composants COM au .NET Framework](exposing-com-components.md)
- [Récapitulatif de la conversion d’une bibliothèque de types en assembly](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Tlbimp. exe (importateur de bibliothèques de types)](../tools/tlbimp-exe-type-library-importer.md)
- [Personnaliser des wrappers standard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h7hx9abd(v=vs.100))
- [Utiliser des types COM dans du code managé](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Compilation d'un projet d'interopérabilité](compiling-an-interop-project.md)
- [Déploiement d'une application d'interopérabilité](deploying-an-interop-application.md)
- [Comment : ajouter des références aux bibliothèques de types](how-to-add-references-to-type-libraries.md)
- [Comment : générer des assemblys d'interopérabilité à partir de bibliothèques de types](how-to-generate-interop-assemblies-from-type-libraries.md)
