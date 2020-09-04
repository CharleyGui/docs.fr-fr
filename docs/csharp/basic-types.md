---
title: Types de base - Guide C#
description: Découvrez les types de base (numérique, chaîne et objet) disponibles dans tous les programmes C#
ms.date: 10/10/2016
ms.technology: csharp-fundamentals
ms.assetid: 95c686ba-ae4f-440e-8e94-0dbd6e04d11f
ms.openlocfilehash: 18a73e62bf45cdc4a4eaa0985c3fe036ac3b55a8
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465258"
---
# <a name="types-variables-and-values"></a>Types, variables et valeurs

C# est un langage fortement typé. Chaque variable et chaque constante ont un type, tout comme chaque expression qui fournit une valeur. Chaque signature de méthode spécifie un type pour chaque paramètre d’entrée et pour la valeur de retour. La bibliothèque de classes .NET définit un ensemble de types numériques intégrés, ainsi que des types plus complexes qui représentent un large éventail de constructions logiques, telles que le système de fichiers, les connexions réseau, les collections et tableaux d’objets, et les dates. Un programme C# classique utilise des types fournis dans la bibliothèque de classes, mais aussi des types définis par l’utilisateur qui modélisent les concepts propres au domaine du problème du programme.  
  
Un type peut stocker les informations suivantes :  
  
- Espace de stockage nécessaire pour une variable du type.  
  
- Valeurs minimale et maximale que le type peut représenter.  
  
- Membres (méthodes, champs, événements, etc.) que le type contient.  
  
- Type de base dont le type est hérité.  
  
- Emplacement où sera allouée la mémoire pour les variables au moment de l’exécution.  
  
- Sortes d’opérations autorisées.  
  
Le compilateur utilise les informations de type pour s’assurer que toutes les opérations qui sont effectuées dans votre code sont de *type safe*. Par exemple, si vous déclarez une variable de type [int](language-reference/builtin-types/integral-numeric-types.md), le compilateur vous permet d’utiliser la variable dans des opérations d’addition et de soustraction. Si vous essayez d’effectuer ces mêmes opérations avec une variable de type [bool](language-reference/builtin-types/bool.md), le compilateur génère une erreur, comme illustré dans l’exemple suivant :  
  
[!code-csharp[Type Safety](../../samples/snippets/csharp/concepts/basic-types/type-safety.cs)]  
  
> [!NOTE]  
> Développeurs C et C++ : notez que dans C#, [bool](language-reference/builtin-types/bool.md) n’est pas convertible en [int](language-reference/builtin-types/integral-numeric-types.md).  
  
Le compilateur incorpore les informations de type dans le fichier exécutable sous forme de métadonnées. Le common language runtime (CLR) utilise ces métadonnées au moment de l’exécution pour garantir que le type est sécurisé lorsqu’il alloue et libère de la mémoire.  

## <a name="specifying-types-in-variable-declarations"></a>Spécification de types dans les déclarations de variable

Lorsque vous déclarez une variable ou une constante dans un programme, vous devez spécifier son type ou utiliser le mot clé [var](language-reference/keywords/var.md) pour permettre au compilateur de déduire le type. L’exemple suivant montre des déclarations de variable qui utilisent des types numériques intégrés et des types complexes définis par l’utilisateur :  
  
[!code-csharp[Variable Declaration](../../samples/snippets/csharp/concepts/basic-types/variable-declaration.cs)]  
  
Les types de paramètres de méthode et de valeurs de retour sont spécifiés dans la signature de méthode. La signature suivante présente une méthode qui requiert [int](language-reference/builtin-types/integral-numeric-types.md) comme argument d’entrée et retourne une chaîne :  
  
[!code-csharp[Method Signature](../../samples/snippets/csharp/concepts/basic-types/method-signature.cs)]  
  
Après qu’une variable est déclarée, elle ne peut pas être déclarée de nouveau avec un nouveau type et elle ne peut pas être définie sur une valeur qui n’est pas compatible avec son type déclaré. Par exemple, vous ne pouvez pas déclarer un [int](language-reference/builtin-types/integral-numeric-types.md) et lui assigner une valeur booléenne `true` . Toutefois, les valeurs peuvent être converties en d’autres types, par exemple, quand elles sont assignées à de nouvelles variables ou passées comme arguments de méthode. Une *conversion de type* qui ne cause pas de perte de données est effectuée automatiquement par le compilateur. Une conversion susceptible de causer la perte de données exige une variable *cast* dans le code source.

Pour plus d’informations, consultez [Cast et conversions de types](programming-guide/types/casting-and-type-conversions.md).

## <a name="built-in-types"></a>Types intégrés

C# fournit un jeu standard de types numériques intégrés pour représenter les nombres entiers, les valeurs à virgule flottante, les expressions booléennes, les caractères de texte, les valeurs décimales et d’autres types de données. Il existe également des types **string** et **object** intégrés, que vous pouvez utiliser dans n’importe quel programme C#. Pour obtenir la liste complète des types intégrés, consultez [types intégrés](language-reference/builtin-types/built-in-types.md).
  
