---
title: 'Comment : inspecter le contenu d’un assembly à l’aide de MetadataLoadContext'
description: Découvrez comment utiliser MetadataLoadContext, une API qui vous permet de charger des assemblys .NET à des fins d’inspection.
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.openlocfilehash: 7205230986aa852813a651d2fcb7c5ef88ab18fe
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94831349"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>Comment : inspecter le contenu d’un assembly à l’aide de MetadataLoadContext

L’API de réflexion dans .NET par défaut permet aux développeurs d’inspecter le contenu des assemblys chargés dans le contexte d’exécution principal. Toutefois, il est parfois impossible de charger un assembly dans le contexte d’exécution, par exemple parce qu’il a été compilé pour une autre architecture de plateforme ou de processeur, ou s’il s’agit d’un [assembly de référence](reference-assemblies.md). L' <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName> API vous permet de charger et d’inspecter de tels assemblys. Les assemblys chargés dans le <xref:System.Reflection.MetadataLoadContext> sont traités uniquement comme des métadonnées, autrement dit, vous pouvez examiner les types dans l’assembly, mais vous ne pouvez pas exécuter le code qu’il contient. Contrairement au contexte d’exécution principal, le <xref:System.Reflection.MetadataLoadContext> ne charge pas automatiquement les dépendances à partir du répertoire actif ; à la place, il utilise la logique de liaison personnalisée fournie par le <xref:System.Reflection.MetadataAssemblyResolver> passé.

## <a name="prerequisites"></a>Prérequis

Pour utiliser <xref:System.Reflection.MetadataLoadContext> , installez le package NuGet [System. Reflection. MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) . Il est pris en charge sur n’importe quel Framework cible conforme à la norme de .NET Standard 2,0, par exemple, .NET Core 2,0 ou .NET Framework 4.6.1.

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>Créer MetadataAssemblyResolver pour MetadataLoadContext

La création du <xref:System.Reflection.MetadataLoadContext> requiert la fourniture de l’instance du <xref:System.Reflection.MetadataAssemblyResolver> . La façon la plus simple d’en fournir une consiste à utiliser <xref:System.Reflection.PathAssemblyResolver> , qui résout les assemblys à partir de la collection donnée de chaînes de chemin d’accès d’assembly. Cette collection, outre les assemblys que vous souhaitez inspecter directement, doit également inclure toutes les dépendances nécessaires. Par exemple, pour lire l’attribut personnalisé situé dans un assembly externe, vous devez inclure cet assembly, sans quoi une exception sera levée. Dans la plupart des cas, vous devez inclure au moins l' *assembly principal*, autrement dit, l’assembly contenant les types de système intégrés, tels que <xref:System.Object?displayProperty=nameWithType> . Le code suivant montre comment créer à l' <xref:System.Reflection.PathAssemblyResolver> aide de la collection constituée de l’assembly inspecté et de l’assembly principal du runtime actuel :

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

Si vous avez besoin d’accéder à tous les types BCL, vous pouvez inclure tous les assemblys de Runtime dans la collection. Le code suivant montre comment créer à l' <xref:System.Reflection.PathAssemblyResolver> aide de la collection constituée de l’assembly inspecté et de tous les assemblys du runtime actuel :

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>Créer MetadataLoadContext

Pour créer le <xref:System.Reflection.MetadataLoadContext> , appelez son constructeur <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29> , en passant le précédemment créé <xref:System.Reflection.MetadataAssemblyResolver> comme premier paramètre et le nom de l’assembly principal comme deuxième paramètre. Vous pouvez omettre le nom de l’assembly principal, auquel cas le constructeur tente d’utiliser les noms par défaut : « mscorlib », « System. Runtime » ou « netstandard ».

Une fois que vous avez créé le contexte, vous pouvez charger des assemblys dans celui-ci à l’aide de méthodes telles que <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A> . Vous pouvez utiliser toutes les API de réflexion sur les assemblys chargés, à l’exception de ceux qui impliquent l’exécution du code. La <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A> méthode implique l’exécution de constructeurs. par conséquent, utilisez <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> plutôt la méthode lorsque vous devez examiner des attributs personnalisés dans le <xref:System.Reflection.MetadataLoadContext> .

L’exemple de code suivant crée <xref:System.Reflection.MetadataLoadContext> , charge l’assembly dans celui-ci et génère des attributs d’assembly dans la console :

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>Exemple

Pour obtenir un exemple de code complet, consultez l' [exemple inspecter le contenu de l’assembly à l’aide de MetadataLoadContext](/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/).
