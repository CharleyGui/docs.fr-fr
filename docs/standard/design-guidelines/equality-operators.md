---
title: Opérateurs d'égalité
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 31a5ce18f4526b5e3b8411365dff812601de87ad
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709437"
---
# <a name="equality-operators"></a>Opérateurs d'égalité
Cette section traite de la surcharge des opérateurs d’égalité et fait référence à `operator==` et `operator!=` en tant qu’opérateurs d’égalité.  
  
 **X DO NOT** un des opérateurs d’égalité et pas dans l’autre surcharge.  
  
 **✓ DO** vous assurer que <xref:System.Object.Equals%2A?displayProperty=nameWithType> et les opérateurs d’égalité ont exactement la même sémantique et des caractéristiques similaires.  
  
 Cela signifie souvent que `Object.Equals` doit être substitué lorsque les opérateurs d’égalité sont surchargés.  
  
 **X AVOID** lever des exceptions à partir des opérateurs d’égalité.  
  
 Par exemple, retourne false si l’un des arguments a la valeur null au lieu de lever `NullReferenceException`.  
  
## <a name="equality-operators-on-value-types"></a>Opérateurs d’égalité sur les types valeur  
 **✓ DO** surcharger les opérateurs d’égalité sur les types valeur, si l’égalité est explicite.  
  
 Dans la plupart des langages de programmation, il n’y a pas d’implémentation par défaut de `operator==` pour les types valeur.  
  
## <a name="equality-operators-on-reference-types"></a>Opérateurs d’égalité sur les types référence  
 **X AVOID** la surcharge des opérateurs d’égalité sur les types référence mutables.  
  
 De nombreux langages ont des opérateurs d’égalité intégrés pour les types référence. Les opérateurs intégrés implémentent généralement l’égalité des références, et de nombreux développeurs sont surpris lorsque le comportement par défaut est remplacé par l’égalité de la valeur.  
  
 Ce problème est atténué pour les types référence immuables, car l’immuabilité rend beaucoup plus difficile la différence entre l’égalité des références et l’égalité des valeurs.  
  
 **X AVOID** surcharge des opérateurs d’égalité sur les types référence si l’implémentation est beaucoup plus lente que celui de l’égalité des références.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Indications relatives à l’utilisation](../../../docs/standard/design-guidelines/usage-guidelines.md)
