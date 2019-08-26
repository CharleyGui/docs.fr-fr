---
title: Guide pratique pour initialiser un dictionnaire avec un initialiseur de collection - Guide de programmation C#
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 22f80365b974df66999ac68f7bc2a9ffa7d445a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596819"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Guide pratique pour initialiser un dictionnaire avec un initialiseur de collection (Guide de programmation C#)

Un <xref:System.Collections.Generic.Dictionary%602> contient une collection de paires clé/valeur. Sa méthode <xref:System.Collections.Generic.Dictionary%602.Add*> prend deux paramètres, un pour la clé et un pour la valeur. Une façon d’initialiser un <xref:System.Collections.Generic.Dictionary%602> ou toute collection dont la méthode `Add` prend plusieurs paramètres consiste à mettre chaque jeu de paramètres entre accolades, comme illustré dans l’exemple suivant. Une autre option consiste à utiliser un initialiseur d’index, également illustré dans l’exemple suivant.

## <a name="example"></a>Exemples

Dans l’exemple de code suivant, un <xref:System.Collections.Generic.Dictionary%602> est initialisé avec des instances de type `StudentName`.  La première initialisation utilise la méthode `Add` avec deux arguments. Le compilateur génère un appel à `Add` pour chacune des paires de clés `int` et de valeurs `StudentName`. Le deuxième utilise une méthode d’indexeur publique en lecture/écriture de la classe `Dictionary` :

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Notez les deux paires d’accolades dans chaque élément de la collection dans la première déclaration. Les accolades les plus intérieures encadrent l’initialiseur d’objet pour `StudentName`, et les accolades les plus extérieures encadrent l’initialiseur pour la paire clé/valeur ajoutée à `students` <xref:System.Collections.Generic.Dictionary%602>. Pour finir, l’initialiseur de collection entier pour le dictionnaire est placé entre accolades. Dans la deuxième initialisation, le côté gauche de l’affectation est la clé et le côté droit est la valeur, avec un initialiseur d’objet pour `StudentName`.

## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Initialiseurs d’objets et de collections](./object-and-collection-initializers.md)
