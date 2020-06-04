---
title: Types anonymes
ms.date: 07/20/2015
f1_keywords:
- vb.AnonymousType
helpviewer_keywords:
- anonymous types [Visual Basic], about anonymous types
- anonymous types [Visual Basic]
- types [Visual Basic], anonymous
ms.assetid: 7b87532c-4b3e-4398-8503-6ea9d67574a4
ms.openlocfilehash: bbe84ce8a62705027c00bc26db74a3c21fa34fd9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411795"
---
# <a name="anonymous-types-visual-basic"></a>Types anonymes (Visual Basic)
Visual Basic prend en charge les types anonymes, qui vous permettent de créer des objets sans écrire de définition de classe pour le type de données. À la place, le compilateur se charge de générer une classe. La classe n’a pas de nom utilisable, hérite directement de <xref:System.Object> et contient les propriétés que vous spécifiez lors de la déclaration de l’objet. Étant donné que le nom du type de données n’est pas spécifié, il est appelé *type anonyme*.  
  
 L’exemple suivant déclare et crée une variable `product` comme une instance d’un type anonyme qui a deux propriétés, `Name` et `Price` .  
  
 [!code-vb[VbVbalrAnonymousTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#1)]  
  
 Une *expression de requête* utilise des types anonymes pour combiner des colonnes de données sélectionnées par une requête. Vous ne pouvez pas définir le type du résultat à l’avance, car vous ne pouvez pas prédire les colonnes qu’une requête particulière peut sélectionner. Les types anonymes vous permettent d’écrire une requête qui sélectionne un nombre quelconque de colonnes, dans n’importe quel ordre. Le compilateur crée un type de données qui correspond aux propriétés spécifiées et à l’ordre spécifié.  
  
 Dans les exemples suivants, `products` est une liste d’objets Product, chacun ayant de nombreuses propriétés. `namePriceQuery`La variable contient la définition d’une requête qui, lorsqu’elle est exécutée, retourne une collection d’instances d’un type anonyme qui a deux propriétés, `Name` et `Price` .  
  
 [!code-vb[VbVbalrAnonymousTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#2)]  
  
 `nameQuantityQuery`La variable contient la définition d’une requête qui, lorsqu’elle est exécutée, retourne une collection d’instances d’un type anonyme qui a deux propriétés, `Name` et `OnHand` .  
  
 [!code-vb[VbVbalrAnonymousTypes#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#3)]  
  
 Pour plus d’informations sur le code créé par le compilateur pour un type anonyme, consultez [définition de type anonyme](anonymous-type-definition.md).  
  
> [!CAUTION]
> Le nom du type anonyme est généré par le compilateur et peut varier de la compilation à la compilation. Votre code ne doit pas utiliser ou s’appuyer sur le nom d’un type anonyme, car le nom peut changer quand un projet est recompilé.  
  
## <a name="declaring-an-anonymous-type"></a>Déclaration d’un type anonyme  
 La déclaration d’une instance d’un type anonyme utilise une liste d’initialiseurs pour spécifier les propriétés du type. Vous pouvez spécifier uniquement des propriétés lorsque vous déclarez un type anonyme, et non d’autres éléments de classe tels que des méthodes ou des événements. Dans l’exemple suivant, `product1` est une instance d’un type anonyme qui a deux propriétés : `Name` et `Price` .  
  
 [!code-vb[VbVbalrAnonymousTypes#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#4)]  
  
 Si vous désignez des propriétés en tant que propriétés de clé, vous pouvez les utiliser pour comparer deux instances de type anonymes pour déterminer leur égalité. Toutefois, les valeurs des propriétés de clé ne peuvent pas être modifiées. Pour plus d’informations, consultez la section Propriétés de clé plus loin dans cette rubrique.  
  
 Notez que la déclaration d’une instance d’un type anonyme est semblable à la déclaration d’une instance d’un type nommé à l’aide d’un initialiseur d’objet :  
  
 [!code-vb[VbVbalrAnonymousTypes#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#5)]  
  
 Pour plus d’informations sur d’autres façons de spécifier des propriétés de type anonyme, consultez [Comment : déduire les types et les noms de propriétés dans des déclarations de type anonyme](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="key-properties"></a>Propriétés de clé  
 Les propriétés de clé diffèrent des propriétés non-clés de plusieurs façons :  
  
- Seules les valeurs des propriétés de clé sont comparées afin de déterminer si deux instances sont égales.  
  
- Les valeurs des propriétés de clé sont en lecture seule et ne peuvent pas être modifiées.  
  
- Seules les valeurs de propriété de clé sont incluses dans l’algorithme de code de hachage généré par le compilateur pour un type anonyme.  
  
### <a name="equality"></a>Égalité  
 Les instances de types anonymes peuvent être égales uniquement si elles sont des instances du même type anonyme. Le compilateur traite deux instances comme des instances du même type s’ils remplissent les conditions suivantes :  
  
- Ils sont déclarés dans le même assembly.  
  
- Leurs propriétés ont les mêmes noms, les mêmes types déduits et sont déclarées dans le même ordre. Les comparaisons de noms ne respectent pas la casse.  
  
- Les mêmes propriétés dans chaque sont marquées en tant que propriétés de clé.  
  
- Au moins une propriété de chaque déclaration est une propriété de clé.  
  
 Une instance d’un type anonyme qui n’a pas de propriétés de clé est uniquement égale à elle-même.  
  
 [!code-vb[VbVbalrAnonymousTypes#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#6)]  
  
 Deux instances du même type anonyme sont égales si les valeurs de leurs propriétés de clé sont égales. Les exemples suivants illustrent la manière dont l’égalité est testée.  
  
 [!code-vb[VbVbalrAnonymousTypes#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#7)]  
  
### <a name="read-only-values"></a>Valeurs en lecture seule  
 Les valeurs des propriétés de clé ne peuvent pas être modifiées. Par exemple, dans `prod8` dans l’exemple précédent, les `Name` `Price` champs et sont `read-only` , mais ils `OnHand` peuvent être modifiés.  
  
 [!code-vb[VbVbalrAnonymousTypes#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#8)]  
  
## <a name="anonymous-types-from-query-expressions"></a>Types anonymes à partir d’expressions de requête  
 Les expressions de requête ne nécessitent pas toujours la création de types anonymes. Lorsque cela est possible, ils utilisent un type existant pour contenir les données de la colonne. Cela se produit lorsque la requête retourne des enregistrements entiers de la source de données ou un seul champ de chaque enregistrement. Dans les exemples de code suivants, `customers` est une collection d’objets d’une `Customer` classe. La classe possède de nombreuses propriétés, et vous pouvez inclure une ou plusieurs d’entre elles dans le résultat de la requête, dans n’importe quel ordre. Dans les deux premiers exemples, aucun type anonyme n’est nécessaire, car les requêtes sélectionnent des éléments de types nommés :  
  
- `custs1`contient une collection de chaînes, car `cust.Name` est une chaîne.  
  
     [!code-vb[VbVbalrAnonymousTypes#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#30)]  
  
- `custs2`contient une collection d' `Customer` objets, car chaque élément de `customers` est un `Customer` objet et la totalité de l’élément est sélectionnée par la requête.  
  
     [!code-vb[VbVbalrAnonymousTypes#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#31)]  
  
 Toutefois, les types nommés appropriés ne sont pas toujours disponibles. Vous pouvez sélectionner des noms et des adresses de clients pour un seul objectif, des numéros d’identification client et des emplacements pour un autre, ainsi que des noms de clients, des adresses et des historiques de commande pour un troisième. Les types anonymes vous permettent de sélectionner n’importe quelle combinaison de propriétés, dans n’importe quel ordre, sans déclarer d’abord un nouveau type nommé pour contenir le résultat. Au lieu de cela, le compilateur crée un type anonyme pour chaque compilation des propriétés. La requête suivante sélectionne uniquement le nom et le numéro d’ID du client à partir de chaque `Customer` objet dans `customers` . Par conséquent, le compilateur crée un type anonyme qui contient uniquement ces deux propriétés.  
  
 [!code-vb[VbVbalrAnonymousTYpes#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#32)]  
  
 Les noms et les types de données des propriétés dans le type anonyme sont extraits des arguments à `Select` , `cust.Name` et `cust.ID` . Les propriétés d’un type anonyme créé par une requête sont toujours des propriétés de clé. Lorsque `custs3` est exécuté dans la `For Each` boucle suivante, le résultat est une collection d’instances d’un type anonyme avec deux propriétés de clé, `Name` et `ID` .  
  
 [!code-vb[VbVbalrAnonymousTypes#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#33)]  
  
 Les éléments de la collection représentée par `custs3` sont fortement typés, et vous pouvez utiliser IntelliSense pour parcourir les propriétés disponibles et vérifier leurs types.  
  
 Pour plus d’informations, consultez [Introduction à LINQ dans Visual Basic](../linq/introduction-to-linq.md).  
  
## <a name="deciding-whether-to-use-anonymous-types"></a>Choix de l’utilisation des types anonymes  
 Avant de créer un objet en tant qu’instance d’une classe anonyme, déterminez s’il s’agit de la meilleure option. Par exemple, si vous souhaitez créer un objet temporaire pour contenir des données associées et que vous n’avez pas besoin d’autres champs et méthodes qu’une classe complète peut contenir, un type anonyme est une bonne solution. Les types anonymes sont également pratiques si vous souhaitez une sélection de propriétés différente pour chaque déclaration, ou si vous souhaitez modifier l’ordre des propriétés. Toutefois, si votre projet comprend plusieurs objets qui ont les mêmes propriétés, dans un ordre fixe, vous pouvez les déclarer plus facilement en utilisant un type nommé avec un constructeur de classe. Par exemple, avec un constructeur approprié, il est plus facile de déclarer plusieurs instances d’une `Product` classe que de déclarer plusieurs instances d’un type anonyme.  
  
 [!code-vb[VbVbalrAnonymousTypes#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#9)]  
  
 Un autre avantage des types nommés est que le compilateur peut intercepter une faute de frappe accidentelle d’un nom de propriété. Dans les exemples précédents, `firstProd2` , `secondProd2` et `thirdProd2` sont destinés à être des instances du même type anonyme. Toutefois, si vous deviez déclarer accidentellement de `thirdProd2` l’une des façons suivantes, son type serait différent de celui de `firstProd2` et `secondProd2` .  
  
 [!code-vb[VbVbalrAnonymousTypes#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class1.vb#10)]  
  
 Plus important encore, il existe des limitations sur l’utilisation de types anonymes qui ne s’appliquent pas aux instances de types nommés. `firstProd2`, `secondProd2` et `thirdProd2` sont des instances du même type anonyme. Toutefois, le nom du type anonyme partagé n’est pas disponible et ne peut pas apparaître lorsqu’un nom de type est attendu dans votre code. Par exemple, un type anonyme ne peut pas être utilisé pour définir une signature de méthode, pour déclarer une autre variable ou un autre champ, ou dans une déclaration de type. Par conséquent, les types anonymes ne sont pas appropriés lorsque vous devez partager des informations entre les méthodes.  
  
## <a name="an-anonymous-type-definition"></a>Définition de type anonyme  
 En réponse à la déclaration d’une instance d’un type anonyme, le compilateur crée une nouvelle définition de classe qui contient les propriétés spécifiées.  
  
 Si le type anonyme contient au moins une propriété de clé, la définition remplace trois membres hérités de <xref:System.Object> : <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> et <xref:System.Object.ToString%2A> . Le code produit pour tester l’égalité et déterminer la valeur de code de hachage ne prend en compte que les propriétés de clé. Si le type anonyme ne contient aucune propriété de clé, seul <xref:System.Object.ToString%2A> est substitué. Les propriétés explicitement nommées d’un type anonyme ne peuvent pas entrer en conflit avec ces méthodes générées. Autrement dit, vous ne pouvez pas utiliser `.Equals` , `.GetHashCode` ou `.ToString` pour nommer une propriété.  
  
 Les définitions de types anonymes qui ont au moins une propriété de clé implémentent également l' <xref:System.IEquatable%601?displayProperty=nameWithType> interface, où `T` est le type du type anonyme.  
  
 Pour plus d’informations sur le code créé par le compilateur et les fonctionnalités des méthodes substituées, consultez [définition de type anonyme](anonymous-type-definition.md).  
  
## <a name="see-also"></a>Voir aussi

- [Initialiseurs d'objets : types nommés et anonymes](object-initializers-named-and-anonymous-types.md)
- [Inférence de type local](../variables/local-type-inference.md)
- [Introduction à LINQ en Visual Basic](../linq/introduction-to-linq.md)
- [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Définition du type anonyme](anonymous-type-definition.md)
- [Clé](../../../language-reference/modifiers/key.md)
