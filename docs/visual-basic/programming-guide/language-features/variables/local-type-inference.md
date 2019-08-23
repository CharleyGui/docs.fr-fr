---
title: Inférence de type local (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: 59559f8775a5fd66a567897b009272df1727b1e8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953330"
---
# <a name="local-type-inference-visual-basic"></a>Inférence de type local (Visual Basic)
Le compilateur Visual Basic utilise l’inférence de *type* pour déterminer les types de données des variables locales `As` déclarées sans clause. Le compilateur déduit le type de la variable à partir du type de l’expression d’initialisation. Cela vous permet de déclarer des variables sans déclarer explicitement un type, comme indiqué dans l’exemple suivant. À la suite des déclarations, `num1` et `num2` sont fortement typées en tant qu’entiers.  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
> Si vous ne `num2` souhaitez pas que dans l’exemple précédent soit tapé comme un `Integer`, vous pouvez spécifier un autre type à l’aide d’une déclaration comme `Dim num3 As Object = 3` ou `Dim num4 As Double = 3`.  

> [!NOTE]
> L’inférence de type ne peut être utilisée que pour les variables locales non statiques; elle ne peut pas être utilisée pour déterminer le type des champs de classe, des propriétés ou des fonctions.
 
 L’inférence de type local s’applique au niveau de la procédure. Elle ne peut pas être utilisée pour déclarer des variables au niveau du module (dans une classe, une structure, un module ou une interface, mais pas dans une procédure ou un bloc). Si `num2` , dans l’exemple précédent, était un champ d’une classe au lieu d’une variable locale dans une procédure, la déclaration provoquerait `Option Strict` une erreur avec on `Object` et `num2` classifierait comme `Option Strict` with OFF. De même, l’inférence de type local ne s’applique pas aux variables de `Static`niveau procédure déclarées comme.  
  
## <a name="type-inference-vs-late-binding"></a>Inférence de type et Liaison tardive  
 Le code qui utilise l’inférence de type ressemble au code qui s’appuie sur la liaison tardive. Toutefois, l’inférence de type type fortement la variable au lieu de `Object`la laisser en tant que. Le compilateur utilise l’initialiseur d’une variable pour déterminer le type de la variable au moment de la compilation pour produire du code à liaison anticipée. Dans l’exemple précédent, `num2`, comme `num1` `Integer`, est de type.  
  
 Le comportement des variables à liaison anticipée diffère de celui des variables à liaison tardive, pour lesquelles le type est connu uniquement au moment de l’exécution. La connaissance du type le plus tôt permet au compilateur d’identifier les problèmes avant leur exécution, d’allouer de la mémoire avec précision et d’effectuer d’autres optimisations. La liaison précoce permet également au Visual Basic environnement de développement intégré (IDE) de fournir une aide IntelliSense sur les membres d’un objet. La liaison précoce est également préférable pour les performances. Cela est dû au fait que toutes les données stockées dans une variable à liaison tardive doivent `Object`être encapsulées en tant que type et que l’accès aux membres du type au moment de l’exécution rend le programme plus lent.  
  
## <a name="examples"></a>Exemples  
 L’inférence de type se produit lorsqu’une variable locale est `As` déclarée sans clause et initialisée. Le compilateur utilise le type de la valeur initiale affectée comme type de la variable. Par exemple, chacune des lignes de code suivantes déclare une variable de type `String`.  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 Le code suivant illustre deux façons équivalentes de créer un tableau d’entiers.  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 Il est pratique d’utiliser l’inférence de type pour déterminer le type d’une variable de contrôle de boucle. Dans le code suivant, le compilateur déduit que `number` est un `Integer` , car `someNumbers2` dans l’exemple précédent, il s’agit d’un tableau d’entiers.  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 L’inférence de type local peut être `Using` utilisée dans les instructions pour établir le type du nom de la ressource, comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 Le type d’une variable peut également être déduit à partir des valeurs de retour des fonctions, comme le montre l’exemple suivant. Et sont des tableaux de processus, car `Process.GetProcesses` retourne un tableau de processus. `pList2` `pList1`  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer`vous permet de spécifier si l’inférence de type local est autorisée dans un fichier particulier. Pour activer ou bloquer l’option, tapez l’une des instructions suivantes au début du fichier.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 Si vous ne spécifiez pas de valeur `Option Infer` pour dans votre code, la valeur par `Option Infer On`défaut du compilateur est. 
  
 Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur contenue dans le fichier est prioritaire.  
  
 Pour plus d’informations, consultez [instruction Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) et [page compiler, concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Voir aussi

- [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Liaison anticipée et liaison tardive](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [For Each...Next (instruction)](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next (instruction)](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Option Infer (instruction)](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
