---
title: Utilisation des fichiers .resx par programmation
description: Créez ou récupérez des données à partir de fichiers de ressources XML (. resx) par programmation à l’aide de types et de membres dans l’espace de noms System. Resources de la bibliothèque de classes .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resource files, .resx files
- .resx files
ms.assetid: 168f941a-2b84-43f8-933f-cf4a8548d824
ms.openlocfilehash: c6b1ef6c7dd8be3dbc98b2298ab0e649ff74008e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254504"
---
# <a name="work-with-resx-files-programmatically"></a>Utiliser des fichiers .resx par programmation

Étant donné que les fichiers de ressources XML (.resx) doivent être constitués de code XML bien défini, notamment un en-tête qui doit respecter un schéma spécifique, suivi de données dans des paires nom/valeur, la création manuelle de ces fichiers est sujette aux erreurs. Alternativement, vous pouvez créer des fichiers .resx par programmation à l’aide de types et de membres de la bibliothèque de classes .NET. Vous pouvez également utiliser la bibliothèque de classes .NET pour récupérer des ressources stockées dans les fichiers .resx. Cet article explique comment vous pouvez utiliser les types et les membres de l' <xref:System.Resources> espace de noms pour travailler avec des fichiers. resx.

Cet article traite de l’utilisation de fichiers XML (. resx) contenant des ressources. Pour plus d’informations sur l’utilisation des fichiers de ressources binaires incorporés dans des assemblys, consultez <xref:System.Resources.ResourceManager> .

> [!WARNING]
> Vous pouvez également utiliser les fichiers .resx autrement que par programmation. Quand vous ajoutez un fichier de ressources à un projet [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) , Visual Studio fournit une interface pour la création et la gestion d’un fichier. resx, et convertit automatiquement le fichier. resx en fichier. Resources au moment de la compilation. Vous pouvez également utiliser un éditeur de texte pour manipuler directement un fichier .resx. Toutefois, pour éviter d’endommager le fichier, veillez à ne pas modifier les informations binaires stockées dans le fichier.

## <a name="create-a-resx-file"></a>Créer un fichier .resx

Vous pouvez utiliser la classe <xref:System.Resources.ResXResourceWriter?displayProperty=nameWithType> pour créer un fichier .resx par programmation, en procédant comme suit :

1. Instanciez un objet <xref:System.Resources.ResXResourceWriter> en appelant la méthode <xref:System.Resources.ResXResourceWriter.%23ctor%28System.String%29> et en fournissant le nom du fichier .resx. Le nom de fichier doit inclure l’extension .resx. Si vous instanciez l’objet <xref:System.Resources.ResXResourceWriter> dans un bloc `using` , vous n’avez pas besoin d’appeler explicitement la méthode <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> à l’étape 3.

2. Appelez la méthode <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> pour chaque ressource que vous voulez ajouter au fichier. Utilisez les surcharges de cette méthode pour ajouter la chaîne, l’objet et les données binaires (tableau d’octets). Si la ressource est un objet, celui-ci doit être sérialisable.

3. Appelez la méthode <xref:System.Resources.ResXResourceWriter.Close%2A?displayProperty=nameWithType> pour générer le fichier de ressources et libérer toutes les ressources. Si l’objet <xref:System.Resources.ResXResourceWriter> a été créé dans un bloc `using` , les ressources sont écrites dans le fichier .resx et celles qui sont utilisées par l’objet <xref:System.Resources.ResXResourceWriter> sont libérées à la fin du bloc `using` .

Le fichier .resx résultant possède l’en-tête approprié et une balise `data` pour chaque ressource ajoutée par la méthode <xref:System.Resources.ResXResourceWriter.AddResource%2A?displayProperty=nameWithType> .

> [!WARNING]
> N’utilisez pas de fichier de ressources pour stocker des mots de passe, des informations sensibles ou des données privées.

L’exemple suivant crée un fichier .resx nommé CarResources.resx qui stocke six chaînes, une icône et deux objets définis par l’application (deux objets `Automobile` ). La `Automobile` classe, qui est définie et instanciée dans l’exemple, est marquée avec l' <xref:System.SerializableAttribute> attribut.

