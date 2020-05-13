---
title: Assemblys dans .NET
description: Les assemblys sont des unités de base pour le déploiement, le contrôle de version, la réutilisation, la portée d’activation et les autorisations de sécurité pour. Applications basées sur le réseau.
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
ms.openlocfilehash: 87030bf9770c464709559b2fb8f4c0004009e48d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379910"
---
# <a name="assemblies-in-net"></a>Assemblys dans .NET

Les assemblys constituent les unités fondamentales de déploiement, de contrôle de version, de réutilisation, de portée d’activation et d’autorisations de sécurité pour. Applications basées sur le réseau. Un assembly est une collection de types et de ressources conçus pour opérer ensemble et former une unité logique de fonctionnalité. Les assemblys prennent la forme de fichiers exécutables (*. exe*) ou de bibliothèques de liens dynamiques (*. dll*), et sont les blocs de construction des applications .net. Ils fournissent au Common Language Runtime les informations dont il a besoin pour connaître les implémentations de type.

Dans .NET Core et .NET Framework, vous pouvez créer un assembly à partir d’un ou de plusieurs fichiers de code source. Dans .NET Framework, les assemblys peuvent contenir un ou plusieurs modules. Cela permet de planifier des projets plus volumineux de manière à ce que plusieurs développeurs puissent travailler sur des modules ou des fichiers de code source distincts, qui sont combinés pour créer un assembly unique. Pour plus d’informations sur les modules, consultez [Comment : générer un assembly multifichier](../../framework/app-domains/build-multifile-assembly.md).

Les assemblys ont les propriétés suivantes :

- Les assemblys sont implémentés en tant que fichiers. *exe* ou *. dll* .

- Pour les bibliothèques qui ciblent le .NET Framework, vous pouvez partager des assemblys entre les applications en les plaçant dans le [global assembly cache (GAC)](../../framework/app-domains/gac.md). Vous devez nommer les assemblys avec nom fort avant de pouvoir les inclure dans le GAC. Pour plus d’informations, consultez [assemblys avec nom fort](strong-named.md).

- Les assemblys sont chargés en mémoire uniquement s’ils sont requis. S’ils ne sont pas utilisés, ils ne sont pas chargés. Cela signifie que les assemblys peuvent être un moyen efficace pour gérer les ressources dans les grands projets.

