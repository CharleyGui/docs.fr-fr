---
title: 'Comment : Inspecter le contenu de l’assemblage à l’aide de MetadataLoadContext'
description: Apprenez à utiliser MetadataLoadContext, qui est une API qui vous permet de charger des assemblages .NET à des fins d’inspection.
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: a782b2db4fb62cfaedaa6768e2131bda6bec864c
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80229300"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>Comment : Inspecter le contenu de l’assemblage à l’aide de MetadataLoadContext

L’API de réflexion en .NET par défaut permet aux développeurs d’inspecter le contenu des assemblages chargés dans le contexte d’exécution principal. Cependant, parfois, il n’est pas possible de charger un assemblage dans le contexte d’exécution, par exemple, parce qu’il a été compilé pour une autre plate-forme ou architecture de processeur, ou c’est un assemblage de [référence](reference-assemblies.md). L’API <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName> vous permet de charger et d’inspecter ces assemblages. Les assemblages <xref:System.Reflection.MetadataLoadContext> chargés dans le sont traités uniquement comme des métadonnées, c’est-à-dire, vous pouvez examiner les types dans l’assemblage, mais vous ne pouvez pas exécuter n’importe quel code contenu en elle. Contrairement au contexte d’exécution principal, le <xref:System.Reflection.MetadataLoadContext> n’est pas automatiquement charger les dépendances de l’annuaire actuel; au lieu de cela, il <xref:System.Reflection.MetadataAssemblyResolver> utilise la logique de liaison personnalisée fournie par le passé à elle.

## <a name="prerequisites"></a>Prérequis

Pour <xref:System.Reflection.MetadataLoadContext>utiliser, installez le paquet [System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) NuGet. Il est pris en charge sur n’importe quel cadre cible .NET Standard 2.0-conforme, par exemple, .NET Core 2.0 ou .NET Framework 4.6.1.

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>Créer MetadataAssemblyResolver pour MetadataLoadContext

Créer <xref:System.Reflection.MetadataLoadContext> les exigences de <xref:System.Reflection.MetadataAssemblyResolver>fournir l’exemple de la . La façon la plus simple d’en fournir une est d’utiliser le <xref:System.Reflection.PathAssemblyResolver>, qui résout les assemblages de la collection donnée de cordes de chemin d’assemblage. Cette collection, en plus des assemblages que vous souhaitez inspecter directement, devrait également inclure toutes les dépendances nécessaires. Par exemple, pour lire l’attribut personnalisé situé dans un assemblage externe, vous devez inclure que l’assemblage ou une exception sera jeté. Dans la plupart des cas, vous devez inclure au moins *l’assemblage de base,* c’est-à-dire l’assemblage contenant des types de système intégrés, tels que <xref:System.Object?displayProperty=nameWithType>. Le code suivant montre <xref:System.Reflection.PathAssemblyResolver> comment créer l’utilisation de la collection composée de l’assemblage inspecté et de l’assemblage de base du temps d’exécution actuel :

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

Si vous avez besoin d’accéder à tous les types BCL, vous pouvez inclure tous les assemblages de temps d’exécution dans la collection. Le code suivant montre <xref:System.Reflection.PathAssemblyResolver> comment créer l’utilisation de la collection composée de l’assemblage inspecté et de tous les assemblages du temps d’exécution actuel :

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>Créer Des métadonnéesLoadContexte

Pour créer <xref:System.Reflection.MetadataLoadContext>le , <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>invoquer son <xref:System.Reflection.MetadataAssemblyResolver> constructeur , en passant le paramètre précédemment créé comme le premier paramètre et le nom d’assemblage de base comme le deuxième paramètre. Vous pouvez omettre le nom d’assemblage de base, auquel cas le constructeur tentera d’utiliser des noms par défaut : "mscorlib", "System.Runtime", ou "netstandard".

Une fois que vous avez créé le contexte, vous <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>pouvez charger des assemblages en elle en utilisant des méthodes telles que . Vous pouvez utiliser toutes les API de réflexion sur les assemblages chargés, sauf ceux qui impliquent l’exécution du code. La <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A> méthode implique l’exécution des constructeurs, alors utilisez la méthode à la <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> place lorsque vous avez besoin d’examiner les attributs personnalisés dans le <xref:System.Reflection.MetadataLoadContext>.

L’échantillon de <xref:System.Reflection.MetadataLoadContext>code suivant crée, charge l’assemblage en elle, et les attributs d’assemblage de sorties dans la console:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>Exemple

Pour un exemple complet de code, voir [inspecter le contenu de l’assemblage à l’aide de MetadataLoadContext](https://docs.microsoft.com/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/).
