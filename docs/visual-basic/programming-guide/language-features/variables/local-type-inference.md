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
ms.openlocfilehash: 786466cb0b94a96e629a1f173388ed7d40be7256
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661919"
---
# <a name="local-type-inference-visual-basic"></a>Inférence de type local (Visual Basic)
Le compilateur Visual Basic utilise *l’inférence de type* pour déterminer les types de données des variables locales déclarées sans un `As` clause. Le compilateur déduit le type de la variable du type de l’expression d’initialisation. Cela vous permet de déclarer des variables sans déclarer explicitement un type, comme illustré dans l’exemple suivant. À la suite les déclarations, les deux `num1` et `num2` sont fortement typées en tant qu’entiers.  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  Si vous ne souhaitez pas `num2` dans l’exemple précédent soit typée comme un `Integer`, vous pouvez spécifier un autre type à l’aide d’une déclaration telle que `Dim num3 As Object = 3` ou `Dim num4 As Double = 3`.  

> [!NOTE]
>  Inférence de type peut être utilisée uniquement pour les variables locales non statiques ; Il ne peut pas être utilisé pour déterminer le type des champs de classe, des propriétés ou des fonctions.
 
 Inférence de type local s’applique au niveau de la procédure. Il ne peut pas être utilisé pour déclarer des variables au niveau du module (au sein d’une classe, une structure, un module ou une interface, mais pas dans une procédure ou un bloc). Si `num2` dans l’exemple précédent ont un champ d’une classe au lieu d’une variable locale dans une procédure, la déclaration génère une erreur avec `Option Strict` et classifieriez `num2` comme un `Object` avec `Option Strict` désactivé. De même, l’inférence de type local ne s’applique pas aux variables de niveau procédure déclarées en tant que `Static`.  
  
## <a name="type-inference-vs-late-binding"></a>Visual Studio l’inférence de type. La liaison tardive  
 Code utilise l’inférence de type ressemble au code qui s’appuie sur la liaison tardive. Toutefois, l’inférence de type type fort à la variable au lieu de laisser en tant que `Object`. Le compilateur utilise l’initialiseur de variable pour déterminer le type de variable au moment de la compilation pour produire un code à liaison anticipée. Dans l’exemple précédent, `num2`, comme `num1`, est typé comme un `Integer`.  
  
 Le comportement des variables à liaison anticipée diffère de celui des variables à liaison tardive, dont le type est connu uniquement au moment de l’exécution. Connaître le type tôt permet au compilateur d’identifier les problèmes avant l’exécution, d’allouer la mémoire précisément et d’effectuer d’autres optimisations. Liaison anticipée permet également de l’environnement de développement intégré (IDE) pour fournir une aide IntelliSense sur les membres d’un objet Visual Basic. Liaison anticipée est également par défaut pour les performances. Il s’agit, car toutes les données stockées dans une variable à liaison tardive doivent être encapsulées en tant que type `Object`, ainsi que l’accès aux membres du type au moment de l’exécution ralentit le programme.  
  
## <a name="examples"></a>Exemples  
 Inférence de type se produit lorsqu’une variable locale est déclarée sans un `As` clause et initialisé. Le compilateur utilise le type de la valeur initiale assignée en tant que le type de la variable. Par exemple, chacune des lignes de code suivants déclare une variable de type `String`.  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 Le code suivant illustre deux méthodes pour créer un tableau d’entiers.  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 Il est pratique d’utiliser l’inférence de type pour déterminer le type d’une variable de contrôle de boucle. Dans le code suivant, le compilateur déduit que `number` est un `Integer` car `someNumbers2` à partir de l’exemple précédent est un tableau d’entiers.  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 Inférence de type local peut être utilisé dans `Using` instructions pour établir le type de nom de la ressource, comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 Le type d’une variable peut également être déduit à partir de valeurs de retour des fonctions, comme le montre l’exemple suivant. Les deux `pList1` et `pList2` sont des tableaux de processus, car `Process.GetProcesses` retourne un tableau de processus.  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a>Option Infer  
 `Option Infer` vous permet de que spécifier si l’inférence de type local est autorisée dans un fichier particulier. Pour activer ou bloquer l’option, tapez une des instructions suivantes au début du fichier.  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 Si vous ne spécifiez pas une valeur pour `Option Infer` dans votre code, la valeur par défaut du compilateur est `Option Infer On`. 
  
 Si la valeur définie pour `Option Infer` dans un fichier est en conflit avec la valeur définie dans l'IDE ou sur la ligne de commande, la valeur contenue dans le fichier est prioritaire.  
  
 Pour plus d’informations, consultez [Option Infer, instruction](../../../../visual-basic/language-reference/statements/option-infer-statement.md) et [Page Compiler, Concepteur de projets (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic).  
  
## <a name="see-also"></a>Voir aussi

- [Types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [Liaison anticipée et liaison tardive](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [For Each...Next (instruction)](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next (instruction)](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Option Infer (instruction)](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Introduction à LINQ en Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
