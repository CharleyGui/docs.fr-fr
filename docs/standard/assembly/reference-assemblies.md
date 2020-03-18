---
title: Assemblys de référence
description: En savoir plus sur les assemblages de référence, un type spécial d’assemblages en .NET qui ne contiennent que la surface publique de l’API de la bibliothèque
author: MSDN-WhiteKnight
ms.date: 09/12/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 938942caf81c54a8aa9207dbe87559438ffb252e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79141066"
---
# <a name="reference-assemblies"></a>Assemblys de référence

*Les assemblages* de référence sont un type spécial d’assemblage qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface publique de l’API de la bibliothèque. Elles comprennent des déclarations pour tous les membres qui sont importantes lorsqu’ils font référence à une assemblée dans des outils de construction, mais excluent toutes les mises en œuvre et déclarations des membres du groupe privé qui n’ont aucune incidence observable sur leur contrat d’API. En revanche, les assemblées régulières sont appelées *assemblées de mise en œuvre*.

Les assemblages de référence ne peuvent pas être chargés pour exécution, mais ils peuvent être adoptés comme entrée de compilateur de la même manière que les assemblages de mise en œuvre. Les assemblages de référence sont généralement distribués avec le kit de développement logiciel (SDK) d’une plate-forme ou d’une bibliothèque particulière.

L’utilisation d’un assemblage de référence permet aux développeurs de construire des programmes qui ciblent une version de bibliothèque spécifique sans avoir l’assemblage complet de mise en œuvre pour cette version. Supposons que vous n’ayez que la dernière version d’une bibliothèque sur votre machine, mais vous voulez construire un programme qui cible une version antérieure de cette bibliothèque. Si vous compilez directement contre l’assemblée de mise en œuvre, vous pouvez utiliser par inadvertance des membres de l’API qui ne sont pas disponibles dans la version antérieure. Vous ne trouverez cette erreur que lorsque vous testez le programme sur la machine cible. Si vous compilez contre l’assemblage de référence pour la version antérieure, vous obtiendrez immédiatement une erreur de compilation.

Une assemblée de référence peut également représenter un contrat, c’est-à-dire un ensemble d’API qui ne correspondent pas à l’assemblage concret de la mise en œuvre. Ces assemblages de référence, appelés *l’assemblage des contrats,* peuvent être utilisés pour cibler plusieurs plates-formes qui prennent en charge le même ensemble d’API. Par exemple, .NET Standard fournit l’assemblage du contrat, *netstandard.dll*, qui représente l’ensemble des API communes partagées entre les différentes plates-formes .NET. Les implémentations de ces API sont contenues dans différents assemblages sur différentes plates-formes, telles que *mscorlib.dll* sur .NET Framework ou *System.Private.CoreLib.dll* sur .NET Core. Une bibliothèque qui cible .NET Standard peut fonctionner sur toutes les plates-formes qui prennent en charge .NET Standard.

## <a name="using-reference-assemblies"></a>Utilisation d’assemblages de référence

Pour utiliser certaines API de votre projet, vous devez ajouter des références à leurs assemblages. Vous pouvez ajouter des références aux assemblages de mise en œuvre ou aux assemblages de référence. Il est recommandé d’utiliser des assemblages de référence chaque fois qu’ils sont disponibles. Cela garantit que vous utilisez uniquement les membres API pris en charge dans la version cible, destinée à être utilisée par les concepteurs d’API. L’utilisation de l’assemblage de référence garantit que vous ne prenez pas une dépendance aux détails de mise en œuvre.

