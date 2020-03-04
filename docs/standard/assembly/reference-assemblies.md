---
title: Assemblys de référence
description: En savoir plus sur les assemblys de référence, un type spécial d’assemblys dans .NET qui contiennent uniquement la surface de l’API publique de la bibliothèque
author: MSDN-WhiteKnight
ms.date: 09/12/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 3b85e51a015cca1e53ee2503c7bfa58c504fc718
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156463"
---
# <a name="reference-assemblies"></a>Assemblys de référence

Les *assemblys de référence* sont un type spécial d’assembly qui ne contient que la quantité minimale de métadonnées requises pour représenter la surface de l’API publique de la bibliothèque. Elles incluent des déclarations pour tous les membres qui sont significatifs lors du référencement d’un assembly dans les outils de génération, mais excluent toutes les implémentations de membres et les déclarations de membres privés qui n’ont aucun impact observable sur leur contrat d’API. En revanche, les assemblys standard sont appelés *assemblys d’implémentation*.

Les assemblys de référence ne peuvent pas être chargés pour l’exécution, mais ils peuvent être passés en tant qu’entrée de compilateur de la même façon que les assemblys d’implémentation. Les assemblys de référence sont généralement distribués avec le kit de développement logiciel (SDK) d’une plateforme ou d’une bibliothèque particulière.

L’utilisation d’un assembly de référence permet aux développeurs de générer des programmes qui ciblent une version de bibliothèque spécifique sans disposer de l’assembly d’implémentation complète pour cette version. Supposons que vous disposez uniquement de la dernière version d’une bibliothèque sur votre ordinateur, mais que vous souhaitez créer un programme qui cible une version antérieure de cette bibliothèque. Si vous compilez directement par rapport à l’assembly d’implémentation, vous pouvez utiliser par inadvertance des membres de l’API qui ne sont pas disponibles dans la version antérieure. Vous ne trouverez cette erreur que si vous testez le programme sur l’ordinateur cible. Si vous compilez par rapport à l’assembly de référence pour la version antérieure, vous obtenez immédiatement une erreur au moment de la compilation.

Un assembly de référence peut également représenter un contrat, c’est-à-dire un ensemble d’API qui ne correspondent pas à l’assembly d’implémentation concret. De tels assemblys de référence, appelés *assembly de contrat*, peuvent être utilisés pour cibler plusieurs plateformes qui prennent en charge le même ensemble d’API. Par exemple, .NET Standard fournit l’assembly de contrat, *netstandard. dll*, qui représente l’ensemble des API communes partagées entre différentes plateformes .net. Les implémentations de ces API sont contenues dans des assemblys différents sur différentes plateformes, comme *mscorlib. dll* sur .NET Framework ou *System. private. CoreLib. dll* sur .net core. Une bibliothèque qui cible .NET Standard peut s’exécuter sur toutes les plateformes qui prennent en charge .NET Standard.

## <a name="using-reference-assemblies"></a>Utilisation d’assemblys de référence

Pour utiliser certaines API à partir de votre projet, vous devez ajouter des références à leurs assemblys. Vous pouvez ajouter des références à des assemblys d’implémentation ou à des assemblys de référence. Il est recommandé d’utiliser des assemblys de référence chaque fois qu’ils sont disponibles. Cela vous permet de vous assurer que vous utilisez uniquement les membres de l’API pris en charge dans la version cible, destinés à être utilisés par les concepteurs d’API. L’utilisation de l’assembly de référence vous permet de vous assurer que vous n’êtes pas dépendant des détails d’implémentation.

