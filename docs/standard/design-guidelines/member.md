---
title: Instructions de conception des membres
description: Découvrez les instructions de conception des membres dans .NET. Les membres incluent des méthodes, des propriétés, des événements, des constructeurs et des champs.
ms.date: 10/22/2008
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: 5070f45beccd89d6f051f1b1d8345390e915d471
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706591"
---
# <a name="member-design-guidelines"></a>Instructions de conception des membres

Les méthodes, propriétés, événements, constructeurs et champs sont collectivement appelés membres. Les membres sont finalement les moyens par lesquels les fonctionnalités de l’infrastructure sont exposées aux utilisateurs finaux d’une infrastructure.  
  
 Les membres peuvent être virtuels ou non virtuels, concrets ou abstraits, statiques ou d’instance et peuvent avoir plusieurs étendues d’accessibilité différentes. Toute cette variété offre une expressivité incroyable, mais dans le même temps, vous devez faire attention à la partie du concepteur de Framework.  
  
 Ce chapitre propose des instructions de base qui doivent être suivies lors de la conception de membres de n’importe quel type.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Surcharge de membre](member-overloading.md)  
 [Conception des propriétés](property.md)  
 [Conception de constructeur](constructor.md)  
 [Conception des événements](event.md)  
 [Conception de champs](field.md)  
 [Méthodes d’extension](extension-methods.md)  
 [Surcharges d’opérateur](operator-overloads.md)  
 [Conception de paramètres](parameter-design.md)  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Directives de conception d’infrastructure](index.md)