## <a name="custom-types"></a>Types personnalisés

Vous utilisez les constructions [struct](language-reference/builtin-types/struct.md), [classe](language-reference/keywords/class.md), [interface](language-reference/keywords/interface.md) et [enum](language-reference/builtin-types/enum.md) pour créer vos propres types personnalisés. La bibliothèque de classes .NET est une collection de types personnalisés fournie par Microsoft que vous pouvez utiliser dans vos propres applications. Par défaut, les types les plus fréquemment utilisés dans la bibliothèque de classes sont disponibles dans tous les programmes C#. Les autres types sont disponibles uniquement si vous ajoutez explicitement une référence de projet à l’assembly dans lequel ils sont définis. Une fois que le compilateur a une référence à l’assembly, vous pouvez déclarer des variables (et des constantes) des types déclarés dans cet assembly dans le code source.
  
## <a name="generic-types"></a>Types génériques

Un type peut être déclaré avec un ou plusieurs *paramètres de type* qui servent d’espace réservé pour le type réel (le *type concret*) que le code client fournit lorsqu’il crée une instance du type. Ces types sont appelés *types génériques*. Par exemple, <xref:System.Collections.Generic.List%601> a un paramètre de type qui, par Convention, reçoit le nom *T*. Lorsque vous créez une instance du type, vous spécifiez le type des objets que la liste doit contenir, par exemple String :  
  
[!code-csharp[Generic types](../../samples/snippets/csharp/concepts/basic-types/generic-type.cs)]
  
L’utilisation du paramètre de type rend possible la réutilisation de la même classe pour contenir tout type d’élément, sans avoir à convertir chaque élément en [object](language-reference/builtin-types/reference-types.md#the-object-type). Les classes de collection génériques sont appelées *collections fortement typées* , car le compilateur connaît le type spécifique des éléments de la collection et peut déclencher une erreur au moment de la compilation si, par exemple, vous tentez d’ajouter un entier à l' `strings` objet dans l’exemple précédent. Pour plus d’informations, consultez [Génériques](programming-guide/generics/index.md).

## <a name="implicit-types-anonymous-types-and-tuple-types"></a>Types implicites, types anonymes et types tuple

Comme indiqué précédemment, vous pouvez attribuer implicitement un type à une variable locale (mais pas les membres de la classe) à l’aide du mot clé [var](language-reference/keywords/var.md). La variable reçoit toujours un type au moment de la compilation, mais le type est fourni par le compilateur. Pour plus d’informations, consultez [variables locales implicitement typées](programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
Dans certains cas, il est difficile de créer un type nommé pour des ensembles simples de valeurs associées que vous ne souhaitez pas stocker ou transférer en dehors des limites de la méthode. Vous pouvez alors créer des *types anonymes*. Pour plus d’informations, consultez [types anonymes](programming-guide/classes-and-structs/anonymous-types.md).

Il est courant de vouloir retourner plusieurs valeurs d’une méthode. Vous pouvez créer des *types tuple* qui retournent plusieurs valeurs dans un seul appel de méthode. Pour plus d’informations, consultez [types de tuples](language-reference/builtin-types/value-tuples.md).

## <a name="the-common-type-system"></a>Système de type commun (CTS)

Il est important de comprendre deux points fondamentaux à propos du système de type dans le .NET :  
  
- Il prend en charge le principe d’héritage. Les types peuvent dériver d’autres types, appelés *types de base*. Le type dérivé hérite (avec certaines restrictions) des méthodes, des propriétés et des autres membres du type de base. Le type de base peut à son tour dériver d’un autre type, auquel cas le type dérivé hérite des membres des deux types de base dans sa hiérarchie d’héritage. Tous les types, y compris les types numériques intégrés tels que <xref:System.Int32> (mot clé C# : `int`), dérivent au final d’un seul type de base, qui est <xref:System.Object> (mot clé C# : `object`). Cette hiérarchie de types unifiée est appelée système de type commun (CTS, [Common type System](../standard/common-type-system.md) ). Pour plus d’informations sur l’héritage dans C#, consultez [Héritage](programming-guide/classes-and-structs/inheritance.md).  
  
- Chaque type du CTS est défini comme *type valeur* ou *type référence*. Cela inclut tous les types personnalisés dans la bibliothèque de classes .NET, ainsi que les types définis par l’utilisateur. Les types que vous définissez à l’aide du `struct` `enum` mot clé ou sont des types valeur. Pour plus d’informations sur les types valeur, consultez [types valeur](language-reference/builtin-types/value-types.md). Les types que vous définissez à l’aide du mot clé [class](language-reference/keywords/class.md) sont des types référence. Pour plus d’informations sur les types référence, consultez [Classes](programming-guide/classes-and-structs/classes.md). Les types référence et les types valeur ne suivent pas les mêmes règles de compilation et ont un comportement différent au moment de l’exécution.

## <a name="see-also"></a>Voir aussi

- [Types de structure](language-reference/builtin-types/struct.md)
- [Types d'énumération](language-reference/builtin-types/enum.md)
- [Classes](programming-guide/classes-and-structs/classes.md)
