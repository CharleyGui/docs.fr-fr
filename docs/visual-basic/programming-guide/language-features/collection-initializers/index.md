---
title: Initialiseurs de collections
ms.date: 07/20/2015
f1_keywords:
- vb.CollectionInitializer
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: a9290329-77b0-4fdf-ae75-8fc17287f469
ms.openlocfilehash: fbdd116298c530ae54677631eff7dac2f22c0fe2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346780"
---
# <a name="collection-initializers-visual-basic"></a>Initialiseurs de collections (Visual Basic)

Les *initialiseurs de collections* fournissent une syntaxe raccourcie qui vous permet de créer une collection et de la remplir avec un ensemble initial de valeurs. Les initialiseurs de collections sont utiles lorsque vous créez une collection à partir d’un ensemble de valeurs connues (par exemple, une liste d’options de menu ou de catégories, un ensemble initial de valeurs numériques, une liste statique de chaînes telles que des noms de jours ou de mois, ou des emplacements géographiques tels qu’une liste d’états utilisée pour la validation).

Pour plus d’informations sur les collections, consultez [Collections](../../../../visual-basic/programming-guide/concepts/collections.md).

Vous identifiez un initialiseur de collection à l’aide du mot clé `From` suivi d’accolades (`{}`). Cette syntaxe est similaire à la syntaxe des littéraux de tableau décrite dans [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md). Les exemples suivants montrent différentes manières d’utiliser des initialiseurs de collections pour créer des collections.

