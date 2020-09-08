---
title: Applicabilité de la transformation fonctionnelle-LINQ to XML
description: Découvrez quand vous pouvez utiliser des transformations fonctionnelles.
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: cfba2a32887891cd4b735c76e940ff2400e55bef
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553551"
---
# <a name="applicability-of-functional-transformation-linq-to-xml"></a>Applicabilité de la transformation fonctionnelle (LINQ to XML)

Les transformations fonctionnelles pures sont applicables dans un large éventail de situations.

L'approche de transformation fonctionnelle convient tout particulièrement à l'interrogation et à la manipulation de données structurées : elle s'adapte donc parfaitement aux technologies LINQ. Toutefois, les transformations fonctionnelles ont un champ d'application beaucoup plus large que leur utilisation avec LINQ. Tout processus dont l'objectif principal consiste à transformer des données d'une forme vers une autre peut être considéré comme un candidat à la transformation fonctionnelle.

Cette approche est applicable à de nombreux problèmes qui, de premier abord, pourraient sembler ne pas être de bons candidats. Utilisée avec ou séparément de LINQ, la transformation fonctionnelle doit être considérée pour les domaines suivants :

- Documents XML. Les données de forme correcte de tout dialecte XML peuvent être manipulées aisément par le biais de la transformation fonctionnelle. Pour plus d’informations, consultez [transformation fonctionnelle de XML](functional-transformation-xml.md).
- Autres formats de fichiers structurés. Des fichiers Windows.ini aux documents de texte clair, la plupart des fichiers ont une structure qui se prête à l'analyse et à la transformation.
- Protocoles de streaming de données. L'encodage et le décodage de données vers et à partir de protocoles de communication peuvent souvent être représentés par une transformation fonctionnelle simple.
- Données de bases de données relationnelles et orientées objets. Les bases de données relationnelles et orientées objets, comme le code XML, sont des sources de données structurées largement utilisées.
- Solutions mathématiques, statistiques et scientifiques. Ces champs tendent à manipuler de grands ensembles de données afin d'aider l'utilisateur à visualiser, évaluer ou résoudre des problèmes complexes.

Comme décrit dans [Refactoriser dans des fonctions pures](refactor-pure-functions.md), l’utilisation de fonctions pures est un exemple de programmation fonctionnelle. Outre les avantages immédiats des fonctions pures, leur utilisation procure une expérience précieuse pour la résolution des problèmes du point de vue des transformations fonctionnelles. Cette approche peut également avoir un impact majeur sur la conception des programmes et des classes. Cela est particulièrement vrai lorsqu'un problème se prête à une solution de transformation de données, comme indiqué plus haut.

Bien qu’ils n’entrent pas dans le cadre de ce didacticiel, les conceptions qui sont influencées par la perspective de transformation fonctionnelle tendent à être centrées sur les processus plus que sur les objets en tant qu’acteurs, et la solution résultante tend à être implémentée comme une série de transformations à grande échelle, plutôt que des modifications d’état d’objet individuelles.

 Là encore, souvenez-vous que C# et Visual Basic prennent en charge les approches impératives et fonctionnelles ; la meilleure conception pour votre application peut donc incorporer des éléments de ces deux approches.

## <a name="see-also"></a>Voir aussi

- [Présentation des transformations fonctionnelles pures](introduction-pure-functional-transformations.md)
- [Transformation fonctionnelle de XML](functional-transformation-xml.md)
- [Refactoriser dans des fonctions pures](refactor-pure-functions.md)
