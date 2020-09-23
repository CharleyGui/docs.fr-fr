---
title: "Initialiseurs d'objets : types nommés et anonymes"
ms.date: 07/20/2015
f1_keywords:
- vb.ObjectInitializer
helpviewer_keywords:
- object initializers [Visual Basic]
- anonymous types [Visual Basic], object initializers
- initializing properties [Visual Basic]
- initializers [Visual Basic]
- named types [Visual Basic]
ms.assetid: e2df3807-a70f-49dd-ac94-f1e07f472b1b
ms.openlocfilehash: 724407fed5bf90ed6e3e470cbabc9e42856cb99a
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91087477"
---
# <a name="object-initializers-named-and-anonymous-types-visual-basic"></a>Initialiseurs d'objets : types nommés et anonymes (Visual Basic)

Les initialiseurs d’objets vous permettent de spécifier des propriétés pour un objet complexe à l’aide d’une expression unique. Elles peuvent être utilisées pour créer des instances de types nommés et de types anonymes.  
  
## <a name="declarations"></a>Déclarations  

 Les déclarations d’instances de types nommés et anonymes peuvent paraître presque identiques, mais leurs effets ne sont pas les mêmes. Chaque catégorie possède des capacités et des restrictions propres. L’exemple suivant montre un moyen pratique de déclarer et d’initialiser une instance d’une classe nommée, `Customer` , à l’aide d’une liste d’initialiseurs d’objets. Notez que le nom de la classe est spécifié après le mot clé `New` .  
  
 [!code-vb[VbVbalrObjectInit#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#1)]  
  
 Un type anonyme n’a pas de nom utilisable. Par conséquent, une instanciation d’un type anonyme ne peut pas inclure un nom de classe.  
  
 [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
 Les exigences et les résultats des deux déclarations ne sont pas identiques. Pour `namedCust` , une `Customer` classe qui a une `Name` propriété doit déjà exister, et la déclaration crée une instance de cette classe. Pour `anonymousCust` , le compilateur définit une nouvelle classe qui a une propriété, une chaîne appelée `Name` et crée une nouvelle instance de cette classe.  
  
## <a name="named-types"></a>Types nommés  

 Les initialiseurs d’objets fournissent un moyen simple d’appeler le constructeur d’un type, puis de définir les valeurs de certaines ou de toutes les propriétés dans une même instruction. Le compilateur appelle le constructeur approprié pour l’instruction : le constructeur sans paramètre si aucun argument n’est présenté, ou un constructeur paramétrable si un ou plusieurs arguments sont envoyés. Après cela, les propriétés spécifiées sont initialisées dans l’ordre dans lequel elles sont présentées dans la liste d’initialiseurs.  
  
 Chaque initialisation dans la liste d’initialiseurs se compose de l’assignation d’une valeur initiale à un membre de la classe. Les noms et types de données des membres sont déterminés lorsque la classe est définie. Dans les exemples suivants, la `Customer` classe doit exister et doit avoir des membres nommés `Name` et `City` qui peuvent accepter des valeurs de chaîne.  
  
 [!code-vb[VbVbalrObjectInit#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#3)]  
  
 Vous pouvez également obtenir le même résultat à l’aide du code suivant :  
  
 [!code-vb[VbVbalrObjectInit#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#4)]  
  
 Chacune de ces déclarations est équivalente à l’exemple suivant, qui crée un `Customer` objet à l’aide du constructeur sans paramètre, puis spécifie les valeurs initiales des `Name` Propriétés et à `City` l’aide d’une `With` instruction.  
  
 [!code-vb[VbVbalrObjectInit#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#5)]  
  
 Si la `Customer` classe contient un constructeur paramétrable qui vous permet d’envoyer une valeur pour `Name` , par exemple, vous pouvez également déclarer et initialiser un `Customer` objet des manières suivantes :  
  
 [!code-vb[VbVbalrObjectInit#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#6)]  
  
 Vous n’avez pas besoin d’initialiser toutes les propriétés, comme le montre le code suivant.  
  
 [!code-vb[VbVbalrObjectInit#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#7)]  
  
 Toutefois, la liste d’initialisation ne peut pas être vide. Les propriétés non initialisées conservent leurs valeurs par défaut.  
  
### <a name="type-inference-with-named-types"></a>Inférence de type avec des types nommés  

 Vous pouvez raccourcir le code pour la déclaration de `cust1` en combinant des initialiseurs d’objets et l’inférence de type local. Cela vous permet d’omettre la `As` clause dans la déclaration de la variable. Le type de données de la variable est déduit du type de l’objet créé par l’assignation. Dans l’exemple suivant, le type de `cust6` est `Customer` .  
  
 [!code-vb[VbVbalrObjectInit#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#8)]  
  
### <a name="remarks-about-named-types"></a>Remarques sur les types nommés  
  
- Un membre de classe ne peut pas être initialisé plus d’une fois dans la liste d’initialiseurs d’objets. La déclaration de `cust7` provoque une erreur.  
  
     [!code-vb[VbVbalrObjectInit#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#9)]  
  
- Un membre peut être utilisé pour s’initialiser lui-même ou un autre champ. Si vous accédez à un membre avant qu’il n’ait été initialisé, comme dans la déclaration suivante pour `cust8` , la valeur par défaut sera utilisée. N’oubliez pas que lorsqu’une déclaration qui utilise un initialiseur d’objet est traitée, la première chose qui se produit est que le constructeur approprié est appelé. Après cela, les champs individuels de la liste d’initialiseurs sont initialisés. Dans les exemples suivants, la valeur par défaut de `Name` est assignée pour `cust8` , et une valeur initialisée est assignée dans `cust9` .  
  
     [!code-vb[VbVbalrObjectInit#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#10)]  
  
     L’exemple suivant utilise le constructeur paramétrable de `cust3` et `cust4` pour déclarer et initialiser `cust10` et `cust11` .  
  
     [!code-vb[VbVbalrObjectInit#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#11)]  
  
- Les initialiseurs d’objets peuvent être imbriqués. Dans l’exemple suivant, `AddressClass` est une classe qui a deux propriétés, `City` et `State` , et la `Customer` classe a une `Address` propriété qui est une instance de `AddressClass` .  
  
     [!code-vb[VbVbalrObjectInit#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#12)]  
  
- La liste d’initialisation ne peut pas être vide.  
  
- L’instance en cours d’initialisation ne peut pas être de type Object.  
  
- Les membres de classe en cours d’initialisation ne peuvent pas être des membres partagés, des membres en lecture seule, des constantes ou des appels de méthode.  
  
- Les membres de classe en cours d’initialisation ne peuvent pas être indexés ou qualifiés. Les exemples suivants génèrent des erreurs du compilateur :  
  
     `'' Not valid.`  
  
     `' Dim c1 = New Customer With {.OrderNumbers(0) = 148662}`  
  
     `' Dim c2 = New Customer with {.Address.City = "Springfield"}`  
  
## <a name="anonymous-types"></a>Types anonymes  

 Les types anonymes utilisent des initialiseurs d’objets pour créer des instances de nouveaux types que vous ne définissez pas explicitement et que vous nommez. Au lieu de cela, le compilateur génère un type en fonction des propriétés que vous désignez dans la liste d’initialiseurs d’objets. Étant donné que le nom du type n’est pas spécifié, il est appelé *type anonyme*. Par exemple, comparez la déclaration suivante à la précédente pour `cust6` .  
  
 [!code-vb[VbVbalrObjectInit#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#13)]  
  
 La seule différence est qu’aucun nom n’est spécifié après `New` pour le type de données. Toutefois, ce qui se passe est assez différent. Le compilateur définit un nouveau type anonyme qui a deux propriétés, `Name` et `City` , et en crée une instance avec les valeurs spécifiées. L’inférence de type détermine les types de `Name` et `City` dans l’exemple comme des chaînes.  
  
> [!CAUTION]
> Le nom du type anonyme est généré par le compilateur et peut varier de la compilation à la compilation. Votre code ne doit pas utiliser ou s’appuyer sur le nom d’un type anonyme.  
  
 Étant donné que le nom du type n’est pas disponible, vous ne pouvez pas utiliser une `As` clause pour déclarer `cust13` . Son type doit être déduit. Sans utiliser la liaison tardive, cela limite l’utilisation des types anonymes aux variables locales.  
  
 Les types anonymes fournissent une prise en charge critique pour les requêtes LINQ. Pour plus d’informations sur l’utilisation de types anonymes dans les requêtes, consultez [types anonymes](anonymous-types.md) et [Introduction à LINQ dans Visual Basic](../linq/introduction-to-linq.md).  
  
### <a name="remarks-about-anonymous-types"></a>Remarques sur les types anonymes  
  
- En règle générale, la totalité ou la plupart des propriétés d’une déclaration de type anonyme sont des propriétés de clé, qui sont indiquées en tapant le mot clé `Key` devant le nom de la propriété.  
  
     [!code-vb[VbVbalrObjectInit#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#14)]  
  
     Pour plus d’informations sur les propriétés de clé, consultez [Key](../../../language-reference/modifiers/key.md).  
  
- Comme les types nommés, les listes d’initialiseurs pour les définitions de types anonymes doivent déclarer au moins une propriété.  
  
     [!code-vb[VbVbalrObjectInit#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#2)]  
  
- Quand une instance d’un type anonyme est déclarée, le compilateur génère une définition de type anonyme correspondante. Les noms et les types de données des propriétés sont extraits de la déclaration d’instance et sont inclus par le compilateur dans la définition. Les propriétés ne sont pas nommées et définies à l’avance, comme c’est le cas pour un type nommé. Leurs types sont déduits. Vous ne pouvez pas spécifier les types de données des propriétés à l’aide d’une `As` clause.  
  
- Les types anonymes peuvent également établir les noms et les valeurs de leurs propriétés de plusieurs autres façons. Par exemple, une propriété de type anonyme peut accepter à la fois le nom et la valeur d’une variable, ou le nom et la valeur d’une propriété d’un autre objet.  
  
     [!code-vb[VbVbalrObjectInit#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class1.vb#15)]  
  
     Pour plus d’informations sur les options permettant de définir des propriétés dans des types anonymes, consultez [Comment : déduire les types et les noms de propriétés dans des déclarations de type anonyme](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
## <a name="see-also"></a>Voir aussi

- [Inférence de type local](../variables/local-type-inference.md)
- [Types anonymes](anonymous-types.md)
- [Introduction à LINQ en Visual Basic](../linq/introduction-to-linq.md)
- [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
- [Clé](../../../language-reference/modifiers/key.md)
- [Comment : déclarer un objet à l'aide d'un initialiseur d'objet](how-to-declare-an-object-by-using-an-object-initializer.md)
