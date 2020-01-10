---
title: Levée d'exceptions
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 7d1b63e5fde57cbe37a1250d16b6bf74a2d5dc8e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709398"
---
# <a name="exception-throwing"></a>Levée d'exceptions
Les instructions de levée des exceptions décrites dans cette section nécessitent une bonne définition de la signification de l’échec de l’exécution. L’échec de l’exécution se produit chaque fois qu’un membre ne peut pas faire ce qu’il a prévu (ce que signifie le nom du membre). Par exemple, si la méthode `OpenFile` ne peut pas retourner un descripteur de fichier ouvert à l’appelant, elle est considérée comme un échec d’exécution.  
  
 La plupart des développeurs se familiarisent avec l’utilisation d’exceptions pour les erreurs d’utilisation telles que la division par zéro ou les références null. Dans le Framework, les exceptions sont utilisées pour toutes les conditions d’erreur, y compris les erreurs d’exécution.  
  
 **X DO NOT** codes d’erreur.  
  
 Les exceptions sont le principal moyen de signaler les erreurs dans les infrastructures.  
  
 **✓ DO** signale les échecs de l’exécution en levant des exceptions.  
  
 **✓ CONSIDER** mettre fin au processus en appelant `System.Environment.FailFast` (fonctionnalité de .NET Framework 2.0) au lieu de lever une exception si votre code rencontre une situation où il est risqué pour obtenir de l’exécution.  
  
 **X DO NOT** utiliser des exceptions pour le flux normal de contrôle, si possible.  
  
 À l’exception des défaillances système et des opérations avec des conditions de concurrence potentielles, les concepteurs d’infrastructure doivent concevoir des API pour que les utilisateurs puissent écrire du code qui ne lève pas d’exceptions. Par exemple, vous pouvez fournir un moyen de vérifier les conditions préalables avant d’appeler un membre afin que les utilisateurs puissent écrire du code qui ne lève pas d’exceptions.  
  
 Le membre utilisé pour vérifier les conditions préalables d’un autre membre est souvent appelé testeur, et le membre qui effectue réellement le travail est appelé Doer.  
  
 Dans certains cas, le modèle testeur-Doer peut avoir une surcharge de performance inacceptable. Dans ce cas, le modèle « try-parse » doit être pris en compte (pour plus d’informations, consultez [exceptions et performances](../../../docs/standard/design-guidelines/exceptions-and-performance.md) ).  
  
 **✓ CONSIDER** l’impact sur les performances de lever des exceptions. Les taux de rejet supérieurs à 100 par seconde sont susceptibles d’avoir un impact notable sur les performances de la plupart des applications.  
  
 **✓ DO** document toutes les exceptions levées par les membres pouvant être appelés publiquement en raison d’une violation du membre de contrat (au lieu d’une défaillance du système) et les traitent en tant que partie de votre contrat.  
  
 Les exceptions qui font partie du contrat ne doivent pas passer d’une version à l’autre (par exemple, le type d’exception ne doit pas changer et les nouvelles exceptions ne doivent pas être ajoutées).  
  
 **X DO NOT** ont des membres publics qui peuvent lever ou non basées sur une option.  
  
 **X DO NOT** des membres publics de retournent des exceptions comme valeur de retour ou un `out` paramètre.  
  
 Le retour d’exceptions à partir d’API publiques au lieu de les lever est à l’encontre de nombreux avantages du rapport d’erreurs basé sur les exceptions.  
  
 **✓ CONSIDER** à l’aide des méthodes de générateur d’exceptions.  
  
 Il est courant de lever la même exception à partir de différents emplacements. Pour éviter l’augmentation du code, utilisez des méthodes d’assistance qui créent des exceptions et initialisent leurs propriétés.  
  
 En outre, les membres qui lèvent des exceptions ne sont pas Inline. Le déplacement de l’instruction throw dans le générateur peut permettre au membre d’être Inline.  
  
 **X DO NOT** lever des exceptions à partir de blocs de filtre d’exception.  
  
 Lorsqu’un filtre d’exception lève une exception, l’exception est interceptée par le CLR et le filtre retourne la valeur false. Ce comportement ne peut pas être distingué du filtre en cours d’exécution et retourne explicitement false et est donc très difficile à déboguer.  
  
 **X AVOID** lever explicitement des exceptions à partir de blocs finally. Les exceptions levées implicitement qui résultent de l’appel de méthodes qui lèvent sont acceptables.  
  
 *Parties © 2005, 2009 Microsoft Corporation. Tous droits réservés.*  
  
 *Réimprimé avec l’autorisation de Pearson Education, Inc. et extrait de [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) par Krzysztof Cwalina et Brad Abrams, publié le 22 octobre 2008 par Addison-Wesley Professional dans le cadre de la série sur le développement Microsoft Windows.*  
  
## <a name="see-also"></a>Voir aussi

- [Règles de conception de .NET Framework](../../../docs/standard/design-guidelines/index.md)
- [Instructions de conception pour les exceptions](../../../docs/standard/design-guidelines/exceptions.md)
