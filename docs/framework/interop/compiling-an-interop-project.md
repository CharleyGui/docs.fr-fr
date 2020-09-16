---
title: Compilation d'un projet d'interopérabilité
description: Examinez comment compiler un projet COM Interop, qui est compilé comme des projets managés s’ils font référence à un ou plusieurs assemblys contenant des types COM importés.
ms.date: 03/30/2017
helpviewer_keywords:
- interoperation with unmanaged code, compiling
- COM interop, compiling
- exposing COM components to .NET Framework
- compiling interop projects
- interoperation with unmanaged code, exposing COM components
- COM interop, exposing COM components
ms.assetid: 6fcf6588-5e25-41af-b4ae-780974f2c3df
ms.openlocfilehash: 1cf5bdbedd53227e812b0d2ed97778ab34a81444
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557095"
---
# <a name="compiling-an-interop-project"></a>Compilation d'un projet d'interopérabilité

Les projets de COM Interop qui référencent un ou plusieurs assemblys contenant des types COM importés sont compilés comme tout autre projet managé. Vous pouvez référencer des assemblys d’interopérabilité dans un environnement de développement tel que Visual Studio, ou vous pouvez les référencer quand vous utilisez un compilateur de ligne de commande. Dans les deux cas, l’assembly d’interopérabilité doit figurer dans le même répertoire que les autres fichiers projet pour que la compilation réussisse.

 Il existe deux façons de référencer des assemblys d’interopérabilité :

- Types Interop incorporés : à partir de la .NET Framework 4 et de Visual Studio 2010, vous pouvez indiquer au compilateur d’incorporer les informations de type d’un assembly d’interopérabilité dans votre fichier exécutable. Il s’agit de la technique recommandée.

- En déployant des assemblys d’interopérabilité : vous pouvez créer une référence standard à un assembly d’interopérabilité. Dans ce cas, l’assembly d’interopérabilité doit être déployé avec votre application.

 Les différences entre ces deux techniques sont abordées de manière plus détaillée dans [Utilisation de types COM dans du code managé](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100)).

 L’incorporation de types Interop à l’aide de Visual Studio est illustrée dans [procédure pas à pas : incorporation de types provenant d’assemblys managés dans Visual Studio](../../standard/assembly/embed-types-visual-studio.md).

 Pour référencer un assembly d’interopérabilité à l’aide d’un compilateur de ligne de commande et incorporer des informations de type dans vos fichiers exécutables, utilisez les commutateurs [-Link (options du compilateur C#)](../../csharp/language-reference/compiler-options/link-compiler-option.md) ou [-Link (Visual Basic)](../../visual-basic/reference/command-line-compiler/link.md) et spécifiez le nom de l’assembly d’interopérabilité.

> [!NOTE]
> Les applications Visual C++ ne peuvent pas incorporer d’informations de type, mais elles peuvent interagir avec des applications ou des compléments qui le font.

 Pour compiler une application qui inclut un assembly PIA quand elle est déployée, utilisez le commutateur de compilateur **/reference** et spécifiez le nom de l’assembly d’interopérabilité.

## <a name="see-also"></a>Voir aussi

- [Exposition de composants COM au .NET Framework](exposing-com-components.md)
- [Indépendance du langage et composants indépendants du langage](../../standard/language-independence-and-language-independent-components.md)
- [Utiliser des types COM dans du code managé](/previous-versions/dotnet/netframework-4.0/3y76b69k(v=vs.100))
- [Procédure pas à pas : incorporation de types provenant d’assemblys managés dans Visual Studio](../../standard/assembly/embed-types-visual-studio.md)
- [Importation d'une bibliothèque de types sous la forme d'un assembly](importing-a-type-library-as-an-assembly.md)
