---
title: Instructions de conception des membres
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines [.NET Framework], about member design guidelines
- members [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], members
- member design guidelines [.NET Framework]
ms.assetid: 0ce93180-1d7b-4f8c-9306-f828b2d66b8f
ms.openlocfilehash: c323e7edd752a1f003bd3f5d81689aca0eaefd20
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288990"
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
