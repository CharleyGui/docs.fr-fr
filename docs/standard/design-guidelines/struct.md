---
title: Conception de structures
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
author: KrzysztofCwalina
ms.openlocfilehash: e787c5b34848a561b43c3457341673f11cc2bd00
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775547"
---
# <a name="struct-design"></a>Conception de structures
Le type de valeur à usage général est souvent appelé un struct, son mot-clé c#. Cette section fournit des instructions pour la conception de la structure générale.  
  
 **X ne sont pas** fournir un constructeur sans paramètre pour un struct.  
  
 Suivant cette recommandation permet de tableaux de structs peuvent être créés sans avoir à exécuter le constructeur sur chaque élément du tableau. Notez que C# n’autorise pas les structs peuvent avoir des constructeurs sans paramètre.  
  
 **X DO NOT** définissent les types de valeur mutable.  
  
 Types de valeur mutable ont plusieurs problèmes. Par exemple, lorsqu’un accesseur Get de propriété retourne un type valeur, l’appelant reçoit une copie. Étant donné que la copie est créée implicitement, les développeurs connaissez peut-être pas qu’ils sont de mutation la copie et non la valeur d’origine. En outre, certains langages (langages dynamiques, en particulier) ont des problèmes à l’aide de types valeur mutable, car même les variables locales, lorsqu’il est déréférencé, provoquer une copie qu’il veut.  
  
 **✓ DO** s’assurer qu’un état où toutes les données de l’instance est défini sur zéro, false ou null (le cas échéant) est valide.  
  
 Cela empêche la création accidentelle d’instances non valides lors de la création d’un tableau des structs.  
  
 **✓ DO** implémenter <xref:System.IEquatable%601> sur les types valeur.  
  
 Le <xref:System.Object.Equals%2A?displayProperty=nameWithType> (méthode) sur les types valeur entraîne la conversion boxing et son implémentation par défaut n’est pas très efficace, car il utilise la réflexion. <xref:System.IEquatable%601.Equals%2A> peut avoir de meilleures performances et peut être implémentée afin qu’elle n’entraîne pas de boxing.  
  
 **X DO NOT** prolonger explicitement <xref:System.ValueType>. En fait, la plupart des langages éviter ce problème.  
  
 En général, les structs peuvent être très utiles mais ne doit être utilisées que pour les valeurs de petite, unique et immuables qui ne seront pas boxed fréquemment.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson éducation, Inc. à partir de [instructions de conception Framework : Conventions, les idiomes et les modèles pour les bibliothèques .NET réutilisable, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série de développement de Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Instructions pour la conception des types](../../../docs/standard/design-guidelines/type.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Choix entre classe et structure](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
