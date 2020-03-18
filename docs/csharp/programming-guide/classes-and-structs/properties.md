---
title: Propriétés - Guide de programmation C#
ms.date: 03/10/2017
f1_keywords:
- cs.properties
helpviewer_keywords:
- properties [C#]
- C# language, properties
ms.assetid: e295a8a2-b357-4ee7-a12e-385a44146fa8
ms.openlocfilehash: ee530e981e0c85302b2b11cc739d6c51d6650ddd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170102"
---
# <a name="properties-c-programming-guide"></a>Propriétés (Guide de programmation C#)

Une propriété est un membre qui fournit un mécanisme flexible pour la lecture, l'écriture ou le calcul de la valeur d'un champ privé. Les propriétés peuvent être utilisées comme s’il s’agissait de membres de données publics, mais ce sont en fait des méthodes spéciales appelées *accesseurs*. Elles permettent aux données d'être facilement accessibles tout en soutenant quand même la sécurité et la flexibilité des méthodes.  

## <a name="properties-overview"></a>Vue d’ensemble des propriétés  
  
- Les propriétés permettent à une classe d'exposer un moyen public d'obtenir et de définir des valeurs, tout en masquant le code d'implémentation ou de vérification.  
  
- Un accesseur de propriété [get](../../language-reference/keywords/get.md) est utilisé pour retourner la valeur de la propriété et un accesseur de propriété [set](../../language-reference/keywords/set.md) est utilisé pour affecter une nouvelle valeur. Ces accesseurs peuvent avoir différents niveaux d’accès. Pour plus d’informations, consultez [Restriction d’accessibilité de l’accesseur](./restricting-accessor-accessibility.md).  
  
- Le mot clé [value](../../language-reference/keywords/value.md) est utilisé pour définir la valeur assignée par l’accesseur `set`.  
- Les propriétés peuvent être *en lecture-écriture* (elles ont un accesseur `get` et un accesseur `set`), *en lecture seule* (elles ont un accesseur `get`, mais pas d’accesseur `set`) ou *en écriture seule* (elles ont un accesseur `set`, mais pas d’accesseur `get`). Les propriétés en écriture seule sont rares et sont généralement utilisées pour restreindre l’accès aux données sensibles.

- Les propriétés simples qui ne nécessitent pas de code d’accesseur personnalisé peuvent être implémentées en tant que définitions de corps d’expression ou en tant que [propriétés implémentées automatiquement](./auto-implemented-properties.md).

## <a name="properties-with-backing-fields"></a>Propriétés avec des champs de stockage

Un modèle de base pour l’implémentation d’une propriété consiste à utiliser un champ de stockage privé pour définir et extraire la valeur de propriété. L’accesseur `get` retourne la valeur du champ privé et l’accesseur `set` peut effectuer une validation des données avant d’assigner une valeur au champ privé. Les deux accesseurs peuvent également effectuer des opérations de conversion ou de calcul sur les données avant de stocker ou retourner les données.

L’exemple suivant illustre ce modèle. Dans cet exemple, la classe `TimePeriod` représente un intervalle de temps. La classe stocke l’intervalle de temps en secondes, en interne, dans un champ privé nommé `_seconds`. L’utilisateur peut éventuellement spécifier l’intervalle de temps en heures à l’aide de la propriété en lecture-écriture `Hours`. Les deux accesseurs de propriété `get` et `set` effectuent ensuite la conversion nécessaire des heures en secondes. De plus, l’accesseur `set` valide les données et lève une exception <xref:System.ArgumentOutOfRangeException> si le nombre d’heures n’est pas valide.

 [!code-csharp[Properties#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-1.cs)]  
  
## <a name="expression-body-definitions"></a>Définitions de corps d’expression  

 Les accesseurs de propriété sont souvent des instructions sur une ligne qui ne font qu’assigner ou retourner le résultat d’une expression. Vous pouvez implémenter ces propriétés en tant que membres expression-bodied. Les définitions de corps d’expression se composent du symbole `=>` suivi de l’expression à assigner à la propriété ou à récupérer de la propriété.

 À partir de C# 6, les propriétés en lecture seule peuvent implémenter l’accesseur `get` en tant que membre expression-bodied. Dans ce cas, le mot clé d’accesseur `get` et le mot clé `return` ne sont pas utilisés. L’exemple suivant implémente la propriété en lecture seule `Name` en tant que membre expression-bodied.

 [!code-csharp[Properties#2](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-2.cs)]  

 À compter de C# 7.0, les accesseurs `get` et `set` peuvent être implémentés comme membres expression-bodied. Dans ce cas, les mots clés `get` et `set` doivent être spécifiés. L’exemple suivant illustre l’utilisation de définitions de corps d’expression pour les deux accesseurs. Notez que le mot clé `return` n’est pas utilisé avec l’accesseur `get`.

  [!code-csharp[Properties#3](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-3.cs)]  

## <a name="auto-implemented-properties"></a>Propriétés implémentées automatiquement

Dans certains cas, les accesseurs de propriété `get` et `set` ne font qu’assigner une valeur à un champ de stockage, ou récupérer une valeur d’un champ de stockage, sans inclure de logique supplémentaire. En utilisant des propriétés implémentées automatiquement, vous simplifiez votre code, tout en laissant le compilateur C# fournir le champ de stockage de manière transparente.

Si une propriété a les accesseurs `get` et `set`, tous deux doivent être implémentés automatiquement. Vous définissez une propriété implémentée automatiquement à l’aide des mots clés `get` et `set` sans fournir d’implémentation. L’exemple suivant est identique à l’exemple précédent, sauf qu’il utilise les propriétés implémentées automatiquement `Name` et `Price`. Notez que l’exemple supprime également le constructeur paramétrable pour que les objets `SaleItem` soient initialisés avec un appel au constructeur sans paramètre et un [initialiseur d’objet](object-and-collection-initializers.md).

  [!code-csharp[Properties#4](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/properties-4.cs)]  

## <a name="related-sections"></a>Sections connexes  
  
- [Utilisation de propriétés](./using-properties.md)  
  
- [Propriété d’une interface](./interface-properties.md)  
  
- [Comparaison entre propriétés et indexeurs](../indexers/comparison-between-properties-and-indexers.md)  
  
- [Restriction d’accessibilité de l’accesseur](./restricting-accessor-accessibility.md)  
  
- [Propriétés implémentées automatiquement](./auto-implemented-properties.md)  
  
## <a name="c-language-specification"></a>Spécification du langage C#  

Pour plus d’informations, consultez [Propriétés](~/_csharplang/spec/classes.md#properties) dans la [spécification du langage C#](/dotnet/csharp/language-reference/language-specification/introduction). La spécification du langage est la source de référence pour la syntaxe C# et son utilisation.
  
## <a name="see-also"></a>Voir aussi

- [Guide de programmation C#](../index.md)
- [Utilisation de propriétés](./using-properties.md)
- [Indexeurs](../indexers/index.md)
- [get, mot clé](../../language-reference/keywords/get.md)
- [set, mot clé](../../language-reference/keywords/set.md)
