---
title: Conception de champs
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- fields, design guidelines
- read-only fields
- member design guidelines, fields
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
ms.openlocfilehash: d39c9b95d759902d6d523b028f3db8b8da954336
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709346"
---
# <a name="field-design"></a>Conception de champs
Le principe de l’encapsulation est l’une des notions les plus importantes en matière de conception orientée objet. Ce principe stipule que les données stockées dans un objet ne doivent être accessibles qu’à cet objet.  
  
 Une méthode utile pour interpréter le principe consiste à indiquer qu’un type doit être conçu de manière à ce que les modifications apportées aux champs de ce type (modification de nom ou de type) puissent être effectuées sans interrompre le code autre que pour les membres du type. Cette interprétation implique immédiatement que tous les champs doivent être privés.  
  
 Nous excluons les champs constants et statiques en lecture seule de cette restriction stricte, car ces champs, presque par définition, ne sont jamais requis pour la modification.  
  
 **X DO NOT** contiennent des champs d’instance qui sont publics ou protégés.  
  
 Vous devez fournir des propriétés pour accéder aux champs au lieu de les rendre publics ou protégés.  
  
 **✓ DO** utiliser les champs constants pour les constantes qui ne changent pas.  
  
 Le compilateur grave les valeurs des champs const directement dans le code appelant. Par conséquent, les valeurs const ne peuvent jamais être modifiées sans risque d’interruption de la compatibilité.  
  
 **✓ DO** utiliser statique public `readonly` champs pour les instances d’objet prédéfinies.  
  
 S’il existe des instances prédéfinies du type, déclarez-les en tant que champs statiques publics en lecture seule du type lui-même.  
  
 **X DO NOT** affecter des instances de types mutables à `readonly` champs.  
  
 Un type mutable est un type dont les instances peuvent être modifiées une fois qu’elles ont été instanciées. Par exemple, les tableaux, la plupart des collections et des flux sont des types mutables, mais <xref:System.Int32?displayProperty=nameWithType>, <xref:System.Uri?displayProperty=nameWithType>et <xref:System.String?displayProperty=nameWithType> sont tous immuables. Le modificateur en lecture seule sur un champ de type référence empêche le remplacement de l’instance stockée dans le champ, mais n’empêche pas la modification des données d’instance du champ en appelant des membres qui modifient l’instance.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Instructions de conception des membres](../../../docs/standard/design-guidelines/member.md)
- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
