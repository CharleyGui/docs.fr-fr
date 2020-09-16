---
title: Concepts et terminologie (transformation fonctionnelle)-LINQ to XML
description: Découvrez les concepts et la terminologie des transformations fonctionnelles pures.
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: 0ecdbdf88ee9f868143f466222fa06f0ccf641d8
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558110"
---
# <a name="concepts-and-terminology-functional-transformation-linq-to-xml"></a>Concepts et terminologie (transformation fonctionnelle) (LINQ to XML)

Cet article présente les concepts et la terminologie des transformations fonctionnelles pures. L’approche de transformation fonctionnelle de la transformation des données génère du code qui est souvent plus rapide à programmer, plus expressif et plus facile à déboguer et à gérer que la programmation impérative, plus traditionnelle.

Notez que les Articles de cette section ne sont pas destinés à expliquer en détail la programmation fonctionnelle. Au lieu de cela, ces articles identifient certaines des capacités de programmation fonctionnelle qui facilitent la transformation du code XML d’une forme en une autre.

## <a name="what-is-pure-functional-transformation"></a>Qu’est-ce que la transformation fonctionnelle pure ?

Dans la *transformation fonctionnelle pure*, un ensemble de fonctions, appelées *fonctions pures*, indiquent comment transformer un ensemble de données structurées de leur forme d’origine en une autre forme. Le mot « pure » indique que les fonctions sont *composables*, ce qui exige qu’elles soient :

- *Être autonomes*, de manière à pouvoir être librement ordonnées et réorganisées sans enchevêtrement ni interdépendance avec le reste du programme. Les transformations pures n'ont aucune connaissance de leur environnement et aucun effet sur lui. Autrement dit, les fonctions utilisées dans la transformation n’ont pas d’*effets secondaires*.
- *Être sans état*, de sorte que l’exécution de la même fonction ou du même ensemble spécifique de fonctions sur la même entrée générera toujours le même résultat. Les transformations pures n'ont pas de mémoire de leur utilisation antérieure.

> [!IMPORTANT]
> Dans le reste de ce didacticiel, le terme « fonction pure » est utilisé dans un sens général pour indiquer une approche de programmation, et non une fonctionnalité de langage spécifique.
>
> Notez que les fonctions pures doivent être implémentées en tant que méthodes en C# et en tant que fonctions dans Visual Basic.
>
> Vous ne devez pas confondre les fonctions pures avec les méthodes virtuelles pures en C++. Ces dernières indiquent que la classe conteneur est abstraite et qu'aucun corps de méthode n'est fourni.

### <a name="functional-programming"></a>Programmation fonctionnelle

La *programmation fonctionnelle* est une approche de programmation prenant directement en charge la transformation fonctionnelle pure.

Historiquement, les langages de programmation fonctionnelle à usage général, tels que ML, Scheme, Haskell et F#, ont toujours essentiellement intéressé la communauté liée au monde de l’enseignement et de la recherche. Même s'il a toujours été possible d'écrire des transformations fonctionnelles pures en C# et Visual Basic, la difficulté de cette opération a toujours découragé la plupart des programmeurs. Dans les versions récentes de ces langages, toutefois, de nouvelles constructions de langage telles que les expressions lambda et l’inférence de type rendent la programmation fonctionnelle beaucoup plus simple et plus productive.

Pour plus d’informations sur la programmation fonctionnelle, consultez [programmation fonctionnelle et programmation impérative](functional-vs-imperative-programming.md).

#### <a name="domain-specific-functional-programming-languages"></a>Langages de programmation fonctionnelle spécifiques à un domaine

Bien que les langages de programmation fonctionnelle généraux n’aient pas été adoptés à grande échelle, certains langages de programmation fonctionnelle spécifiques au domaine ont eu un meilleur succès. Par exemple, les feuilles de style en cascade (CSS) sont utilisées pour déterminer l’apparence de nombreuses pages Web et les feuilles de style XSLT (Extensible Stylesheet Language Transformations) sont largement utilisées dans la manipulation de données XML. Pour plus d’informations sur XSLT, consultez [Transformations XSLT](../data/xml/xslt-transformations.md).

## <a name="terminology"></a>Terminologie

La liste suivante définit certains termes liés aux transformations fonctionnelles.

fonction d’ordre supérieur (première classe) \
Fonction qui peut être traitée en tant qu'objet de programmation. Par exemple, une fonction d'ordre supérieur peut être passée à ou retournée à partir d'autres fonctions. En C# et Visual Basic, les délégués et les expressions lambda sont des fonctionnalités qui prennent en charge les fonctions d’ordre supérieur. Pour écrire une fonction d’ordre supérieur, vous déclarez un ou plusieurs arguments pour prendre des délégués et vous utilisez souvent des expressions lambda lorsque vous appelez votre fonction. Une grande partie des opérateurs de requête standard sont des fonctions d'ordre supérieur.

Pour plus d’informations, consultez [vue d’ensemble des opérateurs de requête standard (C#)](../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md) et [vue d’ensemble des opérateurs de requête standard (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

expression lambda \
Pour l'essentiel, il s'agit d'une fonction anonyme inline qui peut être utilisée partout où un type délégué est attendu. Il s’agit d’une définition simplifiée des expressions lambda, mais elle est adaptée aux objectifs de ce didacticiel.

Pour plus d’informations, consultez [expressions lambda (Guide de programmation C#)](../../csharp/language-reference/operators/lambda-expressions.md) et [expressions lambda (Visual Basic))](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

collection \
Ensemble structuré de données, généralement d'un type uniforme. Pour être compatible avec LINQ, une collection doit implémenter l'interface <xref:System.Collections.IEnumerable> ou l'interface <xref:System.Linq.IQueryable> (ou l'un de leurs équivalents génériques, <xref:System.Collections.Generic.IEnumerator%601> ou <xref:System.Linq.IQueryable%601>).

tuple (types anonymes) \
Concept mathématique, un tuple est une séquence limitée d'objets, chacun d'un type spécifique. Un tuple porte également le nom de liste ordonnée. Les types anonymes sont une implémentation linguistique de ce concept, qui permet à un type de classe non nommé d'être déclaré et à un objet de ce type d'être instancié en même temps.

Pour plus d’informations, consultez [types anonymes (Guide de programmation C#)](../../csharp/programming-guide/classes-and-structs/anonymous-types.md) et [types anonymes (Visual Basic)](../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

inférence de type (typage implicite) \
Capacité d'un compilateur à déterminer le type d'une variable en l'absence d'une déclaration de type explicite.

Pour plus d’informations, consultez [variables locales implicitement typées (Guide de programmation C#)](../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) et [inférence de Type local (Visual Basic)](../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

exécution différée et évaluation différée \
Action de retarder l'évaluation d'une expression jusqu'à ce que sa valeur résolue soit réellement nécessaire. L’exécution différée est prise en charge dans les collections.

Pour plus d’informations sur C#, consultez [Introduction aux requêtes LINQ (c#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md) et [exécution différée et évaluation différée en LINQ to XML (c#)](./deferred-execution-lazy-evaluation.md).

Pour plus d’informations Visual Basic, consultez [opérations de requête de base (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) et [exécution différée et évaluation différée dans LINQ to XML (Visual Basic)](./deferred-execution-lazy-evaluation.md).

Ces fonctionnalités de langage seront utilisées dans les exemples de code tout au long de cette section.

## <a name="see-also"></a>Voir aussi

- [Introduction aux transformations fonctionnelles pures](introduction-pure-functional-transformations.md)
- [Comparaison de la programmation fonctionnelle et de la programmation impérative](functional-vs-imperative-programming.md)
