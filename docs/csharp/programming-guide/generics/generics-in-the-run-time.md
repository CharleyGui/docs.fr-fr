---
title: Génériques dans le runtime - Guide de programmation C#
description: En savoir plus sur les types génériques au moment de l’exécution. Consultez des exemples de code et affichez des ressources disponibles supplémentaires.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: 8e072e7aa53177929dda0be931beb85863b6a12e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299225"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Génériques dans le runtime (Guide de programmation C#)
Quand une méthode ou un type générique est compilé dans le langage intermédiaire Microsoft (MSIL), il ou elle contient des métadonnées qui l’identifient comme ayant des paramètres de type. La façon dont le langage MSIL d’un type générique est utilisé diffère selon que le paramètre de type fourni est un type valeur ou référence.  
  
 Quand un type générique est construit en premier avec un type valeur comme paramètre, le runtime crée un type générique spécialisé avec le paramètre fourni ou les paramètres substitués aux emplacements appropriés dans le langage MSIL. Des types génériques spécialisés sont créés une fois pour chaque type valeur unique qui est utilisé comme paramètre.  
  
 Par exemple, supposons que votre code de programme ait déclaré une pile construite d’entiers :  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 À ce stade, le runtime génère une version spécialisée de la classe <xref:System.Collections.Generic.Stack%601> dont l’entier a été substitué correctement à son paramètre. Maintenant, chaque fois que le code de programme utilise une pile d’entiers, le runtime réutilise la classe <xref:System.Collections.Generic.Stack%601> spécialisée générée. Dans l’exemple suivant, deux instances d’une pile d’entiers sont créées, et elles partagent une instance unique du code `Stack<int>` :  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Toutefois, supposons qu’une autre classe <xref:System.Collections.Generic.Stack%601> avec un type valeur différent tel qu’un type `long` ou une structure définie par l’utilisateur comme son paramètre est créée à un autre endroit dans votre code. Le runtime génère alors une autre version du type générique et substitue un type `long` aux emplacements appropriés dans le langage MSIL. Les conversions ne sont plus nécessaires parce que chaque classe générique spécialisée contient le type valeur en mode natif.  
  
 Les génériques fonctionnent un peu différemment pour les types référence. La première fois qu’un type générique est construit avec un type référence quelconque, le runtime crée un type générique spécialisé avec les références d’objet substituées aux paramètres dans le langage MSIL. Ensuite, chaque fois qu’un type construit est instancié avec un type référence comme son paramètre, indépendamment de son type, le runtime réutilise la version spécialisée créée précédemment pour le type générique. Ceci est possible parce que toutes les références ont la même taille.  
  
 Par exemple, supposons que vous ayez deux types référence, une classe `Customer` et une classe `Order`, et supposons également que vous ayez créé une pile de types `Customer` :  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 À ce stade, le runtime génère une version spécialisée de la classe <xref:System.Collections.Generic.Stack%601> qui stocke des références d’objet qui seront remplies ultérieurement au lieu de stocker des données. Supposons que la ligne de code suivante crée une pile d’un autre type référence, qui est nommé `Order` :  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 Contrairement aux types valeur, une autre version spécialisée de la classe <xref:System.Collections.Generic.Stack%601> n’est pas créée pour le type `Order`. À la place, une instance de la version spécialisée de la classe <xref:System.Collections.Generic.Stack%601> est créée et la variable `orders` est définie pour la référencer. Supposons que vous ayez rencontré ensuite une ligne de code pour créer une pile d’un type `Customer` :  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 Comme avec l’utilisation précédente de la classe <xref:System.Collections.Generic.Stack%601> créée à l’aide du type `Order`, une autre instance de la classe <xref:System.Collections.Generic.Stack%601> spécialisée est créée. Les pointeurs contenus ici sont configurés pour référencer une zone de mémoire de la taille d’un type `Customer`. Dans la mesure où le nombre de types référence peut varier de manière importante d’un programme à l’autre, l’implémentation C# de génériques réduit sensiblement le volume du code en ramenant à une unité le nombre de classes spécialisées créées par le compilateur pour les classes génériques de types référence.  
  
 De plus, quand une classe C# générique est instanciée à l’aide d’un paramètre de type valeur ou référence, la réflexion peut l’interroger au moment de l’exécution, et son type réel ainsi que son paramètre de type peuvent être vérifiés.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Collections.Generic>
- [Guide de programmation C#](../index.md)
- [Introduction aux génériques](./index.md)
- [Génériques](../../../standard/generics/index.md)
