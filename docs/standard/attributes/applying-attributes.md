---
title: Application des attributs
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET], attributes
- attributes [.NET], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
ms.openlocfilehash: 24fe58ddf48e40b422652baa4c5bba86eea6b84f
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92889229"
---
# <a name="apply-attributes"></a>Appliquer des attributs

Effectuez la procédure suivante pour appliquer un attribut à un élément de votre code.

1. Définissez un nouvel attribut ou utilisez un attribut .NET existant.

2. Appliquez l’attribut à l’élément de code en le plaçant immédiatement avant l’élément.

     Chaque langage possède sa propre syntaxe d’attribut. Dans C++ et C#, l’attribut est entouré par des crochets et séparé de l’élément par un espace blanc, qui peut inclure un saut de ligne. Dans Visual Basic, l’attribut est entouré par des crochets angulaires et doit se trouver sur la même ligne logique. Le caractère de continuation de ligne peut être utilisé si vous souhaitez un saut de ligne.

3. Spécifiez des paramètres positionnels et des paramètres nommés pour l’attribut.

     Les paramètres *positionnels* sont requis et doivent précéder les paramètres nommés. elles correspondent aux paramètres de l’un des constructeurs de l’attribut. Les paramètres *nommés* sont facultatifs et correspondent aux propriétés de lecture/écriture de l’attribut. En C++ et C#, spécifiez `name=value` pour chaque paramètre facultatif, où `name` est le nom de la propriété. Dans Visual Basic, spécifiez `name:=value` .

 L’attribut est émis dans des métadonnées lorsque vous compilez votre code et est disponible pour le common language runtime et toute application ou tout outil personnalisé via les services de réflexion du runtime.

 Par Convention, tous les noms d’attributs se terminent par « Attribute ». Toutefois, plusieurs langages qui ciblent le runtime, tels que Visual Basic et C#, ne nécessitent pas de spécifier le nom complet d’un attribut. Par exemple, si vous souhaitez initialiser <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, vous devez uniquement le référencer en tant qu’attribut **obsolète** .

## <a name="apply-an-attribute-to-a-method"></a>Appliquer un attribut à une méthode

 L’exemple de code suivant montre comment utiliser **System. ObsoleteAttribute** , qui marque le code comme obsolète. La chaîne `"Will be removed in next version"` est passée à l’attribut. Cet attribut provoque un avertissement du compilateur qui affiche la chaîne passée lorsque le code que l’attribut décrit est appelé.

 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]

## <a name="apply-attributes-at-the-assembly-level"></a>Appliquer des attributs au niveau de l’assembly

 Si vous souhaitez appliquer un attribut au niveau de l’assembly, utilisez `assembly` le `Assembly` mot clé (en Visual Basic). Le code suivant illustre l’attribut **AssemblyTitleAttribute** appliqué au niveau de l’assembly.

 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]

 Lorsque cet attribut est appliqué, la chaîne `"My Assembly"` est placée dans le manifeste de l’assembly dans la partie métadonnées du fichier. Vous pouvez afficher l’attribut à l’aide du [Désassembleur MSIL (Ildasm.exe)](../../framework/tools/ildasm-exe-il-disassembler.md) ou en créant un programme personnalisé pour récupérer l’attribut.

## <a name="see-also"></a>Voir aussi

- [Attributs](index.md)
- [Récupération des informations stockées dans les attributs](retrieving-information-stored-in-attributes.md)
- [Concepts](/cpp/windows/attributed-programming-concepts)
- [Attributs (C#)](../../csharp/programming-guide/concepts/attributes/index.md)
- [Vue d’ensemble des attributs (Visual Basic)](../../visual-basic/programming-guide/concepts/attributes/index.md)
