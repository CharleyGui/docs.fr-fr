---
title: Assemblys dans .NET
ms.date: 08/15/2019
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
helpviewer_keywords:
- dynamic assemblies
- security [.NET Framework], boundaries
- boundaries of assemblies
- assemblies [.NET Framework], about
- assemblies [.NET Framework], boundaries
- reference scope boundaries
- assemblies [.NET Framework]
- version boundaries
- type boundaries
ms.openlocfilehash: f85fef37ac952c91ac73570f26d80d8a46f4eedf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156503"
---
# <a name="assemblies-in-net"></a>Assemblys dans .NET

Les assemblages forment les unités fondamentales de déploiement, de contrôle de la version, de réutilisation, de portée d’activation et d’autorisations de sécurité pour . Applications basées sur NET. Un assembly est une collection de types et de ressources conçus pour opérer ensemble et former une unité logique de fonctionnalité. Les assemblages prennent la forme de fichiers exécutables (*.exe*) ou de bibliothèque de liaison dynamique (*.dll),* et sont les éléments constitutifs des applications .NET. Ils fournissent au Common Language Runtime les informations dont il a besoin pour connaître les implémentations de type.

Dans .NET Core et .NET Framework, vous pouvez créer un assemblage à partir d’un ou plusieurs fichiers de code source. Dans .NET Framework, les assemblys peuvent contenir un ou plusieurs modules. Cela permet de planifier de plus grands projets afin que plusieurs développeurs puissent travailler sur des fichiers ou modules de code source distincts, qui sont combinés pour créer un seul assemblage. Pour plus d’informations sur les modules, voir [Comment : Construire un assemblage multifils.](../../framework/app-domains/build-multifile-assembly.md)

Les assemblys ont les propriétés suivantes :

- Les assemblages sont implémentés sous forme de fichiers *.exe* ou *.dll.*

- Pour les bibliothèques qui ciblent le cadre .NET, vous pouvez partager des assemblages entre les applications en les plaçant dans le [cache d’assemblage global (GAC)](../../framework/app-domains/gac.md). Vous devez des assemblées de nom fort avant de pouvoir les inclure dans le GAC. Pour plus d’informations, voir [Assemblées nommées par strong](strong-named.md).

- Les assemblys sont chargés en mémoire uniquement s’ils sont requis. S’ils ne sont pas utilisés, ils ne sont pas chargés. Cela signifie que les assemblys peuvent être un moyen efficace pour gérer les ressources dans les grands projets.