Les assemblages de référence pour les bibliothèques cadre .NET sont distribués avec des packs de ciblage. Vous pouvez les obtenir en téléchargeant un installateur autonome ou en sélectionnant un composant dans l’installateur Visual Studio. Pour plus d’informations, voir [Installer le cadre .NET pour les développeurs](../../framework/install/guide-for-developers.md). Pour .NET Core et .NET Standard, les assemblages de référence sont automatiquement téléchargés au besoin (via NuGet) et référencés. Pour .NET Core 3.0 et plus, les assemblages de référence pour le cadre de base sont dans le paquet [Microsoft.NETCore.App.Ref](https://www.nuget.org/packages/Microsoft.NETCore.App.Ref) (le paquet [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) est utilisé à la place pour les versions avant 3.0). Pour plus d’informations, voir [Paquets, métapackages et cadres](../../core/packages.md) dans le guide de base .NET.

Lorsque vous ajoutez des références à des assemblages cadres .NET dans Visual Studio à l’aide du dialogue **de référence Add,** vous sélectionnez un assemblage de la liste, et Visual Studio trouve automatiquement des assemblages de référence qui correspondent à la version cadre cible sélectionnée dans votre projet. Il en va de même pour l’ajout de références directement dans le projet MSBuild à l’aide de [l’élément](/visualstudio/msbuild/common-msbuild-project-items#reference) du projet De référence : vous n’avez qu’à spécifier le nom de l’assemblage, et non la trajectoire complète du fichier. Lorsque vous ajoutez des références à ces `-reference` assemblages dans la ligne de commande en utilisant l’option compilateur[(en C](../../csharp/language-reference/compiler-options/reference-compiler-option.md) et dans Visual [Basic](../../visual-basic/reference/command-line-compiler/reference.md)) ou en utilisant la <xref:Microsoft.CodeAnalysis.Compilation.AddReferences%2A?displayProperty=nameWithType> méthode dans l’API Roslyn, vous devez spécifier manuellement les fichiers d’assemblage de référence pour la bonne version de la plate-forme cible. .NET Les fichiers d’assemblage de référence du Cadre sont situés dans le *cadre\\\\\\Microsoft Assembly des % ProgramFiles(x86)% .\\ Annuaire NETFramework.* Pour .NET Core, vous pouvez forcer l’opération de publication à copier des assemblages de référence pour `PreserveCompilationContext` votre `true`plate-forme cible dans la sous-direction de votre répertoire de sortie *de publication/réfsation* en fixant la propriété du projet à . Ensuite, vous pouvez passer ces fichiers d’assemblage de référence au compilateur. L’utilisation `DependencyContext` du package [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/) peut aider à localiser leurs chemins.

Parce qu’ils ne contiennent aucune implémentation, les assemblages de référence ne peuvent pas être chargés pour l’exécution. Essayer de le faire <xref:System.BadImageFormatException?displayProperty=nameWithType>se traduit par un . Si vous souhaitez examiner le contenu d’un assemblage de référence, vous pouvez le <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> charger dans le <xref:System.Reflection.MetadataLoadContext> contexte de réflexion uniquement dans .NET Framework (en utilisant la méthode) ou dans le noyau en .NET.

## <a name="generating-reference-assemblies"></a>Génération d’assemblages de référence

Générer des assemblages de référence pour vos bibliothèques peut être utile lorsque les consommateurs de votre bibliothèque ont besoin de construire leurs programmes contre de nombreuses versions différentes de la bibliothèque. La distribution d’assemblages d’implémentation pour toutes ces versions peut être peu pratique en raison de leur grande taille. Les assemblages de référence sont de plus petite taille, et leur distribution dans le cadre du SDK de votre bibliothèque réduit la taille du téléchargement et permet d’économiser de l’espace disque.

Les IDE et les outils de construction peuvent également tirer parti des assemblages de référence pour réduire les temps de construction en cas de grandes solutions composées de bibliothèques de plusieurs classes. Habituellement, dans les scénarios de construction incrémentielle, un projet est reconstruit lorsque l’un de ses fichiers d’entrée est modifié, y compris les assemblages dont il dépend. L’assemblage de mise en œuvre change chaque fois que le programmeur modifie la mise en œuvre d’un membre. L’assemblage de référence ne change que lorsque son API public est affecté. Ainsi, l’utilisation de l’assemblage de référence comme fichier d’entrée au lieu de l’assemblage de mise en œuvre permet de sauter la construction du projet dépendant dans certains cas.

Vous pouvez générer des assemblages de référence :

- Dans un projet MSBuild, en utilisant la [ `ProduceReferenceAssembly` propriété](/visualstudio/msbuild/common-msbuild-project-properties)du projet .
- Lors de la compilation du programme à `-refonly` partir de la ligne `-refout` de commande, en spécifiant[(C -](../../csharp/language-reference/compiler-options/refonly-compiler-option.md) / Visual[Basic](../../visual-basic/reference/command-line-compiler/refonly-compiler-option.md) ) ou ( C[-](../../csharp/language-reference/compiler-options/refout-compiler-option.md) / [Visual Basic](../../visual-basic/reference/command-line-compiler/refout-compiler-option.md)) options compiler.
- Lors de l’utilisation de <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.EmitMetadataOnly?displayProperty=nameWithType> l’API Roslyn, en définissant `true` et <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.IncludePrivateMembers?displayProperty=nameWithType> à `false` dans un objet passé à la <xref:Microsoft.CodeAnalysis.Compilation.Emit%2A?displayProperty=nameWithType> méthode.

Si vous souhaitez distribuer des assemblages de référence avec des paquets NuGet, vous devez les inclure dans la sous-direction *de l’application\\ * du paquet au lieu de dans la sous-direction *lib\\ * utilisée pour les assemblages de mise en œuvre.

## <a name="reference-assemblies-structure"></a>Structure d’assemblages de référence

Les assemblages de référence sont une expansion du concept connexe, *des assemblages de métadonnées seulement*. Les assemblys de métadonnées uniquement ont leurs corps de méthode remplacés par un corps `throw null` unique, mais incluent tous les membres à l’exception des types anonymes. La raison `throw null` de l’utilisation des corps (par opposition à aucun corps) est de sorte que **PEVerify** peut courir et passer (validant ainsi l’exhaustivité des métadonnées).

En outre, les assemblys de référence suppriment les métadonnées (membres privés) des assemblys de métadonnées uniquement :

- Un assembly de référence a uniquement des références pour ce dont il a besoin dans la surface de l’API. L’assembly réel peut avoir des références supplémentaires relatives à des implémentations spécifiques. Par exemple, l’assemblage de référence pour `class C { private void M() { dynamic d = 1; ... } }` `dynamic`ne fait pas référence à tous les types requis pour .
- Les membres de fonction privés (méthodes, propriétés et événements) sont supprimés si leur suppression n’affecte pas la compilation sensiblement. S’il n’y a pas [d’attributs InternalsVisibleTo,](xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute) les membres de la fonction interne sont également supprimés.

Les métadonnées dans les assemblages de référence continuent de conserver les informations suivantes :

- Tous types, y compris les types privés et imbriqués.
- Tous les attributs, même internes.
- Toutes les méthodes virtuelles.
- Implémentations d’interface explicites.
- Propriétés et événements explicitement mis en œuvre, parce que leurs accesseurs sont virtuels.
- Tous les champs de structures.

Les assemblages de référence comprennent un attribut [Dementassembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) au niveau de l’assemblage. Cet attribut peut être spécifié dans la source; alors le compilateur n’aura pas besoin de le synthétiser. En raison de cet attribut, les temps d’exécution refuseront de charger des assemblages de référence pour l’exécution (mais ils peuvent être chargés en mode réflexion seulement).

Les détails exacts de la structure d’assemblage de référence dépendent de la version compilateur. Les versions plus nouvelles peuvent choisir d’exclure plus de métadonnées si elles sont déterminées comme n’affectant pas la surface publique de l’API.

> [!NOTE]
> Les informations contenues dans cette section ne s’appliquent qu’aux assemblages de référence générés par les compilateurs Roslyn à partir de la version 7.1 ou de la version 15.3 visual. La structure des assemblages de référence pour les bibliothèques de base .NET et .NET peuvent différer dans certains détails, car elles utilisent leur propre mécanisme de génération d’assemblages de référence. Par exemple, ils peuvent avoir des `throw null` corps de méthode totalement vides au lieu du corps. Mais le principe général s’applique toujours : ils n’ont pas de mise en œuvre de méthode utilisable et ne contiennent des métadonnées que pour les membres qui ont un impact observable du point de vue de l’API public.

## <a name="see-also"></a>Voir aussi

- [Assemblys dans .NET](index.md)
- [Vue d’ensemble du ciblage des frameworks](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Comment : Ajouter ou supprimer des références en utilisant le gestionnaire de référence](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)
