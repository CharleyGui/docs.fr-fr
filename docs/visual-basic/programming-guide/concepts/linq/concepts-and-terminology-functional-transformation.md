---
title: Concepts et terminologie (transformation fonctionnelle)
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: 4a63630d431a0972fb1a61981306a41e6f4926e3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410862"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Concepts et terminologie (transformation fonctionnelle) (Visual Basic)
Cette rubrique présente les concepts et la terminologie des transformations fonctionnelles pures. L'approche de transformation fonctionnelle pour la transformation des données génère du code qui est souvent plus rapide à programmer, plus expressif et plus facile à déboguer et à maintenir que le code de programmation impératif plus traditionnel.

Notez que les rubriques de cette section n'ont pas pour but d'expliquer en détail la programmation fonctionnelle. Au lieu de cela, elles identifient certaines des capacités de programmation fonctionnelle qui facilitent la transformation de code XML d'une forme en une autre.

## <a name="what-is-pure-functional-transformation"></a>Qu'est-ce que la transformation fonctionnelle pure ?

Dans la *transformation fonctionnelle pure*, un ensemble de fonctions, appelées *fonctions pures*, indiquent comment transformer un ensemble de données structurées de leur forme d’origine en une autre forme. Le terme "pur" indique que les fonctions sont *composables*, ce qui nécessite qu’elles aient les caractéristiques suivantes :

- *Être autonomes*, de manière à pouvoir être librement ordonnées et réorganisées sans enchevêtrement ni interdépendance avec le reste du programme. Les transformations pures n'ont aucune connaissance de leur environnement et aucun effet sur lui. Autrement dit, les fonctions utilisées dans la transformation n’ont pas d’*effets secondaires*.

- *Être sans état*, de sorte que l’exécution de la même fonction ou du même ensemble spécifique de fonctions sur la même entrée générera toujours le même résultat. Les transformations pures n'ont pas de mémoire de leur utilisation antérieure.

> [!IMPORTANT]
> Dans le reste de ce didacticiel, le terme « fonction pure » est utilisé dans un sens général pour indiquer une approche de programmation, et non une fonctionnalité de langage spécifique.
>
> Notez que les fonctions pures doivent être implémentées en tant que fonctions dans Visual Basic.
>
> En outre, il convient de ne pas confondre les fonctions pures avec les méthodes virtuelles pures en C++. Ces dernières indiquent que la classe conteneur est abstraite et qu'aucun corps de méthode n'est fourni.

### <a name="functional-programming"></a>Programmation fonctionnelle

La *programmation fonctionnelle* est une approche de programmation prenant directement en charge la transformation fonctionnelle pure.

Historiquement, les langages de programmation fonctionnelle à usage général, tels que ML, Scheme, Haskell et F#, ont toujours essentiellement intéressé la communauté liée au monde de l’enseignement et de la recherche. Bien qu’il ait toujours été possible d’écrire des transformations fonctionnelles pures dans Visual Basic, la difficulté de cette opération n’a pas rendu une option intéressante pour la plupart des programmeurs. Toutefois, avec les versions ultérieures de Visual Basic, de nouvelles constructions de langage telles que les expressions lambda et l’inférence de type rendent la programmation fonctionnelle beaucoup plus simple et plus productive.

Pour plus d’informations sur la programmation fonctionnelle, consultez [programmation fonctionnelle et programmation impérative (Visual Basic)](functional-programming-vs-imperative-programming.md).

#### <a name="domain-specific-fp-languages"></a>Langages de programmation fonctionnelle spécifiques aux domaines

Bien que les langages de programmation fonctionnelle généraux n'aient pas été adoptés à grande échelle, les langages de programmation fonctionnelle spécifiques aux domaines ont eu un meilleur succès. Par exemple, les feuilles de style en cascade (CSS, Cascading Style Sheets) sont utilisées pour déterminer l’apparence et la convivialité de nombreuses pages web et les feuilles de style XSLT (Extensible Stylesheet Language Transformations) sont utilisées de manière intensive dans la manipulation de données XML. Pour plus d’informations sur XSLT, consultez [Transformations XSLT](../../../../standard/data/xml/xslt-transformations.md).

## <a name="terminology"></a>Terminologie

Le tableau suivant définit certains termes liés aux transformations fonctionnelles.

fonction d’ordre supérieur (première classe) \
Fonction qui peut être traitée en tant qu'objet de programmation. Par exemple, une fonction d'ordre supérieur peut être passée à ou retournée à partir d'autres fonctions. Dans Visual Basic, les délégués et les expressions lambda sont des fonctionnalités de langage qui prennent en charge des fonctions d’ordre supérieur. Pour écrire une fonction d’ordre supérieur, vous déclarez un ou plusieurs arguments pour prendre des délégués et vous utilisez souvent des expressions lambda lorsque vous appelez votre fonction. Une grande partie des opérateurs de requête standard sont des fonctions d'ordre supérieur.

Pour plus d’informations, consultez [vue d’ensemble des opérateurs de requête standard (Visual Basic)](standard-query-operators-overview.md).

expression lambda \
Pour l'essentiel, il s'agit d'une fonction anonyme inline qui peut être utilisée partout où un type délégué est attendu. Cette définition des expressions lambda est simplifiée, mais elle convient pour les besoins de ce didacticiel.

Pour plus d’informations, consultez [Expressions lambda](../../language-features/procedures/lambda-expressions.md).

collection \
Ensemble structuré de données, généralement d'un type uniforme. Pour être compatible avec LINQ, une collection doit implémenter l'interface <xref:System.Collections.IEnumerable> ou l'interface <xref:System.Linq.IQueryable> (ou l'un de leurs équivalents génériques, <xref:System.Collections.Generic.IEnumerator%601> ou <xref:System.Linq.IQueryable%601>).

tuple (types anonymes) \
Concept mathématique, un tuple est une séquence limitée d'objets, chacun d'un type spécifique. Un tuple porte également le nom de liste ordonnée. Les types anonymes sont une implémentation linguistique de ce concept, qui permet à un type de classe non nommé d'être déclaré et à un objet de ce type d'être instancié en même temps.

Pour plus d’informations, consultez [types anonymes](../../language-features/objects-and-classes/anonymous-types.md).

inférence de type (typage implicite) \
Capacité d'un compilateur à déterminer le type d'une variable en l'absence d'une déclaration de type explicite.

Pour plus d’informations, consultez [inférence de type local](../../language-features/variables/local-type-inference.md).

exécution différée et évaluation différée \
Action de retarder l'évaluation d'une expression jusqu'à ce que sa valeur résolue soit réellement nécessaire. L’exécution différée est prise en charge dans les collections.

Pour plus d’informations, consultez [opérations de requête de base (Visual Basic)](basic-query-operations.md) et [exécution différée et évaluation différée dans LINQ to XML (Visual Basic)](deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Ces fonctionnalités de langage seront utilisées dans les exemples de code tout au long de cette section.

## <a name="see-also"></a>Voir aussi

- [Présentation des transformations fonctionnelles pures (Visual Basic)](introduction-to-pure-functional-transformations.md)
- [Programmation fonctionnelle et programmation impérative (Visual Basic)](functional-programming-vs-imperative-programming.md)
