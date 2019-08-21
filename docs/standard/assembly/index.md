---
title: Assemblys dans .NET
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
ms.openlocfilehash: 09dc44141a4eea7601df3f918e8740efdb99aeda
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666588"
---
# <a name="assemblies-in-net"></a>Assemblys dans .NET

Les assemblys constituent l’unité fondamentale dans le déploiement, la gestion de version, la portée d’activation et les autorisations de sécurité d’une application .NET. Les assemblys prennent la forme d’un fichier exécutable (.exe) ou d’un fichier de bibliothèque de liens dynamiques (.dll) et sont les blocs de construction des applications .NET. Ils fournissent au Common Language Runtime les informations dont il a besoin pour connaître les implémentations de type. Vous pouvez comparer un assembly à une collection de types et de ressources conçus pour opérer ensemble et former une unité logique de fonctionnalité.

Dans .NET Core et .NET Framework, un assembly peut être créé à partir d’un ou plusieurs fichiers de code source. Dans .NET Framework, les assemblys peuvent contenir un ou plusieurs modules. Ainsi, les projets plus importants peuvent être planifiés de sorte que plusieurs développeurs individuels travaillent sur des modules ou fichiers de code source distincts, qui sont regroupés pour créer un assembly unique. Pour plus d’informations sur les modules, consultez [Guide pratique pour générer un assembly multifichier](../../framework/app-domains/how-to-build-a-multifile-assembly.md).

Les assemblys ont les propriétés suivantes :

- Les assemblys sont implémentés en tant que fichiers .exe ou .dll.

- Pour les bibliothèques qui ciblent le .NET Framework, vous pouvez partager un assembly entre des applications en le plaçant dans le [Global Assembly Cache](../../framework/app-domains/gac.md). Les assemblys doivent avoir un nom fort avant d’être inclus dans le GAC. Pour plus d’informations, consultez [Assemblys avec nom fort](../../framework/app-domains/strong-named-assemblies.md).

- Les assemblys sont chargés en mémoire uniquement s’ils sont requis. S’ils ne sont pas utilisés, ils ne sont pas chargés. Cela signifie que les assemblys peuvent être un moyen efficace pour gérer les ressources dans les grands projets.

- Vous pouvez obtenir par programme des informations sur un assembly à l’aide de la réflexion. Pour plus d’informations, consultez [Réflexion (C#)](../../csharp/programming-guide/concepts/reflection.md) ou [Réflexion (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Vous pouvez charger un assembly uniquement pour l’inspecter en utilisant la classe <xref:System.Reflection.MetadataLoadContext>.

## <a name="assembly-manifest"></a>Manifeste d'assembly

Tous les assemblys contiennent un *manifeste d’assembly*. Semblable à une table des matières, le manifeste d’assembly contient les éléments suivants :

- L’identité de l’assembly (nom et version).

- Une table de fichiers décrivant tous les autres fichiers qui composent l’assembly, par exemple, les autres assemblys que vous avez créés et qui sont utilisés par votre fichier .exe ou .dll, ou même des fichiers bitmap ou Readme.

- Une *liste de référence de l’assembly*, qui est une liste de toutes les dépendances externes, fichiers .dll ou autres, nécessaires à votre application qui ont été créés par quelqu’un d’autre. Les références de l’assembly contiennent des références aux objets globaux et privés. Les objets globaux sont disponibles pour toutes les autres applications. Dans .NET Core, ils sont associés à un runtime .NET Core particulier. Dans .NET Framework, ils se trouvent dans le Global Assembly Cache. L’espace de noms <xref:System.IO?displayProperty=nameWithType> est un exemple d’un assembly dans le Global Assembly Cache. Les objets privés doivent être dans un répertoire au même niveau ou à un niveau inférieur que celui du répertoire dans lequel votre application est installée.

Comme les assemblys contiennent des informations sur le contenu, la gestion de versions et les dépendances, les applications qui les utilisent n’ont pas besoin de dépendre des valeurs du Registre Windows pour fonctionner correctement. Les assemblys réduisent les conflits de fichiers .dll et rendent vos applications plus fiables et plus faciles à déployer. Dans de nombreux cas, vous pouvez installer une application .NET simplement en copiant ses fichiers sur l’ordinateur cible. Pour plus d’informations, consultez [Manifeste d’assembly](../../framework/app-domains/assembly-manifest.md).

## <a name="adding-a-reference-to-an-assembly"></a>Ajout d’une référence à un assembly

Pour utiliser un assembly, vous devez y ajouter une référence. Ensuite, vous pouvez utiliser la [directive using](../../csharp/language-reference/keywords/using-directive.md) pour C# ou [l’instruction Imports](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) pour que Visual Basic choisisse l’espace de noms des éléments que vous souhaitez utiliser. Une fois qu’un assembly est référencé et importé, tous les types, propriétés, méthodes accessibles et les autres membres de ses espaces de noms sont disponibles pour votre application comme si leur code faisait partie de votre fichier source.

> [!NOTE]
> La plupart des assemblys à partir de la bibliothèque de classes .NET sont référencés automatiquement. Dans certains cas, cependant, un assembly système peut ne pas être référencé automatiquement. Dans .NET Core, vous pouvez ajouter une référence au package NuGet qui contient l’assembly à l’aide du Gestionnaire de packages NuGet dans Visual Studio ou en ajoutant un élément [\<PackageReference>](../../core/tools/dependencies.md#the-new-packagereference-element) pour l’assembly au projet *.csproj ou *.vbproj. Dans .NET Framework, vous pouvez ajouter une référence à l’assembly à l’aide de la boîte de dialogue **Ajouter une référence** dans Visual Studio ou à l’aide de l’option de ligne de commande `-reference` pour les compilateurs [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) ou [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md).

En C#, vous pouvez aussi utiliser deux versions du même assembly dans une même application. Pour plus d’informations, consultez [extern alias](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="creating-an-assembly"></a>Création d’un assembly

Compilez votre application en la créant directement dans Visual Studio, en la générant à partir de la ligne de commande à l’aide des outils de l’interface de ligne de commande (CLI) .NET Core, ou en générant des assemblys .NET Framework avec un compilateur de ligne de commande. Pour plus d’informations sur la création d’assemblys à l’aide des outils CLI .NET, consultez [Outils de l’interface de ligne de commande (CLI) .NET Core](../../core/tools/index.md). Pour la création d’assemblys avec les compilateurs de ligne de commande, consultez [Générer avec la ligne de commande avec csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) pour C# et [Génération à partir de la ligne de commande](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) pour Visual Basic.

> [!NOTE]
> Pour générer un assembly dans Visual Studio, dans le menu **Générer**, choisissez **Générer**.

## <a name="see-also"></a>Voir aussi

- [Format de fichier d’assembly .NET](file-format.md)
- [Assemblys dans le Common Language Runtime](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [Assemblys friend](friend-assemblies.md)
- [Guide pratique pour charger et décharger des assemblys (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Guide pratique pour charger et décharger des assemblys (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)
- [Guide pratique pour Utiliser et déboguer Assembly Unloadability dans .NET Core](unloadability-howto.md)
- [Guide pratique pour déterminer si un fichier est un assembly (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
- [Guide pratique pour déterminer si un fichier est un assembly (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)
