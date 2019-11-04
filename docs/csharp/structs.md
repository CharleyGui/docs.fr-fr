---
title: Structs - Guide C#
description: En savoir plus sur le type struct et la manière de le créer
ms.date: 10/12/2016
ms.technology: csharp-fundamentals
ms.assetid: a7094b8c-7229-4b6f-82fc-824d0ea0ec40
ms.openlocfilehash: 10971dc1a0b2c9d64ac8766734b3f6f630aa3ccf
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423116"
---
# <a name="structs"></a>Structures

Un *struct* est un type valeur. Lorsqu'un struct est créé, la variable à laquelle le struct est assigné contient les données réelles du struct. Lorsque le struct est affecté à une nouvelle variable, il est copié. La nouvelle variable et la variable d’origine contiennent par conséquent deux copies distinctes des mêmes données. Les modifications apportées à une copie n’affectent pas l’autre copie.

Les variables de type valeur contiennent directement leurs valeurs, ce qui signifie que la mémoire est allouée inline dans le contexte où la variable est déclarée. Aucune allocation des tas ni surcharge de garbage collection distincte n’a lieu pour les variables de type valeur.  
  
Il existe deux catégories de types valeur : [struct](./language-reference/keywords/struct.md) et [enum](./language-reference/keywords/enum.md).  
  
Les types numériques intégrés sont des structs et disposent de propriétés et de méthodes auxquelles vous pouvez accéder :  
  
[!code-csharp[Static Method](../../samples/snippets/csharp/concepts/structs/static-method.cs)]
  
Mais vous les déclarez et leur affectez des valeurs comme s’ils étaient de simples types non agrégés :  
  
[!code-csharp[Assign Values](../../samples/snippets/csharp/concepts/structs/assign-value.cs)] 
  
Les types valeur sont scellés (*sealed*), ce qui signifie que par exemple que vous ne pouvez pas dériver un type de <xref:System.Int32>. Vous ne pouvez pas non plus définir un struct pour qu’il hérite d’une classe ou d’un struct défini par l’utilisateur car un struct peut uniquement hériter de <xref:System.ValueType>. Toutefois, un struct peut implémenter une ou plusieurs interfaces. Vous pouvez effectuer un cast d’un type struct en un type interface. En conséquence, une opération de *boxing* encapsule le struct dans un objet de type référence sur le tas managé. Les opérations de boxing surviennent lorsque vous passez un type valeur à une méthode qui accepte un <xref:System.Object> comme paramètre d’entrée. Pour plus d’informations, consultez [Conversion boxing et unboxing](./programming-guide/types/boxing-and-unboxing.md ).  
  
Vous utilisez le mot clé [struct](./language-reference/keywords/struct.md) pour créer vos propres types valeur personnalisés. En règle générale, un struct est utilisé comme conteneur pour un petit jeu de variables connexes, comme le montre l'exemple suivant :  
  
[!code-csharp[Struct Keyword](../../samples/snippets/csharp/concepts/structs/struct-keyword.cs)]  
  
Pour plus d’informations sur les types valeur dans le .NET Framework, consultez [Système de type commun (CTS, Common Type System)](../standard/common-type-system.md).  
    
Les structs partagent presque tous la même syntaxe que les classes, bien qu'ils soient plus limités que ces dernières :  
  
- Au sein d’une déclaration de struct, les champs ne peuvent pas être initialisés à moins d’être déclarés `const` ou `static`.  
  
- Un struct ne peut pas déclarer de constructeur sans paramètre ni de finaliseur.  
  
- Les structs sont copiés lors de l'assignation. Lorsqu'un struct est assigné à une nouvelle variable, toutes les données sont copiées et les modifications apportées à la nouvelle copie ne changent pas les données de la copie d'origine. Il est important de s’en souvenir lors de l’utilisation de collections de types valeur telles que Dictionary<string, myStruct>.  
  
- Les structs sont des types valeur et les classes des types référence.  
  
- Contrairement aux classes, il est possible d’instancier les structs sans avoir recours à un opérateur `new`.  
  
- Les structs peuvent déclarer des constructeurs qui ont des paramètres.  
  
- Un struct ne peut pas hériter d'un autre struct ou d'une classe ; il ne peut pas non plus servir de base à une classe. Tous les structs héritent directement de <xref:System.ValueType>, qui hérite de <xref:System.Object>.  
  
- Un struct peut implémenter des interfaces.

## <a name="literal-values"></a>Valeurs littérales

Dans C#, les valeurs littérales reçoivent un type du compilateur. Vous pouvez spécifier la façon dont un littéral numérique doit être typé en ajoutant une lettre à la fin du nombre. Par exemple, pour spécifier que la valeur 4,56 doit être traitée comme une valeur float, ajoutez « f » ou « F » après le nombre : `4.56f`. Si aucune lettre n’est ajoutée, le compilateur déduit le type `double` pour le littéral. Pour plus d’informations sur les types qui peuvent être spécifiés avec une lettre en suffixe, consultez les pages de référence des différents types dans [Types valeur](./language-reference/keywords/value-types.md).  
  
Comme les littéraux sont typés et que tous les types dérivent en fin de compte de <xref:System.Object>, vous pouvez écrire et compiler du code, tel que le suivant :  
  
[!code-csharp[Literal Values](../../samples/snippets/csharp/concepts/structs/literals.cs)]

Les deux derniers exemples illustrent les fonctionnalités de langage introduites dans C# 7.0. Le premier vous permet d’utiliser un caractère de soulignement comme *séparateur numérique* au sein des littéraux numériques. Vous pouvez les placer où vous le souhaitez entre les chiffres pour améliorer la lisibilité. Ils n’ont aucun effet sur la valeur.

Le second illustre les *littéraux binaires*, qui vous permettent de spécifier des modèles de bits directement au lieu d’utiliser la notation hexadécimale.

## <a name="nullable-value-types"></a>Types valeur Nullable

Les types valeur ordinaires ne peuvent pas avoir la valeur [Null](language-reference/keywords/null.md). Toutefois, vous pouvez créer des types valeur Nullable en apposant un `?` après le type. Par exemple, `int?` est un type `int` qui peut également avoir la valeur [null](./language-reference/keywords/null.md). Les types valeur Nullable sont des instances du type struct générique <xref:System.Nullable%601>. Les types valeur Nullable sont particulièrement utiles lorsque vous passez des données vers et depuis des bases de données dans lesquelles les valeurs numériques peuvent être null ou non définies. Pour plus d’informations, consultez [types valeur Nullable](programming-guide/nullable-types/index.md).

## <a name="see-also"></a>Voir aussi

- [Classes](programming-guide/classes-and-structs/classes.md)
- [Types de base](basic-types.md)
