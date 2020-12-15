---
title: Guide pratique pour initialiser un dictionnaire avec un initialiseur de collection - Guide de programmation C#
description: Découvrez comment initialiser un dictionnaire en C#, à l’aide de la méthode Add ou d’un initialiseur d’index. Cet exemple montre les deux options.
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: bcb9c5af215ff468812d08e93d37eecc40d745ea
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513079"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Guide pratique pour initialiser un dictionnaire avec un initialiseur de collection (Guide de programmation C#)

Un <xref:System.Collections.Generic.Dictionary%602> contient une collection de paires clé/valeur. Sa méthode <xref:System.Collections.Generic.Dictionary%602.Add%2A> prend deux paramètres, un pour la clé et un pour la valeur. Une façon d’initialiser un <xref:System.Collections.Generic.Dictionary%602> ou toute collection dont la méthode `Add` prend plusieurs paramètres consiste à mettre chaque jeu de paramètres entre accolades, comme illustré dans l’exemple suivant. Une autre option consiste à utiliser un initialiseur d’index, également illustré dans l’exemple suivant.

## <a name="example"></a>Exemple

Dans l’exemple de code suivant, un <xref:System.Collections.Generic.Dictionary%602> est initialisé avec des instances de type `StudentName`.  La première initialisation utilise la méthode `Add` avec deux arguments. Le compilateur génère un appel à `Add` pour chacune des paires de clés `int` et de valeurs `StudentName`. Le deuxième utilise une méthode d’indexeur publique en lecture/écriture de la classe `Dictionary` :

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Notez les deux paires d’accolades dans chaque élément de la collection dans la première déclaration. Les accolades les plus à l’intérieur encadrent l’initialiseur d’objet pour le `StudentName` , et les accolades les plus extérieures encadrent l’initialiseur pour la paire clé/valeur qui sera ajoutée à `students` <xref:System.Collections.Generic.Dictionary%602> . Pour finir, l’initialiseur de collection entier pour le dictionnaire est placé entre accolades. Dans la deuxième initialisation, le côté gauche de l’affectation est la clé et le côté droit est la valeur, avec un initialiseur d’objet pour `StudentName`.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Initialiseurs d’objets et de collections](./object-and-collection-initializers.md)
