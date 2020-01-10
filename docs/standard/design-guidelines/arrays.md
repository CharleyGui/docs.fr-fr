---
title: Tableaux
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], arrays
- arrays [.NET Framework], usage guidelines
- empty arrays
ms.assetid: 66a1b3d8-6f3f-4715-b235-e1ff95e32d8e
ms.openlocfilehash: ac4b073d2d3291922498a0e56c7e81f7e7868c65
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709567"
---
# <a name="arrays"></a>Tableaux
**✓ DO** préférez l’utilisation de collections sur des tableaux dans les API publiques. La section [Collections](../../../docs/standard/design-guidelines/guidelines-for-collections.md) fournit des détails sur la manière de choisir entre des collections et des tableaux.  
  
 **X DO NOT** utiliser les champs de tableau en lecture seule. Le champ lui-même est en lecture seule et ne peut pas être modifié, mais les éléments du tableau peuvent être modifiés.  
  
 **✓ CONSIDER** à l’aide de tableaux en escalier à la place de tableaux multidimensionnels.  
  
 Un tableau en escalier est un tableau avec des éléments qui sont également des tableaux. Les tableaux qui composent les éléments peuvent être de différentes tailles, ce qui permet d’obtenir un espace moins gaspillé pour certains jeux de données (par exemple, la matrice éparse) par rapport aux tableaux multidimensionnels. En outre, le CLR optimise les opérations d’index sur les tableaux en escalier, de sorte qu’ils peuvent présenter de meilleures performances d’exécution dans certains scénarios.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Array>
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Indications relatives à l’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)