Les assemblys de référence pour les bibliothèques .NET Framework sont distribués avec des packs de ciblage. Vous pouvez les obtenir en téléchargeant un programme d’installation autonome ou en sélectionnant un composant dans Visual Studio installer. Pour plus d’informations, consultez [installer le .NET Framework pour les développeurs](../../framework/install/guide-for-developers.md). Pour .NET Core et .NET Standard, les assemblys de référence sont automatiquement téléchargés si nécessaire (via NuGet) et référencés. Pour .NET Core 3,0 et versions ultérieures, les assemblys de référence pour l’infrastructure de base se trouvent dans le package [Microsoft. Netcore. app. Ref](https://www.nuget.org/packages/Microsoft.NETCore.App.Ref) (le package [Microsoft. Netcore. app](https://www.nuget.org/packages/Microsoft.NETCore.App) est utilisé à la place pour les versions antérieures à 3,0). Pour plus d’informations, consultez [packages, offres et infrastructures](../../core/packages.md) dans le guide .net core.

Quand vous ajoutez des références à des assemblys .NET Framework dans Visual Studio à l’aide de la boîte de dialogue **Ajouter une référence** , vous sélectionnez un assembly dans la liste, et Visual Studio recherche automatiquement les assemblys de référence qui correspondent à la version cible de .NET Framework sélectionnée dans votre projet. Il en va de même pour l’ajout de références directement dans le projet MSBuild à l’aide de l’élément de projet de [référence](/visualstudio/msbuild/common-msbuild-project-items#reference) : vous devez uniquement spécifier le nom de l’assembly, et non le chemin d’accès complet au fichier. Quand vous ajoutez des références à ces assemblys dans la ligne de commande à l’aide de l’option de compilateur `-reference` ([dans C# ](../../csharp/language-reference/compiler-options/reference-compiler-option.md) et dans [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md)) ou à l’aide de la méthode <xref:Microsoft.CodeAnalysis.Compilation.AddReferences%2A?displayProperty=nameWithType> dans l’API Roslyn, vous devez spécifier manuellement des fichiers d’assembly de référence pour la version de plateforme cible correcte. .NET Framework fichiers d’assembly de référence se trouvent dans les *assemblys de référence% ProgramFiles (x86)%\\\\Microsoft\\Framework\\. Répertoire NETFramework* . Pour .NET Core, vous pouvez forcer l’opération de publication à copier des assemblys de référence pour votre plateforme cible dans le sous-répertoire *Publish/REFS* de votre répertoire de sortie en affectant à la propriété `PreserveCompilationContext` Project la valeur `true`. Vous pouvez ensuite passer ces fichiers d’assembly de référence au compilateur. L’utilisation de `DependencyContext` du package [Microsoft. extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/) peut faciliter la localisation de leurs chemins d’accès.

Étant donné qu’elles ne contiennent aucune implémentation, les assemblys de référence ne peuvent pas être chargés pour l’exécution ; Si vous tentez de le faire, une <xref:System.BadImageFormatException?displayProperty=nameWithType>est générée. Toutefois, elles peuvent toujours être chargées dans le contexte de réflexion uniquement (à l’aide de la méthode <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType>), si vous devez examiner leur contenu.

## <a name="generating-reference-assemblies"></a>Génération d’assemblys de référence

La génération d’assemblys de référence pour vos bibliothèques peut être utile lorsque les consommateurs de votre bibliothèque doivent créer leurs programmes sur de nombreuses versions différentes de la bibliothèque. La distribution d’assemblys d’implémentation pour toutes ces versions peut être irréalisable en raison de leur taille importante. La taille des assemblys de référence est plus petite et leur distribution dans le cadre du kit de développement logiciel (SDK) de votre bibliothèque réduit la taille du téléchargement et économise de l’espace disque.

Les IDE et les outils de génération peuvent également tirer parti des assemblys de référence pour réduire les délais de génération en cas de solutions volumineuses composées de plusieurs bibliothèques de classes. En général, dans les scénarios de génération incrémentielle, un projet est régénéré quand l’un de ses fichiers d’entrée est modifié, y compris les assemblys dont il dépend. L’assembly d’implémentation change chaque fois que le programmeur modifie l’implémentation d’un membre. L’assembly de référence change uniquement lorsque son API publique est affectée. Ainsi, l’utilisation de l’assembly de référence comme fichier d’entrée au lieu de l’assembly d’implémentation permet d’ignorer la génération du projet dépendant dans certains cas.

Vous pouvez générer des assemblys de référence :

- Dans un projet MSBuild, à l’aide de la [propriété de projet`ProduceReferenceAssembly`](/visualstudio/msbuild/common-msbuild-project-properties).
- Lors de la compilation d’un programme à partir de la[C#](../../csharp/language-reference/compiler-options/refonly-compiler-option.md) ligne de commande, en fonction[C#](../../csharp/language-reference/compiler-options/refout-compiler-option.md) des options du compilateur `-refonly` ( / [Visual Basic](../../visual-basic/reference/command-line-compiler/refonly-compiler-option.md) ) ou `-refout` ( / [Visual Basic](../../visual-basic/reference/command-line-compiler/refout-compiler-option.md)).
- Lorsque vous utilisez l’API Roslyn, en définissant <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.EmitMetadataOnly?displayProperty=nameWithType> sur `true` et <xref:Microsoft.CodeAnalysis.Emit.EmitOptions.IncludePrivateMembers?displayProperty=nameWithType> pour `false` dans un objet passé à la méthode <xref:Microsoft.CodeAnalysis.Compilation.Emit%2A?displayProperty=nameWithType>.

Si vous souhaitez distribuer des assemblys de référence avec des packages NuGet, vous devez les inclure dans le sous-répertoire *ref\\* sous le répertoire du package plutôt que dans le sous-répertoire *lib\\* utilisé pour les assemblys d’implémentation.

## <a name="reference-assemblies-structure"></a>Structure des assemblys de référence

Les assemblys de référence sont une expansion du concept connexe, des *assemblys de métadonnées uniquement*. Les assemblys de métadonnées uniquement ont leurs corps de méthode remplacés par un corps `throw null` unique, mais incluent tous les membres à l’exception des types anonymes. La raison de l’utilisation de `throw null` corps (par opposition à aucun corps) est que **PEVerify** peut s’exécuter et réussir (validant ainsi l’exhaustivité des métadonnées).

En outre, les assemblys de référence suppriment les métadonnées (membres privés) des assemblys de métadonnées uniquement :

- Un assembly de référence a uniquement des références pour ce dont il a besoin dans la surface de l’API. L’assembly réel peut avoir des références supplémentaires relatives à des implémentations spécifiques. Par exemple, l’assembly de référence pour `class C { private void M() { dynamic d = 1; ... } }` ne fait référence à aucun type requis pour la `dynamic`.
- Les membres de fonction privés (méthodes, propriétés et événements) sont supprimés si leur suppression n’affecte pas la compilation sensiblement. S’il n’y a pas d’attributs [InternalsVisibleTo](xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute) , les membres de fonction internes sont également supprimés.

Les métadonnées dans les assemblys de référence continuent à conserver les informations suivantes :

- Tous les types, y compris les types privés et imbriqués.
- Tous les attributs, y compris internes.
- Toutes les méthodes virtuelles.
- Implémentations d’interface explicites.
- Les propriétés et les événements implémentés explicitement, car leurs accesseurs sont virtuels.
- Tous les champs de structures.

Les assemblys de référence incluent un attribut [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) au niveau de l’assembly. Cet attribut peut être spécifié dans la source ; le compilateur n’a pas besoin de le synthétiser. En raison de cet attribut, les runtimes refusent de charger des assemblys de référence pour l’exécution (mais ils peuvent être chargés en mode de réflexion uniquement).

Les détails de la structure de l’assembly de référence exact dépendent de la version du compilateur. Les versions plus récentes peuvent choisir d’exclure davantage de métadonnées si elles sont déterminées comme n’affectant pas la surface de l’API publique.

> [!NOTE]
> Les informations contenues dans cette section s’appliquent uniquement aux assemblys de référence générés par C# les compilateurs Roslyn à partir de la version 7,1 ou Visual Basic version 15,3. La structure des assemblys de référence pour les .NET Framework et les bibliothèques .NET Core peut différer dans certains détails, car ils utilisent leur propre mécanisme de génération d’assemblys de référence. Par exemple, ils peuvent avoir des corps de méthode entièrement vides au lieu du corps du `throw null`. Toutefois, le principe général s’applique toujours : ils n’ont pas d’implémentations de méthode utilisables et contiennent uniquement des métadonnées pour les membres qui ont un impact observable à partir d’une perspective d’API publique.

## <a name="see-also"></a>Voir aussi

- [Assemblys dans .NET](index.md)
- [Vue d’ensemble du ciblage des frameworks](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Procédure : ajouter ou supprimer des références à l’aide du gestionnaire de références](/visualstudio/ide/how-to-add-or-remove-references-by-using-the-reference-manager)