[!code-vb[VbVbalrCollectionInitializers#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#1)]

> [!NOTE]
> C# fournit également des initialiseurs de collections. Les initialiseurs de collections C# fournissent les mêmes fonctionnalités que les initialiseurs de collections Visual Basic. Pour plus d’informations sur les initialiseurs de collections C#, consultez [Initialiseurs d’objets et de collections](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).

## <a name="syntax"></a>Syntaxe

Un initialiseur de collection se compose d’une liste de valeurs séparées par des virgules et placées entre accolades (`{}`), précédées par le mot clé `From`, comme illustré dans le code suivant.

[!code-vb[VbVbalrCollectionInitializers#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#2)]

Lorsque vous créez une collection, comme un <xref:System.Collections.Generic.List%601> ou un <xref:System.Collections.Generic.Dictionary%602>, vous devez fournir le type de collection avant l’initialiseur de collection, comme indiqué dans le code suivant.

[!code-vb[VbVbalrCollectionInitializers#13](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#13)]

> [!NOTE]
> Vous ne pouvez pas combiner un initialiseur de collection et un initialiseur d’objet pour initialiser le même objet de collection. Vous pouvez utiliser des initialiseurs d’objets pour initialiser des objets dans un initialiseur de collection.

## <a name="creating-a-collection-by-using-a-collection-initializer"></a>Création d’une collection à l’aide d’un initialiseur de collection

Lorsque vous créez une collection à l’aide d’un initialiseur de collection, chaque valeur fournie dans l’initialiseur de collection est passée à la méthode `Add` appropriée de la collection. Par exemple, si vous créez un <xref:System.Collections.Generic.List%601> en utilisant un initialiseur de collection, chaque valeur de chaîne de l’initialiseur de collection est passée à la méthode <xref:System.Collections.Generic.List%601.Add%2A>. Si vous souhaitez créer une collection à l’aide d’un initialiseur de collection, le type spécifié doit être un type de collection valide. Les types de collections valides sont, par exemple, des classes qui implémentent l’interface <xref:System.Collections.Generic.IEnumerable%601> ou qui héritent de la classe <xref:System.Collections.CollectionBase>. Le type spécifié doit également exposer une méthode `Add` qui répond aux critères suivants.

- La méthode `Add` doit être disponible à partir de la portée dans laquelle l’initialiseur de collection est appelé. La méthode `Add` ne doit pas nécessairement être publique si vous utilisez l’initialiseur de collection dans un scénario où les méthodes non publiques de la collection sont accessibles.

- La méthode `Add` doit être un membre d’instance ou un membre `Shared` de la classe de collection, ou une méthode d’extension.

- Il doit exister une méthode `Add` pouvant être mise en correspondance, selon les règles de résolution de surcharge, avec les types fournis dans l’initialiseur de collection.

 Ainsi, l’exemple de code suivant montre comment créer une collection `List(Of Customer)` à l’aide d’un initialiseur de collection. Lorsque le code est exécuté, chaque objet `Customer` est passé à la méthode `Add(Customer)` de la liste générique.

[!code-vb[VbVbalrCollectionInitializers#9](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#9)]

L’exemple de code suivant montre le code équivalent qui n’utilise pas d’initialiseur de collection.

[!code-vb[VbVbalrCollectionInitializers#10](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#10)]

Si la collection a une méthode `Add` ayant des paramètres qui correspondent au constructeur de l’objet `Customer`, vous pouvez imbriquer des valeurs de paramètre pour la méthode `Add` dans les initialiseurs de collections, comme indiqué dans la section suivante. Si la collection n’a pas une telle méthode `Add`, vous pouvez en créer une comme méthode d’extension. Pour obtenir un exemple montrant comment créer une méthode `Add` comme méthode d’extension pour une collection, consultez [Guide pratique pour créer une méthode d’extension Add utilisée par un initialiseur de collection](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md). Pour obtenir un exemple montrant comment créer une collection personnalisée pouvant être utilisée avec un initialiseur de collection, consultez [Guide pratique pour créer une collection utilisée par un initialiseur de collection](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md).

## <a name="nesting-collection-initializers"></a>Imbrication d’initialiseurs de collections

Vous pouvez imbriquer des valeurs dans un initialiseur de collection pour identifier une surcharge spécifique d’une méthode `Add` pour la collection qui est créée. Les valeurs passées à la méthode `Add` doivent être séparées par des virgules et placées entre accolades (`{}`), comme vous le feriez dans un littéral de tableau ou un initialiseur de collection.

Lorsque vous créez une collection à l’aide de valeurs imbriquées, chaque élément de la liste de valeurs imbriquée est passé comme argument à la méthode `Add` correspondant aux types d’éléments. Ainsi, l’exemple de code suivant crée un <xref:System.Collections.Generic.Dictionary%602> dans lequel les clés sont de type `Integer` et les valeurs sont de type `String`. Chacune des listes de valeurs imbriquées est mise en correspondance avec la méthode <xref:System.Collections.Generic.Dictionary%602.Add%2A> pour `Dictionary`.

[!code-vb[VbVbalrCollectionInitializers#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#5)]

L’exemple de code précédent est équivalent au code suivant.

[!code-vb[VbVbalrCollectionInitializers#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializers/VB/Module1.vb#6)]

Seules les listes de valeurs imbriquées du premier niveau d’imbrication sont envoyées à la méthode `Add` pour le type de collection. Les niveaux d’imbrication plus profonds sont traités comme des littéraux de tableau et les listes de valeurs imbriquées ne sont pas mises en correspondance avec la méthode `Add` de toute collection.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|---|---|
|[Guide pratique : créer une méthode d’extension Add utilisée par un initialiseur de collection](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)|Montre comment créer une méthode d’extension appelée `Add` qui peut être utilisée pour renseigner une collection avec des valeurs d’un initialiseur de collection.|
|[Guide pratique : créer une collection utilisée par un initialiseur de collection](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)|Montre comment activer l’utilisation d’un initialiseur de collection en incluant une méthode `Add` dans une classe de collection qui implémente `IEnumerable`.|

## <a name="see-also"></a>Voir aussi

- [Regroupements](../../../../visual-basic/programming-guide/concepts/collections.md)
- [Tableaux](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Initialiseurs d’objets : types nommés et anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [New (opérateur)](../../../../visual-basic/language-reference/operators/new-operator.md)
- [Propriétés implémentées automatiquement](../../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [Comment : initialiser une variable tableau en Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
- [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Guide pratique : créer une liste d’éléments](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
