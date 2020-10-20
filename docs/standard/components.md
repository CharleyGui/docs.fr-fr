---
title: Composants architecturaux de .NET
description: Décrit les composants de l’architecture .NET, tels que les .NET Standard, les implémentations .NET, les runtimes .NET et les outils.
author: cartermp
ms.date: 10/05/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 316063dbcfba5c92b4a9c6a17051e0a7fc178a3a
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224393"
---
# <a name="net-architectural-components"></a>Composants architecturaux de .NET

Une application .NET est développée pour une ou plusieurs *implémentations de .NET* et s’exécute dans ces dernières. Les implémentations de .NET incluent le .NET Framework, .NET 5 (et .NET Core) et mono. Il existe une spécification d’API commune à plusieurs implémentations de .NET, appelée .NET Standard. Cet article présente brièvement chacun de ces concepts.

## <a name="net-standard"></a>.NET Standard

.NET Standard est un ensemble d’API qui sont implémentées par la bibliothèque de classes de base d’une implémentation .NET. Plus formellement, il s’agit d’une spécification d’API .NET qui constituent un ensemble cohérent de contrats par rapport auxquels vous compilez votre code. Ces contrats sont implémentés dans plusieurs implémentations de .NET.

.NET Standard est une version [cible de .NET Framework](glossary.md#target-framework). Si votre code cible une version de .NET Standard, il peut s’exécuter sur n’importe quelle implémentation .NET qui prend en charge cette version de .NET Standard.

.NET Standard a été créé pour permettre la portabilité entre différentes implémentations de .NET, mais désormais .NET 5 offre une meilleure façon de partager du code entre plusieurs plateformes et charges de travail. Pour plus d’informations, consultez [.net 5 et .NET standard](net-standard.md#net-5-and-net-standard).

## <a name="net-implementations"></a>Implémentations de .NET

Chaque implémentation de .NET inclut les composants suivants :

- Un ou plusieurs runtimes. Exemples : .NET Framework CLR, CLR .NET 5.
- Bibliothèque de classes. Exemples : .NET Framework bibliothèque de classes de base, bibliothèque de classes de base .NET 5.
- Le cas échéant, un ou plusieurs frameworks d’application. Exemples : [ASP.net](https://www.asp.net/), [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview)et [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) sont inclus dans le .NET Framework et le .net 5.
- Le cas échéant, des outils de développement. Certains outils de développement sont partagés entre plusieurs implémentations.

Microsoft prend en charge quatre implémentations .NET :

- .NET 5 (et .NET Core) et versions ultérieures
- .NET Framework
- Mono
- UWP

.NET 5 est maintenant l’implémentation principale, qui est l’objectif du développement en cours. .NET 5 repose sur une seule base de code qui prend en charge plusieurs plateformes et de nombreuses charges de travail, telles que les applications de bureau Windows et les applications de console multiplateforme, les services Cloud et les sites Web.

### <a name="net-5"></a>.NET 5

.NET 5 est une implémentation multiplateforme de .NET conçue pour gérer les charges de travail serveur et Cloud à grande échelle. Il prend également en charge d’autres charges de travail, y compris les applications de bureau. Il s’exécute sur Windows, macOS et Linux. Il implémente .NET Standard, de sorte que le code qui cible .NET Standard peut s’exécuter sur .NET 5. [ASP.net Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview)et [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) s’exécutent tous sur .net 5.

Pour plus d’informations, consultez les ressources suivantes :

- [Présentation de .NET](../core/introduction.md)
- [Choix entre .NET 5 et .NET Framework pour les applications serveur](choosing-core-framework-server.md)
- [.NET 5 et .NET Standard](net-standard.md#net-5-and-net-standard)

### <a name="net-framework"></a>.NET Framework

.NET Framework est l’implémentation .NET originale qui existait depuis 2002. Les versions 4,5 et ultérieures implémentent .NET Standard, de sorte que le code qui cible .NET Standard peut s’exécuter sur ces versions de .NET Framework. Il contient des API supplémentaires spécifiques à Windows, notamment des API pour le développement bureautique Windows avec Windows Forms et WPF. .NET Framework est optimisé pour la génération d’applications de bureau Windows.

Pour plus d’informations, consultez le [guide .NET Framework](../framework/index.yml).

### <a name="mono"></a>Mono

Mono est une implémentation de .NET qui est principalement utilisée quand un runtime réduit est requis. C’est le runtime qui alimente les applications Xamarin sur Android, macOS, iOS, tvOS et Watchos, et se concentre principalement sur un faible encombrement. Mono alimente également les jeux créés à l’aide du moteur Unity.

Il prend en charge toutes les versions de .NET Standard publiées.

Historiquement, Mono implémentait l’API plus volumineuse de .NET Framework et émulait certaines des fonctionnalités les plus populaires sur Unix. Il est parfois utilisé pour exécuter des applications .NET qui s’appuient sur ces fonctionnalités sous Unix.

Mono est généralement utilisé avec un compilateur juste-à-temps, mais il comporte également un compilateur statique complet (compilation Ahead Of Time) qui est utilisé sur des plateformes comme iOS.

Pour plus d’informations, consultez la [documentation mono](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Plateforme Windows universelle (UWP)

UWP est une implémentation de .NET qui sert à générer des logiciels et des applications Windows tactiles modernes pour l’Internet des objets (IoT). Il est conçu pour unifier les différents types d’appareils que vous pouvez cibler, y compris les PC, les tablettes, les téléphones et même la Xbox. UWP fournit de nombreux services, comme un magasin d’applications centralisé, un environnement d’exécution (AppContainer) et un ensemble d’API Windows à utiliser à la place de Win32 (WinRT). Les applications peuvent être écrites en C++, C#, Visual Basic et JavaScript.

Pour plus d’informations, consultez [Présentation du plateforme Windows universelle](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>Runtimes .NET

Un runtime est l’environnement d’exécution d’un programme managé. Le système d’exploitation fait partie de l’environnement d’exécution, mais pas du runtime .NET. Voici quelques exemples de runtimes .NET :

- CLR (Common Language Runtime) pour .NET Framework
- CLR (Common Language Runtime) pour .NET 5
- .NET Native pour la plateforme Windows universelle
- Le runtime Mono pour Xamarin.iOS, Xamarin.Android, Xamarin.Mac et le framework de bureau Mono

## <a name="net-tooling-and-common-infrastructure"></a>Outils .NET et infrastructure commune

Vous avez accès à un ensemble complet d’outils et de composants d’infrastructure qui fonctionnent avec toutes les implémentations de .NET. Ces outils et composants sont les suivants :

- Les langages .NET et leurs compilateurs
- Le système de projet .NET (basé sur les fichiers *.csproj*, *.vbproj* et *.fsproj*)
- [MSBuild](/visualstudio/msbuild/msbuild), moteur de génération utilisé pour générer des projets
- [NuGet](/nuget/), gestionnaire de package de Microsoft pour .net
- Outils d’orchestration de génération open source, tels que [CAKE](https://cakebuild.net/) et [FAKE](https://fake.build/)

Pour plus d’informations, consultez [Outils et productivité](../core/introduction.md#tools-and-productivity).

## <a name="applicable-standards"></a>Normes applicables

Les spécifications du langage C# et de la Common Language Infrastructure (CLI) sont standardisées par le biais de [ECMA International &reg; ](https://www.ecma-international.org/). Les premières éditions de ces normes ont été publiées par l’ECMA en décembre 2001.

Les révisions ultérieures des normes ont été développées par les groupes de tâches TC49-TG2 (C#) et TC49-TG3 (CLI) au sein du Comité technique des langages de programmation ([TC49](https://www.ecma-international.org/memento/tc49.htm)) et adoptés par l’assembly général de l’ECMA et par la suite ISO/IEC JTC 1 via le processus ISO Fast-Track.

### <a name="latest-standards"></a>Dernières normes

Les documents ECMA officiels suivants sont disponibles pour [C#](http://www.ecma-international.org/publications/standards/Ecma-334.htm) et l' [interface CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) ([TR-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)) :

- **La norme du langage C# (version 5,0)**: [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)
- **Common Language Infrastructure**: disponible au format [PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf) et [zip](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip) .
- **Informations dérivées du fichier XML de partition IV**: disponibles au format [PDF](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) et [zip](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip) .

Les documents ISO/CEI officiels sont disponibles à partir de la page normes ISO/CEI [disponibles publiquement](https://standards.iso.org/ittf/PubliclyAvailableStandards/) . Ces liens sont directement à partir de cette page :

- **Technologies de l’information-Langages de programmation-C#**: [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **Technologies de l’information : partitions d’Common Language Infrastructure (CLI) I à VI**: [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **Technologies de l’information — Common Language Infrastructure (CLI) — rapport technique sur les informations dérivées du fichier XML de partition IV**: [ISO/IEC TR 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)

## <a name="see-also"></a>Voir aussi

- [Présentation de .NET](../core/introduction.md)
- [Présentation de .NET Standard](net-standard.md)
- [Choix entre .NET 5 et .NET Framework pour les applications serveur](choosing-core-framework-server.md)
- [.NET Framework Guide](../framework/index.yml)
- [C# Guide](../csharp/index.yml)
- [F# Guide](../fsharp/index.yml)
- [Visual Basic Guide](../visual-basic/index.yml)