- Vous pouvez obtenir par programme des informations sur un assembly à l’aide de la réflexion. Pour plus d’informations, consultez [Réflexion (C#)](../../csharp/programming-guide/concepts/reflection.md) ou [Réflexion (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Vous pouvez charger un assemblage juste <xref:System.Reflection.MetadataLoadContext> pour l’inspecter <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> en <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> utilisant la classe en .NET Core et les méthodes ou dans .NET Core et .NET Framework.

## <a name="assemblies-in-the-common-language-runtime"></a>Assemblées dans le runtime langue commune

Les assemblées fournissent l’heure de l’exécution de la langue commune avec l’information dont il a besoin pour être au courant des implémentations de type. Pour le runtime, un type n'existe pas en dehors du contexte d'un assembly.

Une assemblée définit les informations suivantes :

- Code que le langage courant exécute. Notez que chaque assemblage ne `DllMain`peut `WinMain`avoir `Main`qu’un seul point d’entrée: , , ou .

- Limite de sécurité. Un assembly est l'unité au niveau de laquelle les autorisations sont demandées et octroyées. Pour plus d’informations sur les limites de sécurité dans les assemblées, voir [considérations de sécurité de l’Assemblée](security-considerations.md).

- Limite de type. L'identité de chaque type inclut le nom de l'assembly dans lequel il réside. Un type appelé `MyType` chargé dans l'étendue d'un assembly n'est pas le même qu'un type appelé `MyType` chargé dans l'étendue d'un autre assembly.

- Limite de la portée de référence. Le [manifeste d’assemblage](#assembly-manifest) a des métadonnées qui sont utilisées pour résoudre les types et satisfaire les demandes de ressources. Le manifeste spécifie les types et les ressources à exposer en dehors de l’assemblage, et énumère d’autres assemblages dont il dépend. Le code de langue intermédiaire Microsoft (MSIL) dans un fichier portable exécutable (PE) ne sera pas exécuté à moins qu’il n’ait un [manifeste d’assemblage](#assembly-manifest)associé .

- Limite de version. L’assemblage est la plus petite unité versionnable dans l’heure de course de langue commune. Tous les types et ressources d’une même assemblée sont classés en tant qu’unité. Le [manifeste d’assemblage](#assembly-manifest) décrit les dépendances de la version que vous spécifiez pour les assemblages dépendants. Pour plus d’informations sur la version, voir [La version De l’Assemblée](versioning.md).

- Unité de déploiement. Quand une application démarre, seuls les assemblys qu'elle appelle initialement doivent être présents. D’autres assemblages, tels que des assemblages contenant des ressources de localisation ou des cours d’utilité, peuvent être récupérés sur demande. Cela permet aux applications d’être simples et minces lors de leur première mise en œ air. Pour plus d’informations sur le déploiement des assemblages, voir [les applications Deploy](../../framework/deployment/index.md).

- Unité d’exécution côte à côte. Pour plus d’informations sur l’exécution de plusieurs versions d’une assemblée, voir [Assemblées et exécution côte à côte](side-by-side-execution.md).

## <a name="create-an-assembly"></a>Créer un assemblage

Les assemblys peuvent être statiques ou dynamiques. Les assemblys statiques sont stockés sur le disque dans des fichiers exécutables portables (PE). Les assemblages statiques peuvent inclure des interfaces, des classes et des ressources comme des bitmaps, des fichiers JPEG et d’autres fichiers de ressources. Vous pouvez également créer des assemblages dynamiques, qui sont exécutés directement à partir de la mémoire et ne sont pas enregistrés sur disque avant l’exécution. Vous pouvez enregistrer des assemblys dynamiques sur le disque une fois qu'ils ont été exécutés.

Pour créer des assemblys, différentes possibilités s'offrent à vous. Vous pouvez utiliser des outils de développement, tels que Visual Studio, qui peuvent créer des fichiers *.dll* ou *.exe.* Vous pouvez utiliser des outils dans le SDK Windows pour créer des assemblages avec des modules d’autres environnements de développement. Vous pouvez également utiliser les API du Common Language Runtime, comme <xref:System.Reflection.Emit?displayProperty=nameWithType>, pour créer des assemblys dynamiques.

Compilez les assemblages en les construisant en visual Studio, en les construisant avec des outils d’interface de ligne de commande .NET Core, ou en construisant des assemblages cadres .NET avec un compilateur de ligne de commande. Pour plus d’informations sur les assemblages de bâtiments à l’aide de .NET Core CLI, voir [.NET Core CLI aperçu](../../core/tools/index.md). Pour la construction d’assemblages avec les compilateurs de la ligne de commandement, voir [Command-line build with csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) for C, ou [Build from the command line](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) for Visual Basic.

> [!NOTE]
> Pour construire un assemblage dans Visual Studio, sur le menu **Build,** sélectionnez **Build**.

## <a name="assembly-manifest"></a>Manifeste d'assembly

Chaque assemblée a un dossier *manifeste d’assemblage.* Semblable à un tableau de contenu, le manifeste d’assemblage contient :

- L’identité de l’assembly (nom et version).

- Un tableau de fichiers décrivant tous les autres fichiers qui composent l’assemblage, tels que d’autres assemblées que vous avez créées que votre fichier *.exe* ou *.dll s’appuie* sur, fichiers bitmap, ou fichiers Readme.

- Une liste de *référence d’assemblage*, qui est une liste de toutes les dépendances externes, telles que *.dll*s ou d’autres fichiers. Les références de l’assembly contiennent des références aux objets globaux et privés. Les objets globaux sont disponibles pour toutes les autres applications. Dans .NET Core, les objets globaux sont couplés à un temps d’exécution .NET Core particulier. Dans le cadre .NET, les objets globaux résident dans le cache d’assemblage global (GAC). *System.IO.dll* est un exemple d’assemblée dans le GAC. Les objets privés doivent être au niveau d’annuaire à ou en dessous de l’annuaire dans lequel votre application est installée.

Étant donné que les assemblages contiennent des informations sur le contenu, la version et les dépendances, les applications qui les utilisent ne doivent pas s’appuyer sur des sources externes, telles que le registre sur les systèmes Windows, pour fonctionner correctement. Les assemblages réduisent les conflits *.dll* et rendent vos applications plus fiables et plus faciles à déployer. Dans de nombreux cas, vous pouvez installer une application .NET simplement en copiant ses fichiers sur l’ordinateur cible. Pour plus d’informations, voir [Assemblée manifeste](manifest.md).

## <a name="add-a-reference-to-an-assembly"></a>Ajouter une référence à une assemblée

Pour utiliser un assemblage dans une application, vous devez y ajouter une référence. Une fois qu’une assemblée est référencée, tous les types, propriétés, méthodes et autres membres accessibles de son nom sont à votre disposition comme si leur code faisait partie de votre fichier source.

> [!NOTE]
> La plupart des assemblys à partir de la bibliothèque de classes .NET sont référencés automatiquement. Si un assemblage de système n’est pas automatiquement référencé, pour .NET Core, vous pouvez ajouter une référence au paquet NuGet qui contient l’assemblage. Utilisez le gestionnaire de forfait NuGet dans Visual Studio, ou ajoutez un [ \<élément packageReference>](../../core/tools/dependencies.md#the-packagereference-element) pour l’assemblage au projet *.csproj* ou *.vbproj.* Dans .NET Framework, vous pouvez ajouter une référence à l’assemblage en utilisant `-reference` le dialogue Add **Reference** dans Visual Studio, ou en utilisant l’option de ligne de commande pour les compilateurs de base visuelle [ou](../../csharp/language-reference/compiler-options/reference-compiler-option.md) [C.](../../visual-basic/reference/command-line-compiler/reference.md)

Dans C, vous pouvez utiliser deux versions d’un même assemblage dans une seule application. Pour plus d’informations, consultez [extern alias](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="related-content"></a>Contenu connexe

|Intitulé|Description|
|-----------|-----------------|
|[Contenu d’assembly](contents.md)|Éléments qui composent une assemblée.|
|[Manifeste de l’Assemblée](manifest.md)|Les données dans l’assemblage se manifestent, et comment elles sont stockées dans les assemblages.|
|[Cache d’assemblage global](../../framework/app-domains/gac.md)|Comment le GAC stocke et utilise des assemblages.|
|[Assemblées de bien-être](strong-named.md)|Caractéristiques des assemblages nommés par des personnes fortes.|
|[Aspects de la sécurité des assemblys](security-considerations.md)|Comment la sécurité fonctionne avec les assemblées.|
|[Contrôle de version des assemblys](versioning.md)|Aperçu de la politique de version .NET Framework.|
|[Placement de l’assemblage](../../framework/app-domains/assembly-placement.md)|Où localiser les assemblages.|
|[Assemblys et exécution côte à côte](side-by-side-execution.md)|Utilisez plusieurs versions de l’exécution ou d’un assemblage simultanément.|
|[Envoyer des assemblys et des méthodes dynamiques](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Comment créer des assemblages dynamiques.|
|[Comment le temps d’exécution localise les assemblages](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Comment le cadre .NET résout les références d’assemblage au moment de l’exécution.|

## <a name="reference"></a>Informations de référence

<xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>Voir aussi

- [format de fichier d’assemblage .NET](file-format.md)
- [Assemblys friend](friend.md)
- [Assemblys de référence](reference-assemblies.md)
- [Comment : Charger et décharger les assemblages](load-unload.md)
- [Comment: Utiliser et débouger l’impré chargement de l’assemblage en .NET Core](unloadability.md)
- [Comment : Déterminer si un fichier est un assemblage](identify.md)