[!code-csharp[Conceptual.Resources.ResX#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/create1.cs#1)]
[!code-vb[Conceptual.Resources.ResX#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/create1.vb#1)]

> [!TIP]
> Vous pouvez également utiliser [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) pour créer des fichiers. resx. Au moment de la compilation, Visual Studio utilise l’outil [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) pour convertir le fichier .resx en fichier de ressources binaires (.resources), et l’incorpore dans un assembly d’application ou un assembly satellite.

Vous ne pouvez pas incorporer un fichier .resx dans un exécutable du Common Language Runtime ou le compiler dans un assembly satellite. Vous devez convertir votre fichier .resx en fichier de ressources binaires (.resources) à l’aide de l’outil [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md). Le fichier .resources résultant peut ensuite être incorporé dans un assembly d’application ou un assembly satellite. Pour plus d'informations, consultez [Creating Resource Files](creating-resource-files-for-desktop-apps.md).

## <a name="enumerate-resources"></a>Énumérer les ressources

 Dans certains cas, vous voulez récupérer toutes les ressources d’un fichier .resx, et pas seulement une ressource spécifique. Pour ce faire, vous pouvez utiliser la classe <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> , qui fournit un énumérateur pour toutes les ressources du fichier .resx. La classe <xref:System.Resources.ResXResourceReader?displayProperty=nameWithType> implémente <xref:System.Collections.IDictionaryEnumerator>, qui retourne un objet <xref:System.Collections.DictionaryEntry> représentant une ressource particulière pour chaque itération de la boucle. Sa propriété <xref:System.Collections.DictionaryEntry.Key%2A?displayProperty=nameWithType> retourne la clé de la ressource et sa propriété <xref:System.Collections.DictionaryEntry.Value%2A?displayProperty=nameWithType> retourne la valeur de la ressource.

 L’exemple suivant crée un objet <xref:System.Resources.ResXResourceReader> pour le fichier CarResources.resx créé dans l’exemple précédent et itère au sein du fichier de ressources. Il ajoute les deux objets `Automobile` définis dans le fichier de ressources à un objet <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> , et ajoute cinq des six chaînes à un objet <xref:System.Collections.SortedList> . Les valeurs de l’objet <xref:System.Collections.SortedList> sont converties en tableau de paramètres, utilisé pour afficher des en-têtes de colonne dans la console. Les valeurs de propriété `Automobile` sont également affichées dans la console.

 [!code-csharp[Conceptual.Resources.ResX#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/enumerate1.cs#2)]
 [!code-vb[Conceptual.Resources.ResX#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/enumerate1.vb#2)]

## <a name="retrieve-a-specific-resource"></a>Récupérer une ressource spécifique

 Outre l’énumération des éléments d’un fichier .resx, vous pouvez récupérer une ressource spécifique par son nom à l’aide de la classe <xref:System.Resources.ResXResourceSet?displayProperty=nameWithType> . La méthode <xref:System.Resources.ResourceSet.GetString%28System.String%29?displayProperty=nameWithType> extrait la valeur d’une ressource de chaîne nommée. La méthode <xref:System.Resources.ResourceSet.GetObject%28System.String%29?displayProperty=nameWithType> extrait la valeur d’un objet nommé ou des données binaires. La méthode retourne un objet qui doit être casté (en C#) ou converti (en Visual Basic) en objet de type approprié.

 L’exemple suivant récupère la chaîne et l’icône de la légende d’un formulaire par leur nom de ressources. Elle récupère également les objets `Automobile` définis par l’application utilisés dans l’exemple précédent et les affiche dans un contrôle <xref:System.Windows.Forms.DataGridView>.

 [!code-csharp[Conceptual.Resources.ResX#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.resx/cs/retrieve1.cs#3)]
 [!code-vb[Conceptual.Resources.ResX#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.resx/vb/retrieve1.vb#3)]

## <a name="convert-resx-files-to-binary-resources-files"></a>Convertir les fichiers .resx en fichiers binaires .resources

 La conversion de fichiers .resx en fichiers de ressources binaires incorporés (.resources) présente des avantages importants. Bien que les fichiers .resx soient faciles à lire et à gérer pendant le développement d’applications, ils sont rarement inclus avec les applications finies. S’ils sont distribués avec une application, ils existent en tant que fichiers séparés de l’exécutable de l’application et des bibliothèques qui l’accompagnent. En revanche, les fichiers .resources sont incorporés dans l’exécutable d’application ou dans les assemblys qui l’accompagnent. Par ailleurs, pour les applications localisées, l’utilisation de fichiers .resx au moment de l’exécution donne au développeur la responsabilité de la gestion des ressources de secours. En revanche, si un ensemble d’assemblys satellites contenant des fichiers .resources incorporés a été créé, le Common Language Runtime gère le processus de secours pour les ressources.

 Pour convertir un fichier .resx en fichier .resources, vous utilisez l’outil [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md), qui présente la syntaxe de base suivante :

 **Resgen.exe** *.resxFilename*

 Le résultat est un fichier de ressources binaires ayant le même nom de fichier racine que celui du fichier .resx et une extension de fichier .resources. Ce fichier peut ensuite être compilé en exécutable ou bibliothèque au moment de la compilation. Si vous utilisez le compilateur Visual Basic, utilisez la syntaxe suivante pour incorporer un fichier .resources dans l’exécutable d’une application :

 **vbc** *filename* **.vb -resource:** *.resourcesFilename*

 Si vous utilisez C#, la syntaxe est la suivante :

 **csc** *filename* **.cs -resource:** *.resourcesFilename*

 Le fichier .resources peut également être incorporé dans un assembly satellite à l’aide de l’utilitaire [Assembly Linker (AL.exe)](../tools/al-exe-assembly-linker.md), qui présente la syntaxe de base suivante :

 **al** *resourcesFilename* **-out:** *assemblyFilename*

## <a name="see-also"></a>Voir aussi

- [Création de fichiers de ressources](creating-resource-files-for-desktop-apps.md)
- [Resgen.exe (générateur de fichiers de ressources)](../tools/resgen-exe-resource-file-generator.md)
- [Al.exe (Assembly Linker)](../tools/al-exe-assembly-linker.md)
