---
title: Applicabilité des transformations fonctionnelles (C#)
desciption: Learn about functional transformation. See how this approach to LINQ and other processes where the focus is on transforming data from one form to another.
ms.date: 07/20/2015
ms.assetid: c78107bd-b006-4574-a3d4-bbf808388ff3
ms.openlocfilehash: b507e0ad5c09478c3427f87d32a21d8facf1b7a0
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105571"
---
# <a name="applicability-of-functional-transformation-c"></a>Applicabilité des transformations fonctionnelles (C#)
Les transformations fonctionnelles pures sont applicables dans un large éventail de situations.  
  
 L'approche de transformation fonctionnelle convient tout particulièrement à l'interrogation et à la manipulation de données structurées : elle s'adapte donc parfaitement aux technologies LINQ. Toutefois, les transformations fonctionnelles ont un champ d'application beaucoup plus large que leur utilisation avec LINQ. Tout processus dont l'objectif principal consiste à transformer des données d'une forme vers une autre peut être considéré comme un candidat à la transformation fonctionnelle.  
  
 Cette approche est applicable à de nombreux problèmes qui, de premier abord, pourraient sembler ne pas être de bons candidats. Utilisée avec ou séparément de LINQ, la transformation fonctionnelle doit être considérée pour les domaines suivants :  
  
- Documents XML. Les données de forme correcte de tout dialecte XML peuvent être manipulées aisément par le biais de la transformation fonctionnelle. Pour plus d’informations, consultez [Transformation fonctionnelle de données XML (C#)](./functional-transformation-of-xml.md).  
  
- Autres formats de fichiers structurés. Des fichiers Windows.ini aux documents de texte clair, la plupart des fichiers ont une structure qui se prête à l'analyse et à la transformation.  
  
- Protocoles de streaming de données. L'encodage et le décodage de données vers et à partir de protocoles de communication peuvent souvent être représentés par une transformation fonctionnelle simple.  
  
- Données de bases de données relationnelles et orientées objets. Les bases de données relationnelles et orientées objets, comme le code XML, sont des sources de données structurées largement utilisées.  
  
- Solutions mathématiques, statistiques et scientifiques. Ces champs tendent à manipuler de grands ensembles de données afin d'aider l'utilisateur à visualiser, évaluer ou résoudre des problèmes complexes.  
  
 Comme décrit dans [Refactorisation dans des fonctions pures (C#)](./refactoring-into-pure-functions.md), l’utilisation de fonctions pures est un exemple de programmation fonctionnelle. Outre les avantages immédiats des fonctions pures, leur utilisation procure une expérience précieuse pour la résolution des problèmes du point de vue des transformations fonctionnelles. Cette approche peut également avoir un impact majeur sur la conception des programmes et des classes. Cela est particulièrement vrai lorsqu'un problème se prête à une solution de transformation de données, comme indiqué plus haut.  
  
 Bien qu'elles dépassent la portée de ce didacticiel, les conceptions qui sont influencées par la perspective des transformations fonctionnelles tendent à être axées sur les processus plutôt que sur les objets en tant qu'acteurs, et la solution résultante tend à être implémentée en tant que séries de transformations à grande échelle plutôt que comme modifications d'état d'objet individuelles.  
  
 Là encore, souvenez-vous que C# prend en charge les approches impératives et fonctionnelles. La meilleure conception pour votre application peut donc incorporer des éléments de ces deux approches.  
  
## <a name="see-also"></a>Voir aussi

- [Introduction aux transformations fonctionnelles pures (C#)](./introduction-to-pure-functional-transformations.md)
- [Transformation fonctionnelle de données XML (C#)](./functional-transformation-of-xml.md)
- [Refactorisation dans des fonctions pures (C#)](./refactoring-into-pure-functions.md)