- Vous pouvez obtenir par programme des informations sur un assembly à l’aide de la réflexion. Pour plus d’informations, consultez [Réflexion (C#)](../../csharp/programming-guide/concepts/reflection.md) ou [Réflexion (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).

- Vous pouvez charger un assembly juste pour l’inspecter à l’aide de la <xref:System.Reflection.MetadataLoadContext> classe dans .net Core et des <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType> méthodes ou dans .net Core et .NET Framework.

## <a name="assemblies-in-the-common-language-runtime"></a>Assemblys dans le common language runtime

Les assemblys fournissent le common language runtime avec les informations dont il a besoin pour connaître les implémentations de type. Pour le runtime, un type n'existe pas en dehors du contexte d'un assembly.

Un assembly définit les informations suivantes :

- Code que l’common language runtime exécute. Notez que chaque assembly ne peut avoir qu’un seul point d’entrée : `DllMain` , `WinMain` ou `Main` .

- Limite de sécurité. Un assembly est l'unité au niveau de laquelle les autorisations sont demandées et octroyées. Pour plus d’informations sur les limites de sécurité dans les assemblys, consultez Considérations sur la [sécurité](security-considerations.md)des assemblys.

- Limite de type. L'identité de chaque type inclut le nom de l'assembly dans lequel il réside. Un type appelé `MyType` chargé dans l'étendue d'un assembly n'est pas le même qu'un type appelé `MyType` chargé dans l'étendue d'un autre assembly.

- Limite d’étendue de référence. Le [manifeste d’assembly](#assembly-manifest) a des métadonnées qui sont utilisées pour résoudre les types et satisfaire les demandes de ressources. Le manifeste spécifie les types et les ressources à exposer en dehors de l’assembly, et énumère les autres assemblys dont il dépend. Le code MSIL (Microsoft Intermediate Language) dans un fichier exécutable portable (PE) ne sera pas exécuté à moins qu’il n’ait un [manifeste d’assembly](#assembly-manifest)associé.

- Limite de version. L’assembly est la plus petite unité de versionable dans le common language runtime. Tous les types et toutes les ressources dans le même assembly sont associés à une version en tant qu’unité. Le [manifeste d’assembly](#assembly-manifest) décrit les dépendances de version que vous spécifiez pour tous les assemblys dépendants. Pour plus d’informations sur le contrôle de version, consultez contrôle de [version des assemblys](versioning.md).

- Unité de déploiement. Quand une application démarre, seuls les assemblys qu'elle appelle initialement doivent être présents. D’autres assemblys, tels que les assemblys contenant des ressources de localisation ou des classes utilitaires, peuvent être récupérés à la demande. Cela permet aux applications d’être simples et légères lors de leur premier téléchargement. Pour plus d’informations sur le déploiement d’assemblys, consultez [déployer des applications](../../framework/deployment/index.md).

- Unité d’exécution côte à côte. Pour plus d’informations sur l’exécution de plusieurs versions d’un assembly, consultez [assemblys et exécution côte à côte](side-by-side-execution.md).

## <a name="create-an-assembly"></a>Créer un assembly

Les assemblys peuvent être statiques ou dynamiques. Les assemblys statiques sont stockés sur le disque dans des fichiers exécutables portables (PE). Les assemblys statiques peuvent inclure des interfaces, des classes et des ressources telles que des bitmaps, des fichiers JPEG et d’autres fichiers de ressources. Vous pouvez également créer des assemblys dynamiques, qui sont exécutés directement à partir de la mémoire et ne sont pas enregistrés sur le disque avant l’exécution. Vous pouvez enregistrer des assemblys dynamiques sur le disque une fois qu'ils ont été exécutés.

Pour créer des assemblys, différentes possibilités s'offrent à vous. Vous pouvez utiliser des outils de développement, tels que Visual Studio, qui peuvent créer des fichiers *. dll* ou. *exe* . Vous pouvez utiliser les outils de la SDK Windows pour créer des assemblys avec des modules à partir d’autres environnements de développement. Vous pouvez également utiliser les API du Common Language Runtime, comme <xref:System.Reflection.Emit?displayProperty=nameWithType>, pour créer des assemblys dynamiques.

Compilez les assemblys en les générant dans Visual Studio, en les créant avec des outils d’interface de ligne de commande .NET Core ou en générant des assemblys .NET Framework avec un compilateur de ligne de commande. Pour plus d’informations sur la génération d’assemblys à l’aide de CLI .NET Core, consultez [CLI .net Core vue d’ensemble](../../core/tools/index.md). Pour générer des assemblys avec les compilateurs de ligne de commande, consultez génération à partir de la ligne de commande [avec CSC. exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) pour C#, ou [créez à partir de la ligne de commande](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) pour Visual Basic.

> [!NOTE]
> Pour générer un assembly dans Visual Studio, dans le menu **générer** , sélectionnez **générer**.

## <a name="assembly-manifest"></a>Manifeste d'assembly

Chaque assembly possède un fichier manifeste de l' *assembly* . À l’instar d’une table des matières, le manifeste de l’assembly contient les éléments suivants :

- L’identité de l’assembly (nom et version).

- Une table de fichiers décrivant tous les autres fichiers qui composent l’assembly, tels que les autres assemblys que vous avez créés et sur lesquels votre fichier *. exe* ou *. dll* s’appuie, des fichiers bitmap ou des fichiers Lisez-moi.

- Une *liste de références d’assembly*, qui est une liste de toutes les dépendances externes, telles que les fichiers *. dll*ou autres. Les références de l’assembly contiennent des références aux objets globaux et privés. Les objets globaux sont disponibles pour toutes les autres applications. Dans .NET Core, les objets globaux sont associés à un Runtime .NET Core particulier. Dans .NET Framework, les objets globaux résident dans le Global Assembly Cache (GAC). *System. IO. dll* est un exemple d’assembly dans le GAC. Les objets privés doivent se trouver dans un répertoire au niveau ou au-dessous du répertoire dans lequel votre application est installée.

Étant donné que les assemblys contiennent des informations sur le contenu, le contrôle de version et les dépendances, les applications qui les utilisent ne s’appuient pas sur des sources externes, telles que le registre sur les systèmes Windows, pour fonctionner correctement. Les assemblys réduisent les conflits de *dll* et rendent vos applications plus fiables et plus faciles à déployer. Dans de nombreux cas, vous pouvez installer une application .NET simplement en copiant ses fichiers sur l’ordinateur cible. Pour plus d’informations, consultez manifeste de l' [assembly](manifest.md).

## <a name="add-a-reference-to-an-assembly"></a>Ajouter une référence à un assembly

Pour utiliser un assembly dans une application, vous devez lui ajouter une référence. Une fois qu’un assembly est référencé, tous les types, propriétés, méthodes et autres membres accessibles de ses espaces de noms sont disponibles pour votre application comme si leur code faisaient partie de votre fichier source.

> [!NOTE]
> La plupart des assemblys à partir de la bibliothèque de classes .NET sont référencés automatiquement. Si un assembly système n’est pas automatiquement référencé, pour .NET Core, vous pouvez ajouter une référence au package NuGet qui contient l’assembly. Utilisez le gestionnaire de package NuGet dans Visual Studio ou ajoutez un élément [ \< PackageReference>](../../core/tools/dependencies.md#the-packagereference-element) pour l’assembly au projet *. csproj* ou *. vbproj* . Dans .NET Framework, vous pouvez ajouter une référence à l’assembly à l’aide de la boîte de dialogue **Ajouter une référence** dans Visual Studio, ou à l’aide `-reference` de l’option de ligne de commande pour les compilateurs [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) ou [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md) .

En C#, vous pouvez utiliser deux versions du même assembly dans une même application. Pour plus d’informations, consultez [extern alias](../../csharp/language-reference/keywords/extern-alias.md).

## <a name="related-content"></a>Contenu connexe

|Intitulé|Description|
|-----------|-----------------|
|[Contenu d’assembly](contents.md)|Éléments qui composent un assembly.|
|[Manifeste d’assembly](manifest.md)|Les données dans le manifeste de l’assembly et la manière dont elles sont stockées dans les assemblys.|
|[Global assembly cache](../../framework/app-domains/gac.md)|Comment le GAC stocke et utilise les assemblys.|
|[Assemblys avec nom fort](strong-named.md)|Caractéristiques des assemblys avec nom fort.|
|[Aspects de la sécurité des assemblys](security-considerations.md)|Fonctionnement de la sécurité avec les assemblys.|
|[Contrôle de version des assemblys](versioning.md)|Vue d’ensemble de la stratégie de contrôle de version de .NET Framework.|
|[Emplacement d’assembly](../../framework/app-domains/assembly-placement.md)|Où trouver les assemblys.|
|[Assemblys et exécution côte à côte](side-by-side-execution.md)|Utilisez plusieurs versions du runtime ou d’un assembly simultanément.|
|[Envoyer des assemblys et des méthodes dynamiques](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Comment créer des assemblys dynamiques.|
|[Comment le runtime localise les assemblys](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|Comment le .NET Framework résout les références d’assembly au moment de l’exécution.|

## <a name="reference"></a>Informations de référence

<xref:System.Reflection.Assembly?displayProperty=nameWithType>

## <a name="see-also"></a>Voir aussi

- [Format de fichier d’assembly .NET](file-format.md)
- [Assemblys friend](friend.md)
- [Assemblys de référence](reference-assemblies.md)
- [Comment : charger et décharger des assemblys](load-unload.md)
- [Comment : utiliser et déboguer l’inchargement d’assembly dans .NET Core](unloadability.md)
- [Comment : déterminer si un fichier est un assembly](identify.md)
- [Comment : inspecter le contenu d’un assembly à l’aide de MetadataLoadContext](inspect-contents-using-metadataloadcontext.md)
